# 代理 vs 命令 vs 技能 — 何时使用什么

Claude Code 三种扩展机制的比较：子代理、命令和技能。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

![显示 time-skill、time-command 和 time-agent 的斜杠菜单](assets/agent-command-skill-1.jpg)

---

## 概览

| | 代理 | 命令 | 技能 |
|---|---|---|---|
| **位置** | `.claude/agents/<name>.md` | `.claude/commands/<name>.md` | `.claude/skills/<name>/SKILL.md` |
| **上下文** | 独立的子代理进程 | 内联（主对话） | 内联（主对话） |
| **用户可调用** | 无 `/` 菜单 — 由 Claude 调用或通过 Agent 工具调用 | 是 — `/command-name` | 是 — `/skill-name`（除非 `user-invocable: false`） |
| **Claude 自动调用** | 是 — 通过 `description` 字段 | 否 | 是 — 通过 `description` 字段（除非 `disable-model-invocation: true`） |
| **接受参数** | 通过 `prompt` 参数 | `$ARGUMENTS`, `$0`, `$1` | `$ARGUMENTS`, `$0`, `$1` |
| **动态上下文注入** | 否 | 是 — `` !`command` `` | 是 — `` !`command` `` |
| **自有上下文窗口** | 是 — 隔离 | 否 — 共享主窗口 | 否 — 共享主窗口（除非 `context: fork`） |
| **模型覆盖** | `model:` 前置元数据 | `model:` 前置元数据 | `model:` 前置元数据 |
| **工具限制** | `tools:` / `disallowedTools:` | `allowed-tools:` | `allowed-tools:` |
| **钩子** | `hooks:` 前置元数据 | — | `hooks:` 前置元数据 |
| **记忆** | `memory:` 前置元数据（user/project/local） | — | — |
| **可预加载技能** | 是 — `skills:` 前置元数据 | — | — |
| **MCP 服务器** | `mcpServers:` 前置元数据 | — | — |

---

## 何时使用每种机制

### 使用代理当：

- 任务是**自主且多步骤的** — 代理需要探索、决策和行动，无需持续指导
- 你需要**上下文隔离** — 工作不应污染主对话窗口
- 代理需要跨会话的**持久记忆**（例如，学习模式的代码审查者）
- 你希望通过技能**预加载领域知识**而不使主上下文臃肿
- 任务受益于**后台运行**或**git worktree**中运行
- 你需要**工具限制**或**不同的权限模式**（例如，`acceptEdits`，`plan`）

**示例**：`weather-agent` — 使用其预加载的 `weather-fetcher` 技能自主获取天气数据，在受限工具的独立上下文中运行。

### 使用命令当：

- 你需要一个**用户启动的入口点** — 用户显式触发的工作流
- 工作流涉及**编排**其他代理或技能
- 你希望**保持上下文精简** — 命令内容在用户触发之前不会注入到会话上下文中

**示例**：`weather-orchestrator` — 用户触发它，它询问 C/F 偏好，调用代理，然后调用 SVG 技能。

### 使用技能当：

- 你希望 **Claude 基于用户意图自动调用** — 技能描述被注入到会话上下文中用于语义匹配
- 任务是一个**可重用的过程**，可以从多个地方调用（命令、代理或 Claude 自身）
- 你需要**代理预加载** — 在启动时将领域知识注入到特定代理中

**示例**：`weather-svg-creator` — 当用户要求天气卡片时，Claude 自动调用它；也可从命令中调用。

---

## 命令 → 代理 → 技能架构

此仓库展示了一个分层编排模式：

```
用户触发 /command
    ↓
命令编排工作流
    ↓
命令调用代理（独立上下文，自主）
    ↓
代理使用预加载的技能（领域知识）
    ↓
命令调用技能（内联，用于输出生成）
```

**具体示例** — 天气系统：

```
/weather-orchestrator（命令 — 入口点，询问 C/F）
    ↓
weather-agent（代理 — 自主获取温度）
    ├── weather-fetcher（代理技能 — 预加载的 API 指令）
    ↓
weather-svg-creator（技能 — 内联创建 SVG）
```

---

## 前置元数据比较

### 代理前置元数据

```yaml
---
name: my-agent
description: 在以下情况下主动使用此代理...
tools: Read, Write, Edit, Bash
model: sonnet
maxTurns: 10
permissionMode: acceptEdits
memory: user
skills:
  - my-skill
---
```

### 命令前置元数据

```yaml
---
description: 做一些有用的事情
argument-hint: [issue-number]
allowed-tools: Read, Edit, Bash(gh *)
model: sonnet
---
```

### 技能前置元数据

```yaml
---
name: my-skill
description: 当用户要求...时执行操作
argument-hint: [file-path]
disable-model-invocation: false
user-invocable: true
allowed-tools: Read, Grep, Glob
model: sonnet
context: fork
agent: general-purpose
---
```

---

## 关键区别

### 自动调用

| 机制 | Claude 可以自动调用吗？ | 如何阻止 |
|-----------|------------------------|----------------|
| 代理 | 是 — 通过 `description`（使用"主动"来鼓励） | 移除或弱化描述 |
| 命令 | 否 — 始终由用户通过 `/` 启动 | 不适用 |
| 技能 | 是 — 通过 `description` | 设置 `disable-model-invocation: true` |

### 在 `/` 菜单中的可见性

| 机制 | 出现在 `/` 菜单中吗？ | 如何隐藏 |
|-----------|---------------------|-------------|
| 代理 | 否 | 不适用 |
| 命令 | 是 — 始终 | 无法隐藏 |
| 技能 | 是 — 默认 | 设置 `user-invocable: false` |

### 上下文隔离

| 机制 | 在自有上下文中运行吗？ | 如何配置 |
|-----------|---------------------|-----------------|
| 代理 | 始终 | 内置行为 |
| 命令 | 从不 | 不适用 |
| 技能 | 可选 | 设置 `context: fork` |

---

## 实际示例："当前时间是多少？"

此仓库为同一任务定义了所有三种机制 — 显示 PKT 的当前时间。以下是当用户在**不显式调用任何 `/` 命令**的情况下输入 **"当前时间是多少？"** 时发生的情况：

| 机制 | 会触发吗？ | 原因 |
|-----------|--------------|---------------|
| `time-command` | 否 | 命令**从不自动调用**。用户需要显式输入 `/time-command` 才能运行。命令没有自动发现路径 — 它们严格由用户启动。 |
| `time-agent` | **是**（可能） | 代理的 `description` 说*"使用此代理显示巴基斯坦标准时间的当前时间"*。Claude 将此与用户意图匹配，并可能通过 Agent 工具生成它。然而，代理在**单独的上下文窗口**中运行，使它们对这个简单任务来说比必要的更重。 |
| `time-skill` | **是**（最可能） | 技能的 `description` 说*"显示巴基斯坦标准时间 (PKT, UTC+5) 的当前时间。当用户询问当前时间、巴基斯坦时间或 PKT 时使用。"* Claude 匹配此描述并通过 Skill 工具调用它。由于它在**内联**运行，没有上下文开销，它是最高效的匹配。 |

### 解析顺序

当多个机制匹配同一意图时，Claude 首选满足请求的**最轻量级选项**：

```
1. 技能（内联，无上下文开销）     ← 首选
2. 代理（独立上下文，自主）        ← 如果技能不可用或任务复杂时使用
3. 命令（从不 — 需要显式 /）       ← 仅当用户输入 /time-command
```

### 如果技能上设置了 `disable-model-invocation: true` 会怎样？

那么 Claude **不能**自动调用技能。代理成为唯一可自动调用的选项，因此 Claude 会改为生成 `time-agent` — 代价是为一个一行 bash 命令使用单独的上下文窗口。

### 如果技能和代理都禁用了自动调用会怎样？

那么**没有东西会自动触发**。Claude 会退回到自己的通用知识，可能直接运行 `TZ='Asia/Karachi' date` — 不涉及任何扩展机制。用户需要显式输入 `/time-command` 或 `/time-skill` 来使用其中之一。

![当用户询问"当前时间是多少？"时，Claude 自动调用 time-skill](assets/agent-command-skill-2.png)

---

## 来源

- [Claude Code 技能 — 文档](https://code.claude.com/docs/en/skills)
- [Claude Code 子代理 — 文档](https://code.claude.com/docs/en/sub-agents)
- [Claude Code 斜杠命令 — 文档](https://code.claude.com/docs/en/slash-commands)
- [技能最佳实践](../best-practice/claude-skills.md)
- [命令最佳实践](../best-practice/claude-commands.md)
- [子代理最佳实践](../best-practice/claude-subagents.md)
