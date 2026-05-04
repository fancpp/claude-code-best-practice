---
description: 获取迪拜当前时间（GST，UTC+4）并创建可视化 SVG 时间卡片
model: haiku
---

# 时间编排器命令

获取迪拜当前时间（Asia/Dubai，UTC+4）并创建可视化 SVG 时间卡片。

## 工作流

### 第 1 步：获取当前迪拜时间

使用 Agent 工具调用 time agent：
- subagent_type：time-agent
- description：获取当前迪拜时间
- prompt：获取迪拜当前时间（Asia/Dubai，UTC+4）。精确返回三个字段：`time`（时间部分，例如 "14:30:45"）、`timezone`（"GST (UTC+4)"）和 `formatted`（完整格式化字符串，例如 "2026-03-12 14:30:45 +04"）。该代理有一个预加载的技能（time-fetcher）提供详细指令。
- model：haiku

等待代理完成并捕获返回的时间数据。

### 数据契约

time-agent 必须返回这三个字段：
- **time**：时间部分（例如 "14:30:45"）
- **timezone**："GST (UTC+4)"
- **formatted**：完整格式化字符串（例如 "2026-03-12 14:30:45 +04"）

### 第 2 步：创建 SVG 时间卡片

使用 Skill 工具调用 time-svg-creator 技能：
- skill：time-svg-creator
- args：传递第 1 步的时间数据 — 包括 `time`、`timezone` 和 `formatted` 值

该技能将使用第 1 步的时间数据（在当前上下文中可用）来创建 SVG 卡片并写入输出文件。

## 关键要求

1. **对 time-agent 使用 Agent 工具**：不要使用 bash 命令调用代理。必须使用 `subagent_type: "time-agent"` 的 Agent 工具。
2. **对 SVG 创建者使用 Skill 工具**：通过 `skill: "time-svg-creator"` 的 Skill 工具调用 SVG 创建者，而不是 Agent 工具。
3. **顺序流程**：代理必须先完成并返回时间数据，然后才能调用技能。不要并行运行它们。
4. **数据传递**：确保代理响应中的所有三个字段（time、timezone、formatted）在调用技能时在上下文中可用。

## 输出摘要

两个步骤完成后，向用户提供清晰的摘要，显示：
- 已获取当前迪拜时间
- 时区：GST (UTC+4)
- 完整格式化时间戳
- SVG 卡片已创建于 `agent-teams/output/dubai-time.svg`
- 摘要已写入 `agent-teams/output/output.md`
