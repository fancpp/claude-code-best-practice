---
name: weather-svg-creator
description: 创建显示迪拜当前温度的 SVG 天气卡片。将 SVG 写入 orchestration-workflow/weather.svg 并更新 orchestration-workflow/output.md。
---

# Weather SVG Creator Skill（天气 SVG 创建技能）

为阿联酋迪拜创建可视化的 SVG 天气卡片，并写入输出文件。

## 任务

你将收到来自调用上下文的温度值和单位（摄氏度或华氏度）。创建 SVG 天气卡片并写入 SVG 文件和 markdown 摘要。

## 指令

1. **创建 SVG** — 使用 [reference.md](reference.md) 中的 SVG 模板，将占位符替换为实际值
2. **写入 SVG 文件** — 读取后写入到 `orchestration-workflow/weather.svg`
3. **写入摘要** — 使用 [reference.md](reference.md) 中的 markdown 模板，读取后写入到 `orchestration-workflow/output.md`

## 规则

- 使用提供的精确温度值和单位 — 不要重新获取或修改
- SVG 必须是自包含且有效的
- 两个输出文件均位于 `orchestration-workflow/` 目录下

## 附加资源

- 有关 SVG 模板、输出模板和设计规范，请参见 [reference.md](reference.md)
- 有关示例输入/输出对，请参见 [examples.md](examples.md)
