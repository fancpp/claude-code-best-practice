---
description: 获取迪拜天气并创建 SVG 天气卡片
model: haiku
allowed-tools:
  - AskUserQuestion
  - Agent
  - Skill
---

# 天气编排器命令

获取迪拜（阿联酋）的当前温度并创建可视化 SVG 天气卡片。

## 执行合约（不可协商）

你必须通过委托给 `weather-agent` 子代理来完成此命令。禁止以下行为：

- 通过 Bash、WebFetch 或任何其他工具自行获取天气数据
- 跳过步骤 1（用户的单位偏好是代理所需的输入）
- 在代理返回温度之前调用 `weather-svg-creator`

如果无法调用代理工具，请停止并向用户报告错误。不要自行临时处理。

## 工作流

### 步骤 1：询问用户偏好

使用 AskUserQuestion 工具询问用户需要摄氏温度还是华氏温度。在进行下一步之前记录所选单位。

### 步骤 2：通过代理获取天气数据

使用 Agent 工具调用天气代理：

- subagent_type：weather-agent
- description：获取迪拜天气数据
- prompt：获取迪拜（阿联酋）当前的[用户请求的单位]温度。返回数值温度值和单位。该代理预加载了一项技能（weather-fetcher），其中提供了详细说明。
- model：haiku

等待代理完成并记录返回的温度值和单位。

**故障关闭防护**：如果代理未返回数值温度值和单位，不要继续执行步骤 3。向用户报告失败并停止。

### 步骤 3：创建 SVG 天气卡片

使用 Skill 工具调用 weather-svg-creator 技能：

- skill：weather-svg-creator

该技能将使用步骤 2 中的温度值和单位（在当前上下文中可用）创建 SVG 卡片并写入输出文件。

## 输出摘要

向用户提供清晰的摘要，显示：

- 请求的温度单位
- 从迪拜获取的温度
- SVG 卡片已创建于 `orchestration-workflow/weather.svg`
- 摘要已写入 `orchestration-workflow/output.md`
