# Claude Code：代理记忆前置元数据

子代理的持久记忆 — 使代理能够跨会话学习、记忆和积累知识。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 概述

在 **Claude Code v2.1.33**（2026 年 2 月）中引入，`memory` 前置元数据字段为每个子代理提供其自己的基于 Markdown 的持久知识存储。在此之前，每次代理调用都从头开始。

```yaml
---
name: code-reviewer
description: 审查代码的质量和最佳实践
tools: Read, Write, Edit, Bash
model: sonnet
memory: user
---

你是一个代码审查者。在审查代码时，用你发现的模式、约定和重复出现的问题更新你的代理记忆。
```

---

## 记忆范围

| 范围 | 存储位置 | 版本控制 | 共享 | 最适合 |
|-------|-----------------|-------------------|--------|----------|
| `user` | `~/.claude/agent-memory/<agent-name>/` | 否 | 否 | 跨项目知识（推荐默认） |
| `project` | `.claude/agent-memory/<agent-name>/` | 是 | 是 | 项目特定知识，团队应共享 |
| `local` | `.claude/agent-memory-local/<agent-name>/` | 否（git 忽略） | 否 | 项目特定知识，但属个人性质 |

这些范围镜像设置层次结构（`~/.claude/settings.json` → `.claude/settings.json` → `.claude/settings.local.json`）。

---

## 工作原理

1. **启动时**：`MEMORY.md` 的前 200 行被注入到代理的系统提示中
2. **工具访问**：`Read`、`Write`、`Edit` 自动启用，以便代理管理其记忆
3. **执行期间**：代理自由地读/写其记忆目录
4. **整理**：如果 `MEMORY.md` 超过 200 行，代理将详细信息移动到主题特定文件中

```
~/.claude/agent-memory/code-reviewer/     # user 范围示例
├── MEMORY.md                              # 主文件（加载前 200 行）
├── react-patterns.md                      # 主题特定文件
└── security-checklist.md                  # 主题特定文件
```

---

## 代理记忆与其他记忆系统

| 系统 | 谁写入 | 谁读取 | 范围 |
|--------|-----------|-----------|-------|
| **CLAUDE.md** | 你（手动） | 主 Claude + 所有代理 | 项目 |
| **自动记忆** | 主 Claude（自动） | 仅主 Claude | 每项目每用户 |
| **`/memory` 命令** | 你（通过编辑器） | 仅主 Claude | 每项目每用户 |
| **代理记忆** | 代理自身 | 仅该特定代理 | 可配置（user/project/local） |

这些系统是**互补的** — 代理同时读取 CLAUDE.md（项目上下文）和它自己的记忆（代理特定知识）。

---

## 实际示例

```yaml
---
name: api-developer
description: 按照团队约定实现 API 端点
tools: Read, Write, Edit, Bash
model: sonnet
memory: project
skills:
  - api-conventions
  - error-handling-patterns
---

实现 API 端点。遵循预加载技能中的约定。
在工作中，将架构决策和模式保存到你的记忆中。
```

这结合了**技能**（启动时的静态知识）和**记忆**（随时间积累的动态知识）。

---

## 提示

- **提示记忆使用** — 包含显式指令：*"在开始之前，回顾你的记忆。完成后，用你学到的东西更新你的记忆。"*
- **调用代理时请求检查记忆**：*"审查此 PR，并检查你的记忆中是否有你之前见过的模式。"*
- **选择正确的范围** — `user` 用于跨项目，`project` 用于团队共享，`local` 用于个人

---

## 来源

- [创建自定义子代理 — Claude Code 文档](https://code.claude.com/docs/en/sub-agents)
- [管理 Claude 的记忆 — Claude Code 文档](https://code.claude.com/docs/en/memory)
- [Claude Code v2.1.33 发布说明](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
