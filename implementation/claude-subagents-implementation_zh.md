# Sub-agents 实现

![最后更新](https://img.shields.io/badge/最后更新-2026年3月2日_19_59_PKT-white?style=flat&labelColor=555)

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code Best Practice</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

<a href="#weather-agent"><img src="../!/tags/implemented-hd.svg" alt="已实现"></a>

天气代理在本仓库中实现，作为 **Command → Agent → Skill** 架构模式的示例，展示了两种不同的技能模式。

---

## Weather Agent

**文件**：[`.claude/agents/weather-agent.md`](../.claude/agents/weather-agent.md)

```yaml
---
name: weather-agent
description: 当你需要获取阿联酋迪拜的天气数据时，主动使用此代理。
  该代理使用其预加载的 weather-fetcher 技能从 Open-Meteo
  获取实时温度。
allowedTools:
  - "Read"
  - "Skill"
model: sonnet
color: green
maxTurns: 5
permissionMode: acceptEdits
memory: project
skills:
  - weather-fetcher
---

# Weather Agent

你是一个专门的天气代理，负责获取阿联酋迪拜的天气数据。

## 你的任务

按照预加载技能的说明执行天气工作流：

1. **获取**：遵循 `weather-fetcher` 技能的说明获取当前温度
2. **报告**：向调用者返回温度值和单位
3. **记忆**：更新你的代理记忆，记录用于历史追踪的读数详情

...
```

该代理有一个预加载的技能（`weather-fetcher`），提供从 Open-Meteo 获取数据的说明。它向调用的命令返回温度值和单位。

---

## ![如何使用](../!/tags/how-to-use.svg)

```bash
$ claude
> 迪拜的天气怎么样？
```

---

## ![如何实现](../!/tags/how-to-implement.svg)

你可以使用 `/agents` 命令创建代理，
```bash
$ claude
> /agents
```

或者让 Claude 为你创建一个——它将生成带有 YAML frontmatter 和正文的 markdown 文件，位于 `.claude/agents/<name>.md`

---

<a href="https://github.com/shanraisshan/claude-code-best-practice#orchestration-workflow"><img src="../!/tags/orchestration-workflow-hd.svg" alt="编排工作流"></a>

天气代理是 Command → Agent → Skill 编排模式中的 **Agent** 组件。它从 `/weather-orchestrator` 命令接收工作流，并使用其预加载的技能（`weather-fetcher`）获取温度。然后命令调用独立的 `weather-svg-creator` 技能来创建视觉输出。

<p align="center">
  <img src="../orchestration-workflow/orchestration-workflow.svg" alt="Command Skill Agent 架构流程图" width="100%">
</p>

| 组件 | 角色 | 本仓库 |
|-----------|------|-----------|
| **Command** | 入口点，用户交互 | [`/weather-orchestrator`](../.claude/commands/weather-orchestrator.md) |
| **Agent** | 使用预加载技能获取数据（代理技能） | [`weather-agent`](../.claude/agents/weather-agent.md) 带有 [`weather-fetcher`](../.claude/skills/weather-fetcher/SKILL.md) |
| **Skill** | 独立创建输出（技能） | [`weather-svg-creator`](../.claude/skills/weather-svg-creator/SKILL.md) |
