按照以下规范创建专业信息图：

## Image Specifications

- **Type**: Infographic
- **Layout**: dense-modules
- **Style**: pop-laboratory
- **Aspect Ratio**: 9:16
- **Language**: zh

## Core Principles

- Follow the layout structure precisely for information architecture
- Apply style aesthetics consistently throughout
- If content involves sensitive or copyrighted figures, create stylistically similar alternatives
- Keep information concise, highlight keywords and core concepts
- Use ample whitespace for visual clarity
- Maintain clear visual hierarchy

## Text Requirements

- All text must match the specified style treatment
- Main titles should be prominent and readable
- Key concepts should be visually emphasized
- Labels should be clear and appropriately sized
- Use the specified language for all text content

## Layout Guidelines

# dense-modules

High-density modular layout with 6-7 typed information modules packed with concrete data.

## Structure

- 6-7 distinct modules per image, each serving a specific information function
- Every module contains concrete data: brand names, numbers, percentages, parameters
- Minimal whitespace—compact spacing prioritized over breathing room
- Smaller text acceptable to maximize information density
- Each module identified by coordinate label or section marker (e.g., MOD-1, SEC-A)

## Module Archetypes

| Module | Purpose | Content Requirements |
|--------|---------|---------------------|
| **Brand/Selection Array** | Grid of options with recommendations | 4-8 items with icons, names, brief descriptions; highlight "best choice" |
| **Specification Scale** | Quality/measurement gauge | 3-5 levels with precise numerical increments, quality indicators (emoji faces, checkmarks) |
| **Deep Dive/Detail** | Technical breakdown of key item | Zoom-in callouts, internal components, cross-section or exploded view |
| **Scenario Comparison** | Side-by-side use cases | 3-6 scenarios with specific recommendations and data per scenario |
| **Identification Tips** | How-to checklist | 3-5 inspection methods: look/test/check/ask format |
| **Warning/Pitfall Zone** | Critical mistakes to avoid | 3-5 pitfalls with consequences, 1-2 correct approaches; high visual contrast |
| **Quick Reference** | Compact summary | Dense table, one-line summaries, decision flowchart, or key takeaways |

## Variants

Use **free-flowing** variant: Magazine-style layout with dotted frames, varying module sizes, connected by arrows.

## Best For

- Product selection guides and buying guides
- Multi-dimensional comparison content
- Data-rich educational materials
- "Avoid pitfalls" / "complete guide" formats

## Visual Elements

- Module boundary markers (thick lines, dotted frames, or coordinate grids)
- Quality indicators per module (emoji faces, checkmarks, crosses, crowns)
- Data callout boxes with highlighted numbers
- Comparison arrows and progression indicators
- Warning/alert visual markers for pitfall modules
- Metadata in corners (page numbers, timestamps, small barcodes)

## Text Placement

- Main title at top, prominent and impactful
- Subtitle with module count ("X大维度全面解析...")
- Module headers inside colored badges or labeled frames
- Body text compact, multiple columns within modules
- Numbers highlighted with accent colors, slightly larger than body text

## Information Density Rules

- Every corner should contain useful information or metadata
- No decorative-only empty space
- Text size may be reduced to fit more content—information over font size
- Each module must have specific data points, not generic descriptions
- Balance between density and readability: dense but organized

## Style Guidelines

# pop-laboratory

Lab manual precision meets pop art color impact—coordinate systems, technical diagrams, and fluorescent accents on blueprint grid.

## Color Palette

- Background: Professional grayish-white with faint blueprint grid texture (#F2F2F2)
- Primary: Muted teal/sage green (#B8D8BE) for major functional blocks and data zones
- High-alert accent: Vibrant fluorescent pink (#E91E63) strictly for warnings, critical data, or "winner" highlights
- Marker highlights: Vivid lemon yellow (#FFF200) as translucent highlighter effect for keywords
- Line art: Ultra-fine charcoal brown (#2D2926) for technical grids, coordinates, and hairlines

## Visual Elements

- Coordinate-style labels on every module (e.g., R-20, G-02, SEC-08)
- Technical diagrams: exploded views, cross-sections with anchor points, architectural skeletal lines
- Vertical/horizontal rulers with precise markers (0.5mm, 1.8mm, 45°)
- "Marker-over-print" effect: color blocks slightly offset from text, postmodern print feel
- Cross-hair targets, mathematical symbols (Σ, Δ, ∞), directional arrows (X/Y axis)
- Microscopic detail annotations alongside macroscopic bold headers
- Corner metadata: tiny barcodes, timestamps, technical parameters
- High contrast between massive bold headers and tiny 8pt-style annotations

## Typography

- Headers: Bold brutalist characters, high visual impact
- Body: Professional sans-serif or crisp technical print
- Numbers: Large, highlighted with yellow or blue to stand out
- Annotations: Ultra-crisp, small technical labels

## Style Enforcement

- Strictly systematic color usage: only teal, pink, yellow, charcoal—no rainbow palette
- Sufficient fine grid lines and coordinate annotations throughout
- Maintain tension between large impactful headers and small precise parameters
- Lab manual aesthetic: mix of microscopic details and macroscopic data

## Avoid

- Cute or cartoonish doodles
- Soft pastels or generic textures
- Empty white space
- Flat vector stock icons
- Organic or hand-drawn imperfections

---

根据以下内容生成信息图：

# Claude Code Best Practice 知识地图

## SEC-01: 仓库概览

**数据**:
- 定位: "from vibe coding to agentic engineering — practice makes claude perfect"
- 性质: 纯 Markdown 知识库（无源代码）
- 维护者: Shayan（社区成员）
- 地位: GitHub Trending #1
- 规模: 6,556 行 Markdown + SVG/PNG

## SEC-02: 六大核心概念

| 概念 | 位置 | 说明 |
|------|------|------|
| Subagents | .claude/agents/ | YAML 前端的子代理定义 |
| Commands | .claude/commands/ | 斜杠命令工作流入口 |
| Skills | .claude/skills/ | 文件夹结构的技能定义 |
| Hooks | .claude/hooks/ | 27种钩子事件的跨平台通知 |
| MCP Servers | .mcp.json | Playwright, Context7, DeepWiki |
| Memory | CLAUDE.md + rules | 多层次指令系统 |

## SEC-03: 知识资产（6,556行）

- Best Practices: 8篇 / 1,923行（最大: settings 1,132行）
- Deep Reports: 12篇 / 2,790行（最大: Advanced Tool Use 420行）
- Tips: 9篇 / 1,339行 / 83条（来源: Boris Cherny, Thariq, 社区）
- 配置实现: 5代理 + 2命令 + 5技能 + 3 MCP

## SEC-04: 编排工作流

用户输入 /weather-orchestrator
→ ① Command 启动
→ ② Agent (weather-agent) 获取 Open-Meteo 温度
→ ③ Skill (weather-svg-creator) 生成 SVG 卡片

展示了两种技能模式：
- Agent Skills: 预加载到子代理上下文
- Invoked Skills: 通过 Skill 工具显式调用

## SEC-05: 生态地图

12个工作流框架对比:
- Superpowers (175k★): 完整 Skill 体系
- ECC (171k★): 最丰富命令/代理
- Spec Kit (92k★): 规格驱动
- gstack (88k★): 三层审查
- Get Shit Done (59k★): 完整项目周期

6大技能集合:
- anthropics/skills (127k★)
- mattpocock/skills (51k★)
- agent-skills (27k★)

## SEC-06: 质量评估

六大优势:
✓ 信息密度高 (6,500+ 行)
✓ 可操作性强 (概念+实践+配置)
✓ 来源权威 (Boris, Thariq, 社区)
✓ 结构清晰 (相对链接互引)
✓ 持续维护 (活跃 git 提交)
✓ 社区驱动

四大改进:
△ claude-settings.md 1,132行偏大
△ 无自动化测试验证
△ 缺乏搜索索引/术语表
△ 部分文档内容重叠

Text labels (in zh):
- Main Title: "Claude Code Best Practice 知识地图"
- Subtitle: "6大核心概念 · 4类知识资产 · 12个工作流框架"
- SEC-01: "仓库概览" → "6,556行 Markdown · GitHub Trending #1"
- SEC-02: "六大核心概念" → "Subagents · Commands · Skills · Hooks · MCP · Memory"
- SEC-03: "知识资产盘点" → "Best Practices 1,923行 · Reports 2,790行 · Tips 83条"
- SEC-04: "编排工作流" → "Command → Agent → Skill"
- SEC-05: "生态地图" → "12个工作流框架 · 6个技能集合"
- SEC-06: "质量评估" → "6大优势 · 4项改进"
