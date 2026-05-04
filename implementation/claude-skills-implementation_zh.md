# Skills 实现

![最后更新](https://img.shields.io/badge/最后更新-2026年3月2日-white?style=flat&labelColor=555)

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code Best Practice</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

<a href="#weather-svg-creator"><img src="../!/tags/implemented-hd.svg" alt="已实现"></a>

本仓库实现了两个技能作为 **Command → Agent → Skill** 架构模式的一部分，展示了两种不同的技能调用模式：**agent skills（代理技能）**（预加载）和 **skills（技能）**（直接调用）。

---

## Weather SVG Creator（技能）

**文件**：[`.claude/skills/weather-svg-creator/SKILL.md`](../.claude/skills/weather-svg-creator/SKILL.md)

```yaml
---
name: weather-svg-creator
description: 创建显示迪拜当前温度的 SVG 天气卡片。将 SVG 写入
  orchestration-workflow/weather.svg 并更新
  orchestration-workflow/output.md。
---

# Weather SVG Creator 技能

该技能创建可视化的 SVG 天气卡片并写入输出文件。

## 任务
创建显示阿联酋迪拜温度的 SVG 天气卡片，
并将其与摘要一起写入输出文件。

## 说明
你将接收来自调用上下文的温度值和单位（摄氏或华氏）。

### 1. 创建 SVG 天气卡片
生成清晰的 SVG 天气卡片...

### 2. 写入 SVG 文件
将 SVG 内容写入 `orchestration-workflow/weather.svg`。

### 3. 写入输出摘要
写入 `orchestration-workflow/output.md`...

...
```

这是一个 **skill（技能）**——由命令通过 Skill 工具直接调用。它从对话上下文中接收温度数据，创建 SVG 天气卡片和输出摘要。

---

## Weather Fetcher（代理技能）

**文件**：[`.claude/skills/weather-fetcher/SKILL.md`](../.claude/skills/weather-fetcher/SKILL.md)

```yaml
---
name: weather-fetcher
description: 从 Open-Meteo API 获取阿联酋迪拜当前天气温度数据的说明
user-invocable: false
---

# Weather Fetcher 技能

该技能提供获取当前天气数据的说明。

## 任务
以请求的单位（摄氏或华氏）获取阿联酋迪拜的当前温度。

## 说明
1. 获取天气数据：使用 WebFetch 工具获取当前天气数据
   - 摄氏温度 URL：https://api.open-meteo.com/v1/forecast?latitude=25.2048&longitude=55.2708&current=temperature_2m&temperature_unit=celsius
   - 华氏温度 URL：https://api.open-meteo.com/v1/forecast?latitude=25.2048&longitude=55.2708&current=temperature_2m&temperature_unit=fahrenheit
2. 提取温度：从 JSON 响应中提取 `current.temperature_2m`
3. 返回结果：明确返回温度值和单位。

...
```

这是一个 **agent skill（代理技能）**——通过 `skills:` frontmatter 字段在启动时预加载到 `weather-agent` 中。它不是直接调用的，而是作为领域知识注入到代理的上下文中。注意 `user-invocable: false` 将其隐藏于 `/` 命令菜单。

---

## 两种技能模式

| 模式 | 调用方式 | 示例 | 主要区别 |
|---------|-----------|---------|----------------|
| **Skill（技能）** | `Skill(skill: "name")` | `weather-svg-creator` | 通过 Skill 工具直接调用 |
| **Agent Skill（代理技能）** | 通过 `skills:` 字段预加载 | `weather-fetcher` | 启动时注入到代理上下文 |

---

## ![如何使用](../!/tags/how-to-use.svg)

**Skill（技能）**——通过斜杠命令直接调用：
```bash
$ claude
> /weather-svg-creator
```

---

## ![如何实现](../!/tags/how-to-implement.svg)

让 Claude 为你创建一个——它将生成带有 YAML frontmatter 和正文的 markdown 文件，位于 `.claude/skills/my-skill/SKILL.md`

# 我的技能

技能功能的说明。
```
