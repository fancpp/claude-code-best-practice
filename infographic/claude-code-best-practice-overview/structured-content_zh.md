# Claude Code Best Practice 知识地图

## Overview

这是对 shanraisshan/claude-code-best-practice 仓库的全面知识可视化。该仓库是 Claude Code 最佳实践的最全面社区知识库，涵盖 6 个核心概念、4 类知识资产、12 个工作流框架对比和可运行的编排演示，是任何 Claude Code 用户的首选参考资源。

## Learning Objectives
The viewer will understand:
1. 仓库整体规模（6,556行 Markdown）+ 核心定位（GitHub Trending #1）
2. 六大核心概念（Agents/Commands/Skills/Hooks/MCP/Settings）的功能定义
3. 四类知识资产的内容分布和数量指标
4. Command → Agent → Skill 编排工作流的核心模式
5. 仓库生态地图（工作流框架对比 + 其他相关仓库）

---

## Section 1: 仓库概览

**Key Concept**: 一个专注于 Claude Code 最佳实践的综合参考知识库，非应用代码项目

**Content**:
- 维护者：Shayan（社区成员）
- 定位："from vibe coding to agentic engineering — practice makes claude perfect"
- 性质：参考材料 / 知识库 / 教程
- 语言：纯 Markdown（无源代码）
- GitHub Stars：GitHub Trending #1，持续增长中
- 总文档量：约 6,556 行 Markdown + 大量 SVG/PNG 资源

**Visual Element**:
- Type: hero module with key stats
- Subject: Repository header with badge, star count, line count
- Treatment: Large numbers highlighted, repository name prominent

**Text Labels**:
- Headline: "仓库概览"
- Labels: "6,556行 Markdown", "GitHub Trending #1", "纯 Markdown 知识库"

---

## Section 2: 六大核心概念

**Key Concept**: Claude Code 的六个核心可扩展性概念，每个都在仓库中有最佳实践 + 实现文档

**Content**:
- Subagents (.claude/agents/): 子代理定义文件，预配置 YAML 前端元数据
- Commands (.claude/commands/): 斜杠命令，可反复使用的工作流入口
- Skills (.claude/skills/<name>/SKILL.md): 技能文件，文件夹结构包含参考/脚本/示例
- Workflows: Command → Agent → Skill 编排模式
- Hooks (.claude/hooks/): 跨平台音效通知系统，覆盖 27 种钩子事件
- Memory: CLAUDE.md + .claude/rules/ 多层次记忆系统
- MCP Servers (.mcp.json): Playwright, Context7, DeepWiki
- Settings (settings.json): 五层配置层次，从组织强制到全局默认

**Visual Element**:
- Type: icon grid with connecting lines
- Subject: 8 concept cards arranged in a 2x4 or 4x2 grid
- Treatment: Each card has an icon, concept name, brief description

**Text Labels**:
- Headline: "六大核心概念"
- Labels: "Subagents", "Commands", "Skills", "Workflows", "Hooks", "MCP", "Memory", "Settings"

---

## Section 3: 知识资产盘点

**Key Concept**: 仓库包含四类主要知识资产，按类型和数量分布

**Content**:
- 最佳实践文档: 8 篇, 1,923 行 — 全面的实践参考
  - claude-settings.md: 1,132行（最大文档）
  - 其他: CLI 启动标志、MCP、Commands、Memory 等
- 深度报告: 12 篇, 2,790 行 — 深入的专题研究
  - Advanced Tool Use (420行)、LLM Degradation (360行)、Browser MCP 对比 (345行)
- 技巧合集: 9 篇, 1,339 行, 共 83 条技巧
  - 来源: Boris Cherny（创建者）、Thariq（Anthropic）、社区
  - 分类: 15 个主题，从 Prompting 到 Daily
- 实现指南: 5 篇子代理、2 个命令、5 个技能、3 个 MCP

**Visual Element**:
- Type: stacked horizontal bar chart or donut chart
- Subject: Four asset categories with proportional sizes
- Treatment: Color-coded by category, line counts prominently displayed

**Text Labels**:
- Headline: "知识资产盘点"
- Labels: "Best Practices 1,923行", "Reports 2,790行", "Tips 1,339行", "Implementations"

---

## Section 4: 编排工作流

**Key Concept**: 仓库的核心演示 —— Command → Agent → Skill 三阶编排模式

**Content**:
- 用户输入 /weather-orchestrator
  - 步骤1: Command 启动天气编排命令
  - 步骤2: → 调用 weather-agent（子代理）
    - 预加载 weather-fetcher skill（代理技能模式）
    - 通过 Open-Meteo API 获取实时温度数据
  - 步骤3: → 返回主上下文
  - 步骤4: → 调用 weather-svg-creator skill（技能模式）
    - 生成天气 SVG 卡片
    - 写入 orchestration-workflow/weather.svg + output.md

**Visual Element**:
- Type: horizontal workflow flow diagram with arrows
- Subject: Three connected stages with details under each
- Treatment: Arrow connectors between stages, numbered steps

**Text Labels**:
- Headline: "编排工作流"
- Labels: "① Command 启动", "② Agent 获取数据", "③ Skill 生成 SVG"

---

## Section 5: 生态地图

**Key Concept**: 仓库维护了全面的 Claude Code 工作流生态对比

**Content**:
- 12 个主流工作流框架对比：
  - Superpowers (175k ★): 完整 Skill 工作流体系
  - Everything Claude Code (171k ★): 最丰富的命令/代理集合
  - Spec Kit (92k ★): 规格驱动开发
  - gstack (88k ★): CEO/Eng/Design 三层审查
  - Get Shit Done (59k ★): 完整项目周期管理
  - 其他: BMAD, OpenSpec, oh-my-claudecode, agent-skills, Compound Engineering, HumanLayer
- 6 大技能集合仓库：
  - anthropics/skills (127k ★), 17 skills
  - mattpocock/skills (51k ★), 18 skills
  - agent-skills (27k ★), 21 skills
- 相关仓库：Claude Code Hooks、Codex CLI 最佳实践、Gemini CLI 最佳实践

**Visual Element**:
- Type: ranked list with star counts
- Subject: Frameworks sorted by GitHub stars
- Treatment: Star icons, color bars for star count

**Text Labels**:
- Headline: "生态地图"
- Labels: "12个工作流框架", "6个技能集合", "4个相关仓库"

---

## Section 6: 质量评估

**Key Concept**: 仓库的优势和改进空间

**Content**:
- 六大优势：
  - 信息密度高（6,500+ 行）
  - 可操作性强（概念 + 实践 + 配置）
  - 来源权威（Boris Cherny / Thariq / 社区）
  - 结构清晰（相对链接互引）
  - 持续维护（活跃的 git 提交）
  - 社区驱动（大量社区贡献）
- 四大改进空间：
  - claude-settings.md (1,132行) 接近可读性上限
  - 无自动化测试验证文档准确性
  - 缺乏独立搜索索引或术语表
  - README、CLAUDE.md、best-practice 之间部分内容重叠

**Visual Element**:
- Type: pros vs cons comparison
- Subject: Left side (green) advantages, right side (amber) improvements
- Treatment: Checkmark vs warning icon, color-coded

**Text Labels**:
- Headline: "质量评估"
- Labels: "✓ 六大优势", "△ 四大改进空间"

---

## Data Points (Verbatim)

### Statistics
- "总文档量: 约 6,556 行 Markdown + 大量 SVG/PNG 资源"
- "8 篇最佳实践文档 (1,923行)"
- "12 篇深度报告 (2,790行)"
- "9 篇技巧合集 (1,339行, 共83条技巧)"
- "claude-settings.md 最大 — 1,132行"
- "5 个子代理、2 个斜杠命令、5 个技能、3 个 MCP 服务器"
- "覆盖 27 种钩子事件"
- "12 个主流工作流框架对比"

### Key Terms
- **Subagents**: 通过 YAML 前端元数据定义的子代理，位于 .claude/agents/
- **Commands**: 斜杠命令，位于 .claude/commands/
- **Skills**: 以文件夹结构组织的技能定义，位于 .claude/skills/<name>/SKILL.md
- **Hooks**: 跨平台音效通知系统，覆盖全部生命周期事件
- **Workflows**: Command → Agent → Skill 的三阶编排模式

---

## Design Instructions

### Style Preferences
- 高密度信息展示
- 知识卡片风格
- 中文为主

### Layout Preferences
- dense-modules 布局，最大化信息密度
- 6-7 个信息模块，每个模块包含具体数据

### Other Requirements
- 配色清晰，层次分明
- 数据准确性优先
- 适合社交媒体分享的知识卡片格式
