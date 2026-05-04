---
paths:
  - "presentation/**"
---

# 演示文稿委托

## 委托规则

任何更新、修改或修复演示文稿的请求必须由匹配的每个演示文稿代理处理。**切勿直接编辑演示文稿 HTML。** 根据用户所指的演示文稿进行路由：

| 演示文稿 | 路径 | 代理 |
|---|---|---|
| Vibe Coding 到 Agentic Engineering | `presentation/vibe-coding-to-agentic-engineering/index.html` | `presentation-vibe-coding` |
| Claude Code 和 Gemini CLI（GDG Kolachi 活动幻灯片） | `presentation/2026-04-25-gdg-kolachi-cli-claude-code-gemini/index.html` | `presentation-claude-gemini` |
| Claude Code 最佳实践（规范可复用幻灯片） | `presentation/claude-code-best-practice/index.html` | `presentation-claude-code` |

通过 Agent 工具调用：

```
Agent(subagent_type="presentation-vibe-coding", description="...", prompt="...")
Agent(subagent_type="presentation-claude-gemini", description="...", prompt="...")
Agent(subagent_type="presentation-claude-code", description="...", prompt="...")
```

如果用户说"演示文稿"而没有指定是哪一个，请在委托前询问其具体指哪一个。注意"主演示文稿"或"最佳实践幻灯片"通常指 `presentation-claude-code` — 规范的可复用幻灯片 — 但如果有歧义请确认。

## 原因

每个演示文稿都有自己的幻灯片编号、级别系统和目标受众。每个演示文稿的代理让每一个都能保持专注的知识库并自我进化，而不会相互交叉污染。vibe-coding 代理预加载了特定于该幻灯片的框架/结构/样式技能。claude-gemini 代理面向非技术性的 GDG 活动受众，并使用带有 6 个级别的旅程栏。claude-code 代理拥有规范的可复用最佳实践幻灯片（于 2026-04-30 从 GDG 幻灯片分支而来）— 相同的受众语气，更简单的结构（仅级别徽章，无旅程栏），与活动无关的身份。
