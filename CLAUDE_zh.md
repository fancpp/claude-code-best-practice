# CLAUDE.md

本文档为在此仓库中使用 Claude Code (claude.ai/code) 工作时提供指导。

## 仓库概述

这是一个 Claude Code 配置的最佳实践仓库，展示技能、子代理、钩子和命令的模式。它作为参考实现而非应用代码库。

## 关键组件

### 天气系统（示例工作流）

通过 **命令 → 代理 → 技能** 架构演示两种不同的技能模式：
- `/weather-orchestrator` 命令（`.claude/commands/weather-orchestrator.md`）：入口点 — 询问用户 C/F，调用代理，然后调用 SVG 技能
- `weather-agent` 代理（`.claude/agents/weather-agent.md`）：使用预加载的 `weather-fetcher` 技能获取温度（代理技能模式）
- `weather-fetcher` 技能（`.claude/skills/weather-fetcher/SKILL.md`）：预加载到代理中 — 从 Open-Meteo 获取温度的指令
- `weather-svg-creator` 技能（`.claude/skills/weather-svg-creator/SKILL.md`）：技能 — 创建 SVG 天气卡片，写入 `orchestration-workflow/weather.svg` 和 `orchestration-workflow/output.md`

两种技能模式：代理技能（通过 `skills:` 字段预加载）vs 技能（通过 `Skill` 工具调用）。完整的流程图示见 `orchestration-workflow/orchestration-workflow.md`。

### 技能定义结构

`.claude/skills/<name>/SKILL.md` 中的技能使用 YAML frontmatter：
- `name`: 显示名称和 `/slash-command`（默认为目录名）
- `description`: 何时调用（建议用于自动发现）
- `argument-hint`: 自动补全提示（例如 `[issue-number]`）
- `disable-model-invocation`: 设置为 `true` 以防止自动调用
- `user-invocable`: 设置为 `false` 以从 `/` 菜单隐藏（仅作背景知识）
- `allowed-tools`: 技能激活时无需权限提示即可使用的工具
- `model`: 技能激活时要使用的模型
- `context`: 设置为 `fork` 以在隔离的子代理上下文中运行
- `agent`: `context: fork` 的子代理类型（默认：`general-purpose`）
- `hooks`: 限定于此技能的生命周期钩子

### 演示系统

参见 `.claude/rules/presentation.md` — 演示工作根据具体演示委托给 `presentation-vibe-coding`（用于 `presentation/vibe-coding-to-agentic-engineering/`）或 `presentation-claude-gemini`（用于 `presentation/2026-04-25-gdg-kolachi-cli-claude-code-gemini/`）。

### 钩子系统

`.claude/hooks/` 中的跨平台声音通知系统：
- `scripts/hooks.py`: Claude Code 钩子事件的主处理程序
- `config/hooks-config.json`: 共享团队配置
- `config/hooks-config.local.json`: 个人覆盖（git 忽略）
- `sounds/`: 按钩子事件组织的音频文件（通过 ElevenLabs TTS 生成）

`.claude/settings.json` 中配置的钩子事件：PreToolUse, PostToolUse, UserPromptSubmit, Notification, Stop, SubagentStart, SubagentStop, PreCompact, SessionStart, SessionEnd, Setup, PermissionRequest, TeammateIdle, TaskCompleted, ConfigChange。

特殊处理：git 提交触发 `pretooluse-git-committing` 声音。

## 关键模式

### 子代理编排

子代理**不能**通过 bash 命令调用其他子代理。使用 Agent 工具（在 v2.1.63 中从 Task 重命名；`Task(...)` 仍可作为别名）：
```
Agent(subagent_type="agent-name", description="...", prompt="...", model="haiku")
```

在子代理定义中明确说明工具使用。避免使用可能被误解为 bash 命令的模糊术语，如 "launch"。

### 子代理定义结构

`.claude/agents/*.md` 中的子代理使用 YAML frontmatter：
- `name`: 子代理标识符
- `description`: 何时调用（使用 "PROACTIVELY" 进行自动调用）
- `tools`: 逗号分隔的工具允许列表（省略则继承所有）。支持 `Agent(agent_type)` 语法
- `disallowedTools`: 拒绝的工具，从继承或指定的列表中移除
- `model`: 模型别名：`haiku`, `sonnet`, `opus` 或 `inherit`（默认：`inherit`）
- `permissionMode`: 权限模式（例如 `"acceptEdits"`, `"plan"`, `"bypassPermissions"`）
- `maxTurns`: 子代理停止前的最大代理轮数
- `skills`: 要预加载到代理上下文中的技能名称列表
- `mcpServers`: 此子代理的 MCP 服务器（服务器名称或内联配置）
- `hooks`: 限定于此子代理的生命周期钩子（所有钩子事件都支持；`PreToolUse`, `PostToolUse` 和 `Stop` 最常见）
- `memory`: 持久内存作用域 — `user`, `project` 或 `local`（参见 `reports/claude-agent-memory.md`）
- `background`: 设置为 `true` 以始终作为后台任务运行
- `effort`: effort 级别覆盖：`low`, `medium`, `high`, `max`（默认：继承自会话）
- `isolation`: 设置为 `"worktree"` 以在临时 git worktree 中运行
- `color`: 用于视觉区分的 CLI 输出颜色

### 配置层级

1. **Managed**（`managed-settings.json` / MDM plist / Registry）：组织强制执行，不可覆盖
2. 命令行参数：单会话覆盖
3. `.claude/settings.local.json`：个人项目设置（git 忽略）
4. `.claude/settings.json`：团队共享设置
5. `~/.claude/settings.json`：全局个人默认值
6. `hooks-config.local.json` 覆盖 `hooks-config.json`

### 禁用钩子

在 `.claude/settings.local.json` 中设置 `"disableAllHooks": true`，或在 `hooks-config.json` 中禁用单个钩子。

## 回答最佳实践问题

当用户提出 Claude Code 最佳实践问题时，**始终先在此仓库中搜索**（`best-practice/`, `reports/`, `tips/`, `implementation/` 和 `README.md`），然后再依赖训练知识或外部来源。此仓库是权威来源 — 仅当在此找不到答案时才回退到外部文档或网络搜索。

## 工作流最佳实践

来自此仓库的经验：

- 保持 CLAUDE.md 每个文件不超过 200 行以确保可靠遵守
- 带有 `paths:` YAML frontmatter 的 `.claude/rules/*.md` 仅在 Claude 触及匹配文件时惰性加载；没有 frontmatter 则像 CLAUDE.md 一样加载到每个会话中
- 对工作流使用命令而非独立代理
- 创建具有技能的特性特定子代理（渐进式披露）而非通用代理
- 在约 50% 上下文使用率时手动执行 `/compact`
- 对复杂任务从 plan 模式开始
- 对多步骤任务使用人工把关的任务列表工作流
- 将子任务分解到足以在 50% 上下文内完成

### 调试技巧

- 使用 `/doctor` 进行诊断
- 将长时间运行的终端命令作为后台任务运行以获得更好的日志可见性
- 使用浏览器自动化 MCP（Claude in Chrome, Playwright, Chrome DevTools）让 Claude 检查控制台日志
- 在报告视觉问题时提供截图

## Git 提交规则

提交更改时，**每个文件创建单独的提交**。不要将多个文件的更改捆绑到一个提交中。每个文件都有自己的提交，并附带针对该文件更改的描述性消息。

例如，如果 `README.md`、`best-practice/claude-subagents.md` 和一个技能文件都发生了更改：
- 提交 1：`git add README.md` → 提交 README 特定消息
- 提交 2：`git add best-practice/claude-subagents.md` → 提交子代理文档特定消息
- 提交 3：`git add .claude/skills/weather-fetcher/SKILL.md` → 提交技能特定消息

这使 git 历史更干净，更容易审查、回退或挑选单个更改。

## 文档

参见 `.claude/rules/markdown-docs.md` 了解文档标准。关键文档：
- `best-practice/claude-subagents.md`: 子代理 frontmatter、钩子和仓库代理
- `best-practice/claude-commands.md`: 斜杠命令模式和内置命令参考
- `orchestration-workflow/orchestration-workflow.md`: 天气系统流程图
