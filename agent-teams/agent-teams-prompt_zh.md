创建一个代理团队来构建一个时间编排工作流，以可视化 SVG 卡片的形式显示迪拜当前时间。该工作流遵循 Command → Agent → Skill 架构模式：

- Command 编排流程并处理用户交互
- Agent 使用预加载的技能获取迪拜的实时当前时间
- Skill 根据获取的数据创建可视化 SVG 时间卡片

**重要提示**：所有文件都必须在 `agent-teams/.claude/` 内创建 — 而不是在仓库根目录的 `.claude/` 目录下。这使得代理团队的输出保持独立，并可通过 `cd agent-teams && claude` 运行。
请勿引用或复制现有的天气工作流 — 从头构建所有内容。

分配以下团队成员：

1. **Command 架构师** — 设计并实现位于 `agent-teams/.claude/commands/time-orchestrator.md` 的 `/time-orchestrator` 命令。该命令应：
   - 通过 Agent 工具（而非 bash）调用 time-agent 来获取阿联酋迪拜的当前时间（Asia/Dubai 时区，UTC+4）
   - 通过 Skill 工具调用 time-svg-creator 技能，根据获取的时间数据渲染 SVG 卡片
   - 在前置元数据中使用 model: haiku
   - 包含关键需求：顺序流程、正确的工具使用（Agent 工具用于代理，Skill 工具用于技能）以及输出摘要
   - 通过共享任务列表与其他团队成员协调，就组件之间传递的数据契约（{time, timezone, formatted}）达成一致

2. **Agent 工程师** — 设计并实现位于 `agent-teams/.claude/agents/time-agent.md` 的 `time-agent` 及其预加载的 `time-fetcher` 技能（位于 `agent-teams/.claude/skills/time-fetcher/SKILL.md`）。该代理应：
   - 使用 Bash 命令 `TZ='Asia/Dubai' date '+%Y-%m-%d %H:%M:%S %Z'` 获取迪拜的当前时间（Asia/Dubai，UTC+4）
   - 将时间值、时区名称和格式化字符串返回给 Command
   - 使用前置元数据：tools (Bash)、model: haiku、color: blue、maxTurns: 3
   - 通过 `skills:` 字段预加载 time-fetcher 技能
   - time-fetcher 技能（`agent-teams/.claude/skills/time-fetcher/SKILL.md`）应包含迪拜时间的 bash 命令、预期的输出格式，并设置 user-invocable: false，因为它是仅限代理的领域知识
   - 将商定的数据契约发布到共享任务列表，以便 Command 架构师和 Skill 设计师能够对齐接口

3. **Skill 设计师** — 设计并实现位于 `agent-teams/.claude/skills/time-svg-creator/SKILL.md` 的 `time-svg-creator` 技能，附带支持文件 `reference.md`（SVG 模板 + 输出模板）和 `examples.md`（示例输入/输出对）。该技能应：
   - 从调用上下文中接收时间值、时区和格式化字符串
   - 创建一个自包含的迪拜 SVG 时间卡片，显示当前时间
   - 将 SVG 写入 `agent-teams/output/dubai-time.svg`
   - 将 Markdown 摘要写入 `agent-teams/output/output.md`
   - 使用提供的精确时间 — 切勿重新获取
   - 将模板保存在 reference.md 中（带占位符的 SVG 标记、Markdown 输出模板），将示例对保存在 examples.md 中
   - 同时创建 `agent-teams/output/` 目录用于输出文件

所有三位团队成员都应在共享任务列表中创建任务，以协调数据契约：代理返回 {time, timezone, formatted}，Command 通过上下文传递它，Skill 消费它。
由于各组件是独立的，请同时启动所有三位成员 — 他们只需要在数据接口上达成一致，无需等待彼此的实现。
