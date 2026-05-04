# 变更日志 — README 概念部分

跟踪 README 概念表格与官方 Claude Code 文档之间的漂移。

## 状态图例

| 状态 | 含义 |
|--------|---------|
| ✅ `完成（原因）` | 已执行操作并成功解决 |
| ❌ `无效（原因）` | 发现不正确、不适用或有意为之 |
| ✋ `搁置（原因）` | 操作推迟 — 等待外部依赖或用户决定 |

---

## [2026-03-02 11:14 AM PKT] Claude Code v2.1.63

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 损坏 | 修复权限 URL 从 `/iam` 到 `/permissions` | ✅ 完成（URL 已更新为 /permissions） |
| 2 | 高 | 缺少概念 | 在概念表格中添加代理团队行 | ✅ 完成（已添加行，位置为 ~\/\.claude\/teams\/） |
| 3 | 高 | 缺少概念 | 在概念表格中添加键绑定行 | ✅ 完成（已添加行，位置为 ~\/\.claude\/keybindings\.json） |
| 4 | 高 | 缺少概念 | 在概念表格中添加模型配置行 | ✅ 完成（已添加行，位置为 \.claude\/settings\.json） |
| 5 | 高 | 缺少概念 | 在概念表格中添加自动记忆行 | ✅ 完成（已添加行，位置为 ~\/\.claude\/projects\/<project>\/memory\/） |
| 6 | 高 | 锚点过时 | 修复规则 URL 锚点从 `#modular-rules-with-clauderules` 到 `#organize-rules-with-clauderules` | ✅ 完成（锚点已更新） |
| 7 | 中 | 缺少概念 | 在概念表格中添加检查点行 | ✅ 完成（已添加行，位置为基于 git 的自动位置） |
| 8 | 中 | 缺少概念 | 在概念表格中添加状态行行 | ✅ 完成（已添加行，位置为 ~\/\.claude\/settings\.json） |
| 9 | 中 | 缺少概念 | 在概念表格中添加远程控制行 | ✅ 完成（已添加行，位置为 CLI \/ claude\.ai） |
| 10 | 中 | 缺少概念 | 在概念表格中添加快速模式行 | ✅ 完成（已添加行，位置为 \.claude\/settings\.json） |
| 11 | 中 | 缺少概念 | 在概念表格中添加无头模式行 | ✅ 完成（已添加行，位置为 CLI 标志 -p） |
| 12 | 低 | 描述变更 | 更新记忆描述以提及自动记忆 | ✅ 完成（描述和位置已更新） |
| 13 | 低 | 位置变更 | 更新 MCP 服务器位置以包含 `.mcp.json` | ✅ 完成（位置已更新为包含 .mcp.json） |
| 14 | 低 | 缺少徽章 | 在 Hooks 行添加"已实现"徽章 | ✅ 完成（已添加"已实现"徽章，链接到 .claude/hooks/） |

---

## [2026-03-02 11:57 AM PKT] Claude Code v2.1.63

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 表格整合 | 将概念表格从 22 行整合为 10 行 — 将相关概念折叠为内联文档链接 | ✅ 完成（22 → 10 行） |
| 2 | 中 | 合并概念 | 将市场折叠到插件行中作为内联链接 | ✅ 完成（链接到 /discover-plugins） |
| 3 | 中 | 合并概念 | 将代理团队折叠到子代理行中作为内联链接 | ✅ 完成（链接到 /agent-teams） |
| 4 | 中 | 合并概念 | 将权限、模型配置、输出样式、沙箱、键绑定、状态行、快速模式折叠到设置行中作为内联链接 | ✅ 完成（7 个概念已折叠并附有文档链接） |
| 5 | 中 | 合并概念 | 将自动记忆和规则折叠到记忆行中作为内联链接 | ✅ 完成（链接到 /memory 和 /memory#organize-rules-with-clauderules） |
| 6 | 中 | 合并概念 | 将无头模式折叠到远程控制行中作为内联链接 | ✅ 完成（链接到 /headless） |
| 7 | 低 | 重新排序 | 按逻辑分组重新排列表格：构建块 → 扩展 → 配置 → 上下文 → 运行时 | ✅ 完成（按关注点分组，而非时间顺序） |

---

## [2026-03-07 08:40 AM PKT] Claude Code v2.1.71

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 损坏 | 修复 TIPS 中的 `context-management` → `interactive-mode`（第 112、115、135 行） | ✅ 完成（3 处已替换为 interactive-mode） |
| 2 | 高 | URL 损坏 | 修复 TIPS 中的 `model-configuration` → `model-config`（第 115、116、135 行） | ✅ 完成（3 处已替换为 model-config） |
| 3 | 高 | URL 损坏 | 修复 TIPS 中的 `usage-billing` → `costs`（第 115 行） | ✅ 完成（已替换为 costs） |
| 4 | 高 | URL 损坏 | 移除 STARTUPS 中的 `cowork` URL（第 167 行）— 页面不存在 | ✅ 完成（超链接已移除，保留纯文本） |
| 5 | 高 | 缺少概念 | 在概念表格和热点部分中添加定时任务行（`/loop`、cron 工具） | ✅ 完成（由用户添加到两个表格 + /loop 提示 + Boris 推文） |
| 6 | 中 | 位置变更 | 更新代理团队位置从 `.claude/agents/<name>.md` 到 `内置（环境变量）` | ✅ 完成（位置已更新为内置环境变量） |

---

## [2026-03-10 01:18 PM PKT] Claude Code v2.1.72

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 损坏 | 修复概念表格中的命令 URL 从 `/slash-commands` 到 `/skills`（第 24 行）— `/slash-commands` 提供技能页面内容；文档说"命令已合并到技能中" | ❌ 无效（URL 仍然有效；用户选择保持原样） |
| 2 | 高 | URL 损坏 | 修复 TIPS 部分的命令 URL 从 `/slash-commands` 到 `/skills`（第 108 行）— 相同的过时 URL | ❌ 无效（URL 仍然有效；用户选择保持原样） |
| 3 | 中 | 缺少内联链接 | 添加交互模式（`/interactive-mode`）作为 CLI 启动标志行的内联链接 — 涵盖 /compact、/clear、/context、/extra-usage | ✅ 完成（内联链接已添加到 CLI 启动标志描述中） |
| 4 | 中 | 缺少内联链接 | 添加成本（`/costs`）作为设置行的内联链接 — 涵盖 /usage、计费、按量付费 | ❌ 无效（用户选择跳过） |
| 5 | 低 | 缺少概念 | 考虑添加 IDE 集成行（VS Code、JetBrains、桌面应用、Web）或最佳实践中的内联链接 | ❌ 无效（用户选择跳过 — 平台展示面，而非配置概念） |
| 6 | 高 | 缺少概念 | 在热点表格中添加代码审查行 — 多代理 PR 分析（研究预览，团队版和企业版） | ✅ 完成（已作为首个热点条目添加，附有博客链接和最佳实践推文） |
| 7 | 中 | 新徽章 | 创建 `!/tags/beta.svg` 标签（黄色，38x20px）并添加到热点表格中的代码审查和代理团队 | ✅ 完成（beta.svg 已创建；已添加到代码审查和代理团队行） |
| 8 | 中 | 重新排序 | 按发布日期对热点表格排序（最新的在前）：代码审查 → 定时任务 → 语音模式 → 代理团队 → 远程控制 → Git 工作树 → Ralph Wiggum | ✅ 完成（语音模式和代理团队已交换以匹配时间顺序） |

---

## [2026-03-12 12:22 PM PKT] Claude Code v2.1.74

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 损坏 | 修复概念表格中的命令 URL 从 `/slash-commands` 到 `/skills`（第 24 行）— `/slash-commands` 重定向到 `/skills` 页面 | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 20+ 个 URL 返回有效页面） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 目标页面上的记忆锚点 `#organize-rules-with-clauderules` 已验证 | ✅ 完成（标题在 /memory 页面上存在） |
| 5 | 低 | 验证 | 所有概念描述已对照官方文档检查 | ✅ 完成（未检测到描述漂移） |

---

## [2026-03-15 12:48 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 中 | 缺少徽章 | 远程控制（热点）有零个徽章 — 唯一没有 BP 或 Impl 徽章的热点项 | ✅ 完成（BP 徽章已添加，链接到官方文档页面） |
| 3 | 低 | 命名 | README 中的"Sub-Agents"与官方文档中的"subagents"（一个词）— 外观不一致 | ✅ 完成（已在概念表格中重命名为"Subagents"） |
| 4 | 低 | 验证 | 所有 27 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有 13 个概念 + 9 个热点行的描述准确） |

---

## [2026-03-17 12:46 PM PKT] Claude Code v2.1.77

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 高 | 描述变更 | Hooks 描述说"确定性脚本"，但 hooks 现在包括 4 种类型：command、HTTP、prompt 和 agent — 只有 command hooks 是确定性的 | ✅ 完成（已在概念表格中更新为"用户定义的处理程序（脚本、HTTP、提示、代理）"） |
| 3 | 中 | 缺少概念 | 桌面应用在 `/desktop` 有专用文档页面 — 不在概念或热点表格中 | ❌ 无效（用户选择跳过 — 桌面是平台展示面，不是配置概念） |
| 4 | 中 | URL 变更 | Hooks 文档现已分为指南（`/hooks-guide`）和参考（`/hooks`）— 概念仅链接到参考 | ✅ 完成（指南链接已作为内联链接添加到 Hooks 行描述中） |
| 5 | 低 | 验证 | 所有 28 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 6 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20 个徽章目标在文件系统中存在） |
| 7 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 所有概念描述已对照官方文档检查 | ✅ 完成（Hooks 描述漂移已检测到 — 参见 #2） |

---

## [2026-03-18 11:43 PM PKT] Claude Code v2.1.78

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 高 | URL+名称变更 | 热点表格中的语音模式链接到推文而非官方文档 `/voice-dictation`；官方名称是"语音听写" | ✅ 完成（已重命名为"语音听写"，链接到 /voice-dictation，描述已更新；BP 徽章保持链接到推文；也在 STARTUPS 表格中更新） |
| 3 | 低 | 验证 | 所有 29 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 4 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 5 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-19 11:59 AM PKT] Claude Code v2.1.79

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 30 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 5 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-20 08:38 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺少概念 | 在热点表格中添加渠道行 — 从 Telegram/Discord/webhooks 推送事件到正在运行的会话（研究预览，v2.1.80） | ✅ 完成（已作为首个热点条目添加，附有 beta 徽章和参考链接） |
| 2 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 3 | 中 | 缺少深层链接 | Git 工作树 URL 应锚定到 `#run-parallel-claude-code-sessions-with-git-worktrees` | ✅ 完成（锚点已添加到热点表格中的 Git 工作树 URL） |
| 4 | 低 | 缺少内联链接 | 插件行可以添加 `[Marketplaces](https://code.claude.com/docs/en/plugin-marketplaces)` 子链接 | ✅ 完成（创建市场内联链接已添加到插件行） |
| 5 | 低 | 验证 | 所有 31 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 6 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 7 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-21 09:12 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 32 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 5 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-23 09:53 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 33 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 5 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-25 08:12 PM PKT] Claude Code v2.1.83

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 中 | URL 变更 | Simplify & Batch 主要链接指向推文而非官方文档 `/skills#bundled-skills` — 现已官方提供捆绑技能 | ✅ 完成（主要链接已更新为 /skills#bundled-skills；BP 徽章保持链接到 Boris 的推文） |
| 3 | 低 | 验证 | 所有 34 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 4 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 5 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |
| 8 | 高 | 缺少概念 | 在热点表格中添加自动模式行 — 后台安全分类器替代权限提示（研究预览，团队版/企业版） | ✅ 完成（已作为首个热点条目添加，附有 beta 徽章、链接到 @claudeai 推文的 BP 徽章和博客链接） |

---

## [2026-03-26 01:05 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 中 | 缺少概念 | 在热点表格中添加 Slack 集成 — 在 Slack 中 @Claude 将编码任务路由到 Claude Code web 会话 | ✅ 完成（已添加行，位置为 @Claude，附有 web 会话描述，位于 Channels 之后） |
| 3 | 中 | 缺少概念 | 在热点表格中添加 GitHub Actions / CI-CD — 在 CI/CD 管道中自动化 PR 审查、问题分类和代码生成 | ✅ 完成（已添加行，位置为 .github/workflows/，附有 GitLab CI/CD 内联链接，位于代码审查之后） |
| 4 | 低 | 验证 | 所有 35 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 10 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-27 06:37 PM PKT] Claude Code v2.1.85

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 中 | 缺少概念 | 在热点表格中添加 Chrome 集成 — 通过 Claude in Chrome 扩展实现浏览器自动化（beta，专用文档在 `/chrome`） | ✅ 完成（已添加行，位置为 --chrome，附有 beta 徽章，位于 GitHub Actions 之后） |
| 3 | 低 | 验证 | 所有 36 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 4 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 5 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-03-28 06:04 PM PKT] Claude Code v2.1.86

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 中 | 缺少徽章 | 热点表格中的 Chrome 行没有 BP 徽章 — 报告存在于 `reports/claude-in-chrome-v-chrome-devtools-mcp.md` | ✅ 完成（BP 徽章已添加，链接到 reports/claude-in-chrome-v-chrome-devtools-mcp.md） |
| 3 | 低 | 描述变更 | 插件描述缺少 LSP 服务器 — 官方文档列出 `.lsp.json` 作为插件组件 | ✅ 完成（已将"和 LSP 服务器"添加到插件描述中） |
| 4 | 低 | 验证 | 所有 37 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 `.claude/rules/` 存在） |
| 7 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 10 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（除插件 LSP 备注外所有描述准确 — 参见 #3） |

---

## [2026-04-01 12:33 PM PKT] Claude Code v2.1.89

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺少概念 | 在热点表格中添加计算机使用行 — 通过内置 MCP 服务器在 macOS 上进行屏幕控制（研究预览，v2.1.85+） | ✅ 完成（已添加行，附有 beta 徽章和桌面内联链接，位于全屏渲染之后） |
| 2 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 3 | 中 | 缺少概念 | 在热点表格中添加全屏渲染行 — 支持鼠标的无闪烁 alt-screen 渲染（研究预览，v2.1.88+） | ✅ 完成（已作为首个热点条目添加，位置为 CLAUDE_CODE_NO_FLICKER=1） |
| 4 | 低 | 验证 | 所有 38 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 10 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-02 09:17 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 提供技能页面 — 文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 39 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 5 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-03 08:35 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（llms.txt）中 — 重定向到 `/skills` 页面；文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 40 个外部文档 URL 已对照 llms.txt 站点地图（80 页）验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件（已检查 17 个本地目标） | ✅ 完成（所有徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 5 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-04 10:46 PM PKT] Claude Code v2.1.92

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺少概念 | 在热点表格中添加 Ultraplan 行 — 基于云的计划起草，支持浏览器审查、内联评论和灵活执行（`/ultraplan`） | ✅ 完成（已添加行，附有 beta 徽章和 /ultraplan 位置，位于 Power-ups 之后） |
| 2 | 高 | 缺少概念 | 在热点表格中添加 Claude Code Web 行 — 在 claude.ai/code 上使用云基础设施运行任务，支持 PR 自动修复和并行会话 | ✅ 完成（已添加行，附有 beta 徽章、claude.ai/code 位置和 Web 定时任务内联链接，位于 Ultraplan 之后） |
| 3 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图中 — 重定向到 `/skills` 页面；文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 4 | 中 | 缺少概念 | 在热点表格中添加桌面应用行 — 具有可视化差异、Dispatch、计算机使用和并行会话的独立应用 | ❌ 无效（自 2026-03-17 起重复出现；用户认为它是平台展示面，而非配置概念） |

---

## [2026-04-08 09:37 PM PKT] Claude Code v2.1.96

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图中 — 重定向到 `/skills` 页面；文档说"命令已合并到技能中" | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 2 | 中 | 名称变更 | 热点表格中的"无闪烁模式" — 官方文档页面标题是"全屏渲染"；考虑重命名或添加副标题 | ❌ 无效（用户选择保留"无闪烁模式"，遵循 Boris 的推文命名约定；环境变量为 `CLAUDE_CODE_NO_FLICKER`） |
| 3 | 中 | 缺少概念 | 在热点表格中添加桌面应用行 — 具有可视化差异、Dispatch、计算机使用和并行会话的独立应用 | ❌ 无效（自 2026-03-17 起重复出现；用户认为它是平台展示面，而非配置概念） |
| 4 | 低 | 验证 | 所有 41 个外部文档 URL 已验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件 | ✅ 完成（所有 20+ 个徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 7 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 10 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-09 11:37 PM PKT] Claude Code v2.1.97

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺少概念 | 在热点表格中添加 Agent SDK 行 — 使用 Python/TypeScript SDK 构建生产级 AI 代理（29 个文档页面，`/en/agent-sdk/overview`） | ✅ 完成（已添加行，附有快速入门和示例内联链接，位于 Claude Code Web 之后） |
| 2 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图中 — 重定向到 `/skills`；规范命令参考现为 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 3 | 中 | 缺少内联链接 | 在 CLI 启动标志行中添加环境变量（`/env-vars`）内联链接 — 新的专用文档页面 | ✅ 完成（环境变量内联链接已添加在交互模式之后） |
| 4 | 低 | 验证 | 所有 42 个外部文档 URL 已对照 llms.txt 站点地图（110 页）验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件（已检查 20+ 个徽章目标） | ✅ 完成（所有徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 7 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 10 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-11 06:13 PM PKT] Claude Code v2.1.101

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（110 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 43 个外部文档 URL 已对照 llms.txt 站点地图（110 页）验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件（已检查 20+ 个徽章目标） | ✅ 完成（所有徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 5 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-13 08:07 PM PKT] Claude Code v2.1.101

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（110 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 2 | 低 | 验证 | 所有 44 个外部文档 URL 已对照 llms.txt 站点地图（110 页）验证 — 未发现链接损坏 | ✅ 完成（所有 URL 返回有效页面，包括 /slash-commands 重定向） |
| 3 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件（已检查 20+ 个徽章目标） | ✅ 完成（所有徽章目标在文件系统中存在） |
| 4 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 5 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 6 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 7 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-14 11:17 PM PKT] Claude Code v2.1.107

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺少概念 | 在热点表格中添加 Routines 行 — 在 Anthropic 基础设施上的云端自动化，支持调度、API 和 GitHub 事件触发（`/en/routines`） | ✅ 完成（已添加行，附有 beta 徽章和桌面任务内联链接，位于定时任务之后） |
| 2 | 高 | URL 过时 | 更新 Claude Code Web 行（第 45 行）中的 `web-scheduled-tasks` 内联链接为 `/en/routines` — URL 不在站点地图中，重定向到 Routines 页面 | ✅ 完成（内联链接文本已改为"Routines"，URL 已更新为 /routines） |
| 3 | 高 | URL 过时 | 更新定时任务行（第 55 行）中的 `web-scheduled-tasks` 内联链接为 `/en/routines` — 相同的过时 URL | ✅ 完成（URL 已更新为 /routines） |
| 4 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（119 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 5 | 中 | 描述变更 | 更新定时任务描述从"最多 3 天"改为"最多 7 天" — 文档现在指定重复任务七天后过期 | ✅ 完成（描述已更新为"最多 7 天"） |
| 6 | 中 | 缺少概念 | 在热点表格中添加 Devcontainers 行 — 具有安全隔离和防火墙规则的预配置开发容器（`/en/devcontainer`） | ✅ 完成（已添加行，位置为 .devcontainer/，位于 Routines 之后） |

---

## [2026-04-16 08:20 PM PKT] Claude Code v2.1.110

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 修复 TIPS 中（第 223 行）的 `web-scheduled-tasks` URL 为 `/en/routines` — URL 不在站点地图中；相同的过时 URL 已于 2026-04-14 在热点表格中修复，但 TIPS 实例被遗漏 | ✅ 完成（URL 已更新为 /routines） |
| 2 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（111 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户选择保持原样） |
| 3 | 中 | 描述变更 | 将 TIPS 中（第 223 行）的"最多 3 天"更新为"最多 7 天" — 相同的描述已于 2026-04-14 在热点表格中更新，但 TIPS 实例被遗漏 | ✅ 完成（描述已更新为"最多 7 天"） |
| 4 | 低 | 验证 | 所有 45 个外部文档 URL 已对照 llms.txt 站点地图（111 页）验证 — 发现 1 个链接损坏（参见 #1） | ✅ 完成（已标记 web-scheduled-tasks） |
| 5 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件（已检查 20+ 个徽章目标） | ✅ 完成（所有徽章目标在文件系统中存在） |
| 6 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 7 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 8 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 9 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 10 | 低 | 验证 | 所有概念描述已对照官方文档检查 — 未检测到漂移 | ✅ 完成（所有描述准确） |

---

## [2026-04-18 07:53 PM PKT] Claude Code v2.1.113

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 描述变更 | 自动模式行（第 48 行）仍然引用 `claude --enable-auto-mode` — 该标志已在 v2.1.111 中移除；自动模式现在通过 `--permission-mode auto` 或 Shift+Tab 循环启动（Max 订阅用户默认使用 Opus 4.7） | ✅ 完成（位置更新为 `--permission-mode auto`、`Shift+Tab`；描述说明了标志移除和 Max+Opus-4.7 默认） |
| 2 | 高 | 缺少概念 | 在热点表格中添加 Ultrareview 行 — 基于云的多代理代码审查（`/ultrareview`，v2.1.86+，专用文档在 `/en/ultrareview`）；Pro/Max 免费 3 次运行 | ✅ 完成（已添加行，附有 beta 徽章、/ultrareview 位置、任务跟踪内联链接，位于 Routines 之后） |
| 3 | 高 | 缺少概念 | 添加任务行 — `/tasks` 命令用于跟踪后台工作（在 Ultrareview 页面上引用）；根据 `reports/claude-global-vs-project-settings.md` 替换 TodoWrite | ✅ 完成（已添加行，位置为 /tasks，BP 徽章链接到 global-vs-project-settings 报告，位于定时任务之后） |
| 4 | 中 | 描述变更 | 无闪烁模式行（第 47 行） — 官方文档现在以 `/tui fullscreen` 命令为主导（v2.1.110）；环境变量是 v2.1.110 之前的传统路径，根据 /fullscreen 页面 | ✅ 完成（位置更新为 `/tui fullscreen`、`CLAUDE_CODE_NO_FLICKER=1`；描述说明 /tui 是规范用法，环境变量是传统用法） |
| 5 | 中 | 命令名称过时 | TIPS 第 249 行引用 `/fewer-permission-prompts` — 官方技能名称是 `/less-permission-prompts`，根据 v2.1.111 变更日志（本地技能文件夹是 `fewer-permission-prompts`，但用户可见的命令应匹配官方名称） | ✅ 完成（TIPS 第 249 行已更新为 /less-permission-prompts） |
| 6 | 低 | 描述变更 | 定时任务行（第 60 行） — 第 15 周添加了 Monitor 工具 + 自定节奏 `/loop`（LLM 自己选择间隔）；描述未提及此内容 | ✅ 完成（描述已追加自定节奏/Monitor 工具说明） |
| 7 | 低 | 描述变更 | Git 工作树行（第 63 行） — v2.1.105/106 添加了 `EnterWorktree`/`ExitWorktree` 工具和 `isolation: "worktree"` 子代理 frontmatter；描述未提及这些 | ✅ 完成（位置已更新为包含 EnterWorktree/ExitWorktree 和 isolation frontmatter；描述说明了 v2.1.106+ 子代理工作树支持） |
| 8 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（119 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户已在 17+ 次运行中选择保持原样） |
| 9 | 低 | 验证 | 所有 45+ 个外部文档 URL 已对照 llms.txt 站点地图（119 页）验证 — 除重复出现的 `/slash-commands` 重定向外，未发现新的链接损坏 | ✅ 完成（所有标记的 URL 返回有效页面） |
| 10 | 低 | 验证 | 所有本地徽章文件路径已验证 — 无缺失文件（已检查 20+ 个徽章目标） | ✅ 完成（所有徽章目标在文件系统中存在） |
| 11 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 /memory 页面上确认 | ✅ 完成（部分标题 "Organize rules with `.claude/rules/`" 存在） |
| 12 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 /common-workflows 页面上确认 | ✅ 完成（部分标题存在） |
| 13 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 /permission-modes 页面上确认 | ✅ 完成（部分标题存在） |
| 14 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 /skills 页面上确认 | ✅ 完成（部分标题存在） |
| 15 | 低 | 验证 | 全屏页面确认 `/tui fullscreen` 是规范命令，`tui` 是设置字段（v2.1.110） | ✅ 完成（页面已获取并引用） |
| 16 | 低 | 验证 | 权限模式页面确认 `--enable-auto-mode` 标志不再被文档记录；自动模式现在需要 Max 计划 + Opus 4.7 | ✅ 完成（页面已获取；标志不存在于文档中） |
| 17 | 低 | 验证 | Ultrareview 页面存在于 `/en/ultrareview`（v2.1.86+），确认 `/ultrareview` 和 `/tasks` 命令 | ✅ 完成（页面已获取，内容已捕获） |

---

## [2026-04-24 12:32 AM PKT] Claude Code v2.1.118

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 描述变更 | Hooks 行（第 28 行）列出 4 种处理程序类型（"脚本、HTTP、提示、代理"）— 官方 `/en/hooks` 页面现在记录了 5 种类型，新增了 `mcp_tool`（v2.1.118 变更日志："Hooks 可以通过 `type: "mcp_tool"` 直接调用 MCP 工具"） | ✅ 完成（描述已更新为"脚本、HTTP、MCP 工具、提示、代理"） |
| 2 | 中 | 空描述 | 工作流行（第 27 行）描述单元格为空（仅有编排工作流程徽章）— 官方 `/en/common-workflows` 页面涵盖了探索、修复、重构、测试的分步指南 | ✅ 完成（描述已填充官方文档来源的文本："用于探索代码库、修复错误、重构和测试的分步指南 — 多步骤任务的编排模式"） |
| 3 | 低 | 描述变更 | 考虑在 CLI 启动标志行中内联提及 `/usage`（v2.1.118 合并了 `/cost`+`/stats`）— 新的斜杠命令替代了两个传统命令 | ✅ 完成（内联说明"`/usage`（在 v2.1.118 中合并了 `/cost`+`/stats`）"已追加在环境变量之后） |
| 4 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（117 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户已在 18+ 次运行中选择保持原样） |
| 5 | 低 | 验证 | Hooks 页面 `/en/hooks` 已获取 — 确认 5 种处理程序类型，包括 `mcp_tool`（v2.1.118） | ✅ 完成（实时获取记录了 5 类型模式） |
| 6 | 低 | 验证 | Ultrareview 页面 `/en/ultrareview#track-a-running-review` 锚点已获取并确认 | ✅ 完成（部分存在，描述了 `/tasks` 集成） |
| 7 | 低 | 验证 | 检查点页面 `/en/checkpointing` 已获取 — `/undo` 别名（v2.1.108）未在文档中展示，仅在变更日志中；无需更新概念 | ✅ 完成（文档页面内容与现有描述匹配） |
| 8 | 低 | 验证 | 所有本地徽章文件路径 — 自 2026-04-18 的 v2.1.113 运行以来无变化 | ✅ 完成（自上次运行以来保持稳定） |
| 9 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` — 本次运行未重新检查；自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 10 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 11 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 12 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 13 | 低 | 验证 | claude-code-guide 代理交叉检查 — 与专用代理无矛盾；提供了 /recap（v2.1.108）、/usage（v2.1.118）、MCP-tool hooks（v2.1.118）作为佐证 | ✅ 完成（两个代理一致） |

---

## [2026-04-26 01:10 PM PKT] Claude Code v2.1.119

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（139 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户已在 19+ 次运行中选择保持原样） |
| 2 | 高 | 目标 URL 错误 | 任务行（第 62 行）主要 URL 指向 `/ultrareview#track-a-running-review` — 锚点有效，但目标是 ultrareview 跟踪部分，而非更广泛的任务系统；规范主页是本地报告 `reports/claude-global-vs-project-settings.md#tasks-system` | ✅ 完成（主要 URL 已更新为 `reports/claude-global-vs-project-settings.md#tasks-system`；ultrareview 跟踪锚点保留为描述末尾的内联链接"Ultrareview 跟踪"） |
| 3 | 中 | Beta 徽章时效性 | Routines / 无闪烁模式 / 计算机使用 / 代码审查在 README 中有 `![beta]`，但它们的文档页面不再将其标记为 beta — 重新评估并在适当时降级 | ❌ 无效（验证获取了全部 4 个文档页面 — Routines："处于研究预览阶段"；全屏："研究预览"；计算机使用："在 macOS 上为研究预览"；代码审查："处于研究预览阶段" — README beta 徽章是准确的；代理对正文内容的 0.6 置信度读取被 `<Note>` 横幅文本推翻） |
| 4 | 中 | 描述消歧 | 定时任务行（第 61 行）描述混淆了 `/loop`（本地，会话范围，7 天过期）和 `/schedule`（Anthropic 基础设施上的云端 Routines）— 官方 `/en/scheduled-tasks` 页面现在正式区分了云/桌面/循环三种形式 | ✅ 完成（描述现在明确命名了"三种形式"，分别说明 `/loop` 本地、`/schedule` 云端 Routines 和桌面定时任务） |
| 5 | 低 | 缺少概念（可选） | 快速模式当前只是设置内部的一个侧链接（第 31 行）— 它有自己专用的 `/en/fast-mode` 页面，带有 `↯` 指示器和 `/fast` 切换（v2.1.36+）；可以作为热点行 | ✅ 完成（热点行已插入在 Power-ups 和计算机使用之间，附有 beta 徽章；移除了设置中冗余的快速模式侧链接以防止重复） |
| 6 | 低 | 缺少内联链接 | 记忆行可以展示 `reports/claude-agent-memory.md` 作为内联链接 — 引用了自动记忆，但本地深度分析未从概念链接 | ✅ 完成（"自动记忆深度分析"内联链接已添加在记忆行的自动记忆文档和规则之间） |
| 7 | 低 | 缺少内联链接 | 技能行可以展示 `reports/claude-skills-for-larger-mono-repos.md` 作为内联链接 — 存在于本地但仅从 TIPS 引用 | ✅ 完成（"大型单仓库技能"内联链接已追加在技能行的官方技能之后） |
| 8 | 低 | 可选概念 | Vim 可视模式（v2.1.118）、主题定制（`~/.claude/themes/`，v2.1.118）和 PowerShell 工具（v2.1.111）可以作为设置侧链接 — claude-code-guide 交叉检查发现的次要概念 | ❌ 无效（Vim 模式已被现有的键绑定侧链接覆盖；主题没有区别于设置的专用文档页面；PowerShell 工具没有专用文档页面 — 没有具体的子链接目标值得添加） |
| 9 | 低 | 验证 | 所有 35+ 个外部概念文档 URL 已对照 llms.txt 站点地图（139 页）验证 — 仅标记了重复出现的 `/slash-commands` 重定向；所有其他 URL 解析到预期页面 | ✅ 完成（未发现新的损坏 URL） |
| 10 | 低 | 验证 | 所有本地徽章文件路径已验证 — 所有 20+ 个 `best-practice/`、`implementation/` 和 `reports/` 目标在文件系统中存在 | ✅ 完成（无缺失的本地文件） |
| 11 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` 在 `/en/memory` 页面上确认 | ✅ 完成（自 v2.1.113 以来保持稳定） |
| 12 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` 在 `/en/common-workflows` 页面上确认 | ✅ 完成（稳定） |
| 13 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` 在 `/en/permission-modes` 页面上确认 | ✅ 完成（稳定） |
| 14 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` 在 `/en/skills` 页面上确认 | ✅ 完成（稳定） |
| 15 | 低 | 验证 | Ultrareview 锚点 `#track-a-running-review` 在 `/en/ultrareview` 页面上确认 | ✅ 完成（自 v2.1.118 以来保持稳定） |
| 16 | 低 | 验证 | claude-code-guide 交叉检查 — 佐证了专用代理关于 Vim 模式（v2.1.118）、主题（v2.1.118）、Effort xhigh（v2.1.111+ Opus 4.7）、工作树（v2.1.105+）的发现；无矛盾 | ✅ 完成（两个代理一致） |
| 17 | 低 | 验证检查清单更新 | 在 verification-checklist.md 中添加了新规则（#7）"Beta 徽章时效性" — 涵盖根据上游文档页面生命周期重新评估 beta 徽章 | ✅ 完成（规则已添加） |

---

## [2026-04-29 12:53 AM PKT] Claude Code v2.1.121

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图（139+ 页）中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户已在 20+ 次运行中选择保持原样） |
| 2 | 中 | 描述变更 | Ultrareview 行（第 44 行）未提及 v2.1.120 中引入的 `claude ultrareview [target]` 非交互式子命令 — 文档确认了 `--json` 和 `--timeout` 标志用于 CI 使用 | ✅ 完成（位置更新为包含 `claude ultrareview [target]`；描述追加了非交互式子命令及 `--json` 和 `--timeout` 标志说明，v2.1.120+） |
| 3 | 中 | 描述变更 | MCP 服务器行（第 29 行）未提及 v2.1.121 中添加的 `alwaysLoad` 设置 — 绕过工具搜索延迟，使服务器的工具始终加载到上下文中 | ✅ 完成（描述追加了 `alwaysLoad` 说明，解释工具搜索延迟绕过，v2.1.121+） |
| 4 | 中 | 描述变更 | Hooks 行（第 28 行）未提及 v2.1.121 中添加的 `updatedToolOutput` 能力 — PostToolUse hooks 现在可以通过 `hookSpecificOutput.updatedToolOutput` 替换工具输出 | ✅ 完成（描述追加了 `hookSpecificOutput.updatedToolOutput` 说明，用于 PostToolUse 输出替换，v2.1.121+） |
| 5 | 低 | 描述变更 | 子代理行（第 24 行）未提及分支子代理现在可通过 `CLAUDE_CODE_FORK_SUBAGENT=1` 在外部构建中使用（v2.1.117）— 以前仅限内部 | ✅ 完成（描述追加了 `CLAUDE_CODE_FORK_SUBAGENT=1` 说明，用于外部构建，v2.1.117+） |
| 6 | 低 | 缺少内联链接 | 设置行（第 31 行）的内联链接涵盖权限/模型配置/输出样式/沙箱/键绑定，但不包括自动模式配置（`/auto-mode-config`）— 作为独立页面存在 | ✅ 完成（自动模式配置内联链接已追加在键绑定之后） |
| 7 | 低 | 验证 | 所有 35+ 个外部概念文档 URL 已抽查验证 — 子代理、技能、MCP、Ultrareview 页面已确认；仅标记了重复出现的 `/slash-commands` 重定向 | ✅ 完成（未发现新的损坏 URL） |
| 8 | 低 | 验证 | 所有本地徽章文件路径已验证 — 所有 22 个 `best-practice/`、`implementation/`、`reports/`、`.claude/`、`CLAUDE.md` 目标在文件系统中存在 | ✅ 完成（无缺失的本地文件） |
| 9 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` — 自 v2.1.113 以来保持稳定（本次运行未重新获取） | ✅ 完成（稳定） |
| 10 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 11 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 12 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 13 | 低 | 验证 | Ultrareview 锚点 `#track-a-running-review` 在 `/en/ultrareview` 页面上确认 — 部分存在并描述了 `/tasks` 集成 | ✅ 完成（自 v2.1.118 以来保持稳定） |
| 14 | 低 | 验证 | claude-code-guide 交叉检查 — 佐证了专用代理关于 v2.1.117–v2.1.121 变更的发现（分支子代理外部化、alwaysLoad、updatedToolOutput、claude ultrareview 子命令）；还发现了 Bedrock/Vertex/Foundry、桌面、IDE 集成作为长期缺失的概念 | ✅ 完成（两个代理一致；所有"缺失的平台展示面"已根据重复出现的用户决定标记为无效） |

---

## [2026-05-01 03:34 PM PKT] Claude Code v2.1.126

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 版本过时 | README 徽章固定在 v2.1.121（4 月 29 日）— 最新为 v2.1.126（5 月 1 日）；落后 5 个版本 | ✅ 完成（徽章已更新为 v2.1.126 2026 年 5 月 1 日 3:34 PM PKT） |
| 2 | 中 | 新概念（可选） | v2.1.126 引入了 `claude project purge [path]` 子命令，带有 `--dry-run`/`--all` 标志 — 目前不在 CLI 启动标志行中；可以作为内联说明 | ✋ 搁置（推迟 — 单一版本较新的子命令；如果用户要求刷新 CLI 启动标志则重新审视） |
| 3 | 中 | 新概念（可选） | v2.1.126 添加了网关驱动的模型选择器 — 当网关与 Anthropic 兼容时，`/model` 从 `ANTHROPIC_BASE_URL` 的 `/v1/models` 端点列出模型 | ✋ 搁置（推迟 — 小众的 LLM 网关功能；仅与自托管网关用户相关；故意未在概念中展示） |
| 4 | 低 | 描述变更（可选） | v2.1.122 将 `--from-pr` 扩展为接受 GitLab MR + Bitbucket PR + GitHub Enterprise PR URL（最初仅 GitHub）— CLI 启动标志行未展示此内容 | ✋ 搁置（推迟 — `--from-pr` 目前未作为内联链接展示；需要添加新的子链接） |
| 5 | 高 | URL 过时 | 命令 URL `/slash-commands` 不在官方站点地图中 — 重定向到 `/skills`；规范命令参考是 `/en/commands` | ❌ 无效（自 2026-03-10 起重复出现；URL 通过重定向仍然有效；用户已在 21+ 次运行中选择保持原样） |
| 6 | 中 | 缺少概念（重复出现） | 专用代理再次标记输出样式、权限、沙箱、无头模式、桌面应用、IDE 集成作为缺少的独立行 | ❌ 无效（自 2026-03-10/2026-03-17/2026-04-08/2026-04-09 起重复出现；用户认为所有六个平台展示面或作为设置的子链接覆盖 — 不是独立概念） |
| 7 | 中 | 缺少概念（重复出现） | 专用代理标记自动记忆需要独立于记忆的单独行 | ❌ 无效（重复出现 — 当前的记忆行已经通过内联链接展示了 `/en/memory#auto-memory` 和 `reports/claude-agent-memory.md`；用户选择的跨领域功能模式） |
| 8 | 低 | 发现过时 | 专用代理标记任务行的主要 URL 需要 `/en/agent-sdk/todo-tracking` 交叉引用 | ❌ 无效（已于 2026-04-26 解决 — 用户明确将任务主要 URL 移至 `reports/claude-global-vs-project-settings.md#tasks-system`，并保留 ultrareview 跟踪作为内联链接；代理的分析已过时） |
| 9 | 低 | 验证 | 所有 23 个本地徽章文件路径已验证 — `best-practice/`、`implementation/`、`reports/`、`.claude/`、`.mcp.json`、`CLAUDE.md` 全部存在 | ✅ 完成（无缺失的本地文件） |
| 10 | 低 | 验证 | 抽查验证了外部概念 URL（`/en/cli-reference`、`/en/agent-teams`、`/en/changelog`、`/en/mcp`）— 全部返回有效页面 | ✅ 完成（未发现新的损坏 URL） |
| 11 | 低 | 验证 | Beta 徽章时效性（规则 #7）— 获取了 `/en/agent-teams` 并确认了 `<Warning>` 横幅："代理团队是实验性的，默认禁用" — README beta 徽章准确 | ✅ 完成（无需降级） |
| 12 | 低 | 验证 | 记忆锚点 `#organize-rules-with-clauderules` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 13 | 低 | 验证 | Git 工作树锚点 `#run-parallel-claude-code-sessions-with-git-worktrees` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 14 | 低 | 验证 | 自动模式锚点 `#eliminate-prompts-with-auto-mode` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 15 | 低 | 验证 | 捆绑技能锚点 `#bundled-skills` — 自 v2.1.113 以来保持稳定 | ✅ 完成（稳定） |
| 16 | 低 | 验证 | Ultrareview 锚点 `#track-a-running-review` — 自 v2.1.118 以来保持稳定 | ✅ 完成（稳定） |
| 17 | 低 | 验证 | claude-code-guide 交叉检查 — 独立研究展示了相同的 v2.1.122–126 变更（`claude project purge`、网关模型选择器、`--from-pr` 扩展）；也再次展示了长期存在的平台展示面概念（桌面、IDE 集成、Bedrock/Vertex/Foundry），这些根据用户策略是重复出现的无效项；无矛盾 | ✅ 完成（两个代理一致） |
