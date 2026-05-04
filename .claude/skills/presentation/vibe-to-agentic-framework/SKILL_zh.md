---
name: vibe-to-agentic-framework
description: 演示文稿背后的概念框架 — "Vibe Coding 到 Agentic Engineering"意味着什么，为什么旅程以这种方式构建，以及每张幻灯片如何适应叙事序列
---

# "Vibe Coding to Agentic Engineering" 框架

此 skill 教授演示文稿背后的**概念模型**。每张幻灯片和每个章节的存在都是为了讲述一个故事：开发者如何从无结构的"vibe coding"（Low 级别）逐步过渡到高级的 agentic engineering（High 级别）。

## 核心概念

**Vibe Coding（Low 级别）** 是指开发者使用 Claude Code 时没有任何结构 — 没有项目上下文、没有约定、没有可复用的知识。每次提示都是一次抛硬币。Claude 可能会创建随机的端点、忽略现有模式、跳过测试并产生不一致的代码。每次交互，代码库都会朝着混乱方向漂移。

**Agentic Engineering（High 级别）** 是指 Claude Code 作为一个完全配置的工程系统运行。它了解项目架构（CLAUDE.md）、遵循范围限定的约定（Rules）、按需加载领域专业知识（Skills）、委托给专门的工人（Agents）、编排多步骤工作流（Commands）、自动化生命周期事件（Hooks）并连接到外部工具（MCP Servers）。每次提示都会产生一致的、经过测试的、生产质量的代码。

这两个极端之间的旅程是**渐进和累积的**。每个最佳实践都建立在前一个之上，演示文稿按照开发者应该采用它们的顺序教授它们。

## 4 级旅程系统

演示文稿使用 4 级评分系统而非百分比栏：

| 级别 | 顺序 | 颜色 | 旅程栏高度 | 描述 |
|-------|-------|-------|--------------------|-------------|
| Low | 1 | 红/橙色（`hsl(0, 70%, 45%)`） | 25% | Vibe coding 领域 — 无结构 |
| Medium | 2 | 黄色（`hsl(40, 70%, 45%)`） | 50% | 结构化工作流，一些自动化 |
| High | 3 | 浅绿色（`hsl(80, 70%, 45%)`） | 75% | 领域知识、skills、自定义 agents |
| Pro | 4 | 深绿色（`hsl(120, 70%, 45%)`） | 100% | 完整的 agentic engineering，多代理团队 |

旅程栏在幻灯片 1（标题幻灯片）上隐藏，从幻灯片 2 开始显示。级别通过关键转换幻灯片上的 `data-level` 属性设置，并被后续幻灯片继承直到下一个级别变化。当级别变化时，一个 `.level-badge` 由 JS 注入到幻灯片的 `h1` 上（不要在 HTML 中硬编码这些）。

## 运行示例：TodoApp Monorepo

每种技术都在一个现实的全栈项目上演示。演示文稿展示了从普通项目（vibe coding）到具有完整 Claude Code 配置（agentic engineering）的转变：

**之前（Vibe Coding）：**
```
todoapp/
├── backend/          # FastAPI（Python）
│   ├── main.py
│   ├── routes/
│   ├── models/
│   └── tests/
└── frontend/         # Next.js（TypeScript）
    ├── components/
    ├── pages/
    └── lib/
```

**之后（Agentic Engineering）：**
```
todoapp/
├── .claude/                  # Claude Code 配置
│   ├── agents/               # 自定义子代理
│   ├── skills/               # 领域知识
│   ├── commands/             # 斜杠命令
│   ├── hooks/                # 生命周期脚本
│   ├── rules/                # 模块化指令
│   ├── settings.json         # 团队设置
│   └── settings.local.json   # 个人设置
├── backend/
│   └── CLAUDE.md             # 后端指令
├── frontend/
│   └── CLAUDE.md             # 前端指令
├── .mcp.json                 # 托管的 MCP 服务器
└── CLAUDE.md                 # 项目指令
```

**为什么用 TodoApp？** 它足够小可以放在幻灯片上，但又足够复杂可以展示真实问题：具有路由模式和测试约定的后端、具有组件层次结构和设计 token 的前端，以及横切关注点（如添加新功能）需要双方协调的 monorepo 结构。

TodoApp 使 vibe-coding 问题变得具体：没有结构，要求 Claude"添加一个笔记功能"会产生一个不遵循 `routes/todos.py` 模式的随机 `/api/notes` 端点、一个没有侧边栏导航的独立页面以及零个测试。在完整的 agentic 设置下，相同的请求会产生一个遵循现有模式的路由、一个集成到侧边栏的页面以及与 `test_todos.py` 风格匹配的测试。

## 旅程序列：为什么是这个顺序

演示文稿遵循精心设计的教学顺序。每个章节解锁一个新的能力层：

### 第 0 部分：介绍（幻灯片 1-4，无权重）
**目的：** 铺陈背景。介绍 TodoApp，定义 vibe coding，并展示目标。
- 标题幻灯片建立旅程隐喻
- 示例项目展示转变：TodoApp 的前后对比 — 普通项目结构与具有完整 Claude Code 配置（.claude/、CLAUDE.md、.mcp.json 等）的项目
- "什么是 Vibe Coding？"创建了 0% 的基线 — 痛点
- 旅程地图提供了一个可点击的 TOC，显示前方的完整路径

### 第 1 部分：准备工作（幻灯片 5-9，无权重）
**目的：** 安装并运行 Claude Code。这纯粹是后勤 — 还没有工程实践。
- 安装、认证、首次会话、界面概览
- 没有权重，因为知道如何安装工具并不能提高代码质量
- "首次会话"本身就是 vibe coding — 这是故意的，让开发者亲身体验 0% 状态

### 第 2 部分：更好的提示（幻灯片 10-17，级别：Low）
**目的：** 第一个真正的改进。更好的输入产生更好的输出，即使没有任何项目配置。
- **好提示 vs 坏提示：** 具体、范围限定的提示 vs 模糊的请求。最简单的改进。
- **提供上下文：** 使用 `@files` 给 Claude 所需的代码。立即减少幻觉。
- **上下文窗口与 /compact：** 了解有限的上下文窗口可以防止长时间会话中的响应质量下降。
- **计划模式：** `/plan` 强制在编码前思考。防止在错误方法上浪费精力。

**为什么是 Low 级别：** 提示是基础性的但有限的。它改善了个体交互，但不会创建持久的项目知识。每个会话从零开始。

### 第 3 部分：项目记忆（幻灯片 18-24，级别：Medium）
**目的：** 从会话级知识跃升到项目级知识。Claude 现在可以跨会话记忆。
- **CLAUDE.md 与 /init：** 项目的"Claude 的 README"。建立架构、技术栈和约定。这是最有影响力的单个文件。
- **包含什么：** 编写有效 CLAUDE.md 内容的实用指导（保持在 150 行以下，关注 Claude 需要知道的内容）。
- **Rules：** `.claude/rules/` 中路径范围限定的约定。Rules 是一个倍增器 — 它们自动应用于每个匹配的文件，无需开发者努力就能强制执行一致性。一个 `backend-testing.md` rule 确保每个测试永远遵循相同的模式。

**为什么是 Medium 级别：** 项目记忆将 Claude 从无状态工具转变为上下文感知的协作者。但仅凭知识无法创建工作流。

### 第 4 部分：结构化工作流（幻灯片 25-28，级别：Medium）
**目的：** 防止浪费精力并提高执行质量的系统性方法。
- **任务列表：** 将复杂工作分解为可追踪的步骤。防止范围漂移并确保完整性。
- **模型选择：** 选择正确的模型（Opus 用于架构，Sonnet 用于实现，Haiku 用于快速任务）优化成本和质量。

**为什么仍然是 Medium 级别：** 工作流很重要但相对简单的概念。它们建立在第 3 部分的项目记忆基础上，并更系统地使用它。到 High 的步骤伴随着领域知识。

### 第 5 部分：领域知识（幻灯片 29-33，级别：High）
**目的：** 可复用的按需专业知识。Skills 是静态记忆（CLAUDE.md/Rules）和动态代理之间的桥梁。
- **什么是 Skills：** Skills 作为打包的领域知识，Claude 在相关时加载。渐进式披露的概念。
- **创建 Skills：** 实践：为 TodoApp 构建一个 `frontend-conventions` skill，教授 Tailwind tokens、组件模式和侧边栏集成。
- **Skill Frontmatter 与调用：** 技术细节：YAML frontmatter、手动与自动发现调用、`context: fork` 选项。

**为什么是 High 级别：** Skills 是第一个"倍增器"概念 — 一个 skill 定义改善其领域内每个未来的交互。但 skills 是被动的知识；它们需要 agents 才能变得活跃。

### 第 6 部分：Agentic Engineering（幻灯片 34-46，级别：High）
**目的：** 本演示文稿涵盖的目标。自主的、专门的代理协调工作以端到端地构建功能。
- **什么是 Agents：** 具有受限工具和预加载 skills 的专门子代理的概念。
- **前端工程师代理：** 一个具体代理，使用 TodoApp 的前端约定、向侧边栏添加路由、遵循设计 tokens。前后对比展示了转变。
- **后端工程师代理：** 后端的并行代理 — 遵循 FastAPI 路由模式、SQLAlchemy 模型、编写匹配现有风格的测试。
- **Commands 与编排：** 巅峰模式：Command → Agent → Skills。一个 `/add-feature` 命令协调前端+后端代理，每个都有自己的 skills，以交付完整的功能。这是架构的顶峰。
- **Hooks 与 MCP：** 生命周期自动化（提交前检查、声音通知）和外部工具集成。最终的自动化层。
- **Command → Agent → Skills：** 完整的架构图。显示所有部分如何连接：命令调用代理，代理加载 skills，skills 提供知识。这是"High 级别"理解的幻灯片。

**为什么是 High 级别：** 本节涵盖了本演示文稿教授的最高价值实践。之前的一切都在为此铺垫。编排和 agentic 工作流代表了本课程覆盖的顶部 — 完整的 Pro（多代理团队、高级编排模式）超出了本演示文稿的范围。

### High 级别幻灯片（幻灯片 44）
庆祝时刻。显示完整的 TodoApp 配置：
- CLAUDE.md 用于项目上下文
- Rules 用于路径范围限定的约定
- Skills 用于领域知识
- Agents 用于一致的执行
- Commands 用于编排的工作流
- Hooks 用于生命周期自动化
- MCP servers 用于外部工具

### 附录（幻灯片 47+，无权重）
**目的：** 参考资料。每个命令、设置和配置选项。没有权重，因为这些都是参考查询，不是旅程里程碑。包括：工具使用、所有斜杠命令、提交/PR 工作流、自定义选项、调试技巧和黄金规则。

## 如何在编辑幻灯片时使用此框架

在创建或修改幻灯片时，考虑：

1. **这个概念在旅程中的位置？** 关于"提示中更好的错误消息"的幻灯片属于第 2 部分（提示，Low 级别）。关于"代理记忆作用域"的幻灯片属于第 6 部分（agentic，High 级别）。

2. **前后对比是什么？** 每张重要的幻灯片都应隐式或显式地展示对比：在 Low 级别（vibe coding）会发生什么 vs 使用此技术会发生什么。使用 TodoApp 使其具体化。

3. **级别分配感觉正确吗？** 级别转换发生在部分章节边界处。章节内的单个幻灯片继承该章节的级别。

4. **它建立在之前的内容之上吗？** Skills 假定开发者已经了解 CLAUDE.md 和 Rules。Agents 假定他们了解 Skills。Commands 假定他们了解 Agents。永远不要在概念的章节之前引用它。

5. **使用 TodoApp。** 抽象的解释会失去观众。展示实际的 `routes/todos.py` 代码、实际的 `Sidebar.tsx` 组件、实际的 `CLAUDE.md` 内容。运行示例使框架变得具体可感。

## 级别转换参考表

| 幻灯片 | 幻灯片名称 | data-level | 级别标签 |
|-------|-----------|------------|-------------|
| 10 | Better Prompting（章节分隔符） | `data-level="low"` | Low |
| 18 | Project Memory（章节分隔符） | `data-level="medium"` | Medium |
| 29 | Domain Knowledge（章节分隔符） | `data-level="high"` | High |
| 34 | Agentic Engineering（章节分隔符） | `data-level="high"` | High |

所有其他幻灯片从它们之前最后一个 `data-level` 属性继承级别。幻灯片 1-9（介绍 + 准备工作）没有级别，栏隐藏直到幻灯片 2 显示"Low"（幻灯片 2-9 在幻灯片 10 的第一次级别转换之前，因此栏显示为空/零直到幻灯片 10）。

**注意：** 主演示文稿（`presentation/index.html`）上限为 **High** 级别 — 不使用 `data-level="pro"`。Pro 刻度标记在旅程栏上保持可见作为理论上的上限，但填充从未达到它。视频演示文稿（`1-video-workflow.html`）上限为 **Medium** 级别。
