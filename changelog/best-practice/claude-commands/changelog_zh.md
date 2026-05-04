# 命令报告 — 更新日志历史

## 状态图例

| 状态 | 含义 |
|--------|---------|
| ✅ `COMPLETE（原因）` | 已采取行动并成功解决 |
| ❌ `INVALID（原因）` | 发现不正确、不适用或有意为之 |
| ✋ `ON HOLD（原因）` | 操作已推迟 — 等待外部依赖或用户决定 |

---

## [2026-03-13 04:23 PM PKT] Claude Code v2.1.74

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新字段 | 在 frontmatter 表中添加 `name` — 技能的显示名称 | ❌ INVALID（仅技能字段，不适用于命令 frontmatter） |
| 2 | HIGH | 新字段 | 在 frontmatter 表中添加 `disable-model-invocation` — 阻止自动加载 | ❌ INVALID（仅技能字段，不适用于命令 frontmatter） |
| 3 | HIGH | 新字段 | 在 frontmatter 表中添加 `user-invocable` — 从 `/` 菜单中隐藏 | ❌ INVALID（仅技能字段，不适用于命令 frontmatter） |
| 4 | HIGH | 新字段 | 在 frontmatter 表中添加 `context` — fork 以在子代理上下文中运行 | ❌ INVALID（仅技能字段，不适用于命令 frontmatter） |
| 5 | HIGH | 新字段 | 在 frontmatter 表中添加 `agent` — context: fork 的子代理类型 | ❌ INVALID（仅技能字段，不适用于命令 frontmatter） |
| 6 | HIGH | 新字段 | 在 frontmatter 表中添加 `hooks` — 作用域为技能的生命周期钩子 | ❌ INVALID（仅技能字段，不适用于命令 frontmatter） |
| 7 | HIGH | 新命令 | 添加 `/btw <question>` — 快速问一个副问题而不添加到对话中 | ✅ COMPLETE（在 Session 标签中作为 #53 添加） |
| 8 | HIGH | 新命令 | 添加 `/hooks` — 管理工具事件的钩子配置 | ✅ COMPLETE（在 Extensions 标签中作为 #30 添加） |
| 9 | HIGH | 新命令 | 添加 `/insights` — 生成会话分析报告 | ✅ COMPLETE（在 Context 标签中作为 #17 添加） |
| 10 | HIGH | 新命令 | 添加 `/plugin` — 管理 Claude Code 插件 | ✅ COMPLETE（在 Extensions 标签中作为 #33 添加） |
| 11 | HIGH | 新命令 | 添加 `/skills` — 列出可用技能 | ✅ COMPLETE（在 Extensions 标签中作为 #35 添加） |
| 12 | HIGH | 新命令 | 添加 `/upgrade` — 打开升级页面以切换计划层级 | ✅ COMPLETE（在 Auth 标签中作为 #3 添加） |
| 13 | HIGH | 移除命令 | 移除 `/output-style` — 在 v2.1.73 中弃用，改用 `/config` | ✅ COMPLETE（从 Config 标签中移除） |
| 14 | HIGH | 移除命令 | 移除 `/bug` 行 — 现在列为 `/feedback` 的别名 | ✅ COMPLETE（移除行，在 `/feedback` 描述中添加"别名：/bug"） |
| 15 | HIGH | 变更描述 | 更新 `/passes` — 从审查轮次重新用于推荐分享 | ✅ COMPLETE（更新描述，保留在 Model 标签中） |
| 16 | HIGH | 变更描述 | 更新 `/review` — 已弃用，由 `code-review` 市场插件替代 | ✅ COMPLETE（更新 Project 标签中的描述） |
| 17 | MED | 变更描述 | 更新 `/stickers` — 从 UI 贴纸包变更为订购实体贴纸 | ✅ COMPLETE（更新 Config 标签中的描述） |

---

## [2026-03-15 12:50 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/color [color\|default]` 到 Config 标签 — 设置当前会话的提示栏颜色 | ✅ COMPLETE（在 Config 标签中作为 #4 添加） |
| 2 | HIGH | 新命令 | 添加 `/effort [low\|medium\|high\|max\|auto]` 到 Model 标签 — 设置模型 effort 级别 | ✅ COMPLETE（在 Model 标签中作为 #38 添加） |
| 3 | MED | 变更描述 | 更新 `/status` — 现在为"打开设置界面（状态标签页）"而非"显示简洁的会话状态摘要" | ✅ COMPLETE（在 Context 标签 #20 处更新描述） |
| 4 | MED | 变更描述 | 更新 `/desktop` — 现在为"在当前会话中继续使用 Claude Code 桌面应用。仅限 macOS 和 Windows。" | ✅ COMPLETE（在 Remote 标签 #49 处更新描述） |
| 5 | LOW | 变更参数 | 更新 `/init` — 官方文档删除了 `[prompt]` 参数提示 | ✅ COMPLETE（在 Project 标签 #45 处移除 [prompt] 提示） |

---

## [2026-03-17 12:45 PM PKT] Claude Code v2.1.77

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新别名 | 在 `/fork` 条目中添加 `别名：/branch`（v2.1.77 将 fork 重命名为 branch） | ✅ COMPLETE（在 Session 标签 #59 处为 /fork 添加"别名：/branch"） |
| 2 | HIGH | 新别名 | 为 8 个命令添加别名：`/clear`（+/reset、/new）、`/config`（+/settings）、`/desktop`（+/app）、`/exit`（+/quit）、`/rewind`（+/checkpoint）、`/resume`（+/continue）、`/remote-control`（+/rc）、`/mobile`（+/ios、/android） | ✅ COMPLETE（为所有 8 个命令描述添加了别名标注） |
| 3 | MED | 变更描述 | 更新 `/diff` — "打开交互式差异查看器，显示未提交的更改和每轮差异" | ✅ COMPLETE（在 Project 标签 #44 处更新描述） |
| 4 | MED | 变更描述 | 更新 `/memory` — "编辑 CLAUDE.md 内存文件，启用或禁用自动内存，并查看自动内存条目" | ✅ COMPLETE（在 Memory 标签 #37 处更新描述） |
| 5 | MED | 变更描述 | 更新 `/copy` — "将最后一条助手回复复制到剪贴板。显示代码块的交互式选择器" | ✅ COMPLETE（在 Export 标签 #27 处更新描述） |
| 6 | MED | 变更描述 | 更新 `/mobile` — "显示 QR 码以下载 Claude 移动应用" | ✅ COMPLETE（在 Remote 标签 #52 处更新描述 + 别名） |
| 7 | MED | 变更描述 | 更新 `/remote-control` — "使此会话可从 claude.ai 进行远程控制" | ✅ COMPLETE（在 Remote 标签 #53 处更新描述 + 别名） |
| 8 | LOW | Frontmatter 作用域 | 6 个仅技能字段仍不在报告中（有意限定范围） | ❌ INVALID（仅技能字段 — 与 v2.1.74 运行相同的判断） |

---

## [2026-03-18 11:38 PM PKT] Claude Code v2.1.78

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/voice` 到 Config 标签 — 切换一键通语音听写 | ✅ COMPLETE（在 Config 标签中作为 #15 添加） |
| 2 | HIGH | 反转别名 | 将 `/fork` → `/branch` 作为主要命令，`/fork` 作为别名 | ✅ COMPLETE（在 Session 标签 #56 处交换为 `/branch`，按字母顺序重新排序） |
| 3 | MED | 新别名 | 添加 `/allowed-tools` 作为 `/permissions` 的别名 | ✅ COMPLETE（在 Config 标签 #7 处添加别名） |
| 4 | MED | 新参数 | 为 `/copy` 添加 `[N]` 参数语法 | ✅ COMPLETE（在 Export 标签 #28 处更新为 `/copy [N]`） |
| 5 | LOW | Frontmatter 作用域 | 6 个仅技能字段不在报告中（有意限定范围） | ❌ INVALID（仅技能字段 — 与 v2.1.74 和 v2.1.77 运行相同的判断） |

---

## [2026-03-19 11:54 AM PKT] Claude Code v2.1.79

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | LOW | Frontmatter 作用域 | 6 个仅技能字段不在报告中（有意限定范围） | ❌ INVALID（仅技能字段 — 与 v2.1.74、v2.1.77 和 v2.1.78 运行相同的判断） |

---

## [2026-03-20 08:33 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MED | 新字段 | 在 frontmatter 表中添加 `effort` — 调用命令时覆盖模型 effort 级别（v2.1.80） | ✅ COMPLETE（作为第 5 个字段添加，后在添加完整字段集时重新定位到第 8 位） |
| 2 | HIGH | QA 修正 | 添加 6 个缺失字段（`name`、`disable-model-invocation`、`user-invocable`、`context`、`agent`、`hooks`）— 官方文档指出命令支持"与技能相同的 frontmatter"；之前 INVALID 的判断（v2.1.74–v2.1.79）不正确 | ✅ COMPLETE（添加了所有 6 个字段，计数更新 5 → 11，字段顺序与官方文档一致） |
| 3 | HIGH | 跨报告修复 | 在技能报告（`claude-skills.md`）中添加 `effort` — 该字段在那里也缺失 | ✅ COMPLETE（在技能报告中作为第 8 个字段添加，计数更新 10 → 11） |

---

## [2026-03-21 09:08 PM PKT] Claude Code v2.1.81

没有优先级操作项 — 报告与官方文档完全同步（11 个 frontmatter 字段，63 个内置命令）。

---

## [2026-03-23 09:48 PM PKT] Claude Code v2.1.81

没有优先级操作项 — 报告与官方文档完全同步（11 个 frontmatter 字段，63 个内置命令）。

---

## [2026-03-25 08:07 PM PKT] Claude Code v2.1.83

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/schedule [description]` 到 Remote 标签 — 创建、更新、列出或运行云定时任务 | ✅ COMPLETE（在 Remote 标签中作为 #56 添加，计数更新 63 → 64） |

---

## [2026-03-26 01:01 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新字段 | 在 frontmatter 表中添加 `shell` — `!command` 块的 shell（`bash` 或 `powershell`） | ✅ COMPLETE（在 `hooks` 之前作为第 12 个字段添加，计数更新 11 → 12） |
| 2 | LOW | 变更参数 | 为 `/fast` 命令添加 `[on\|off]` 参数提示 | ✅ COMPLETE（在 Model 标签 #40 处将 `/fast` 更新为 `/fast [on\|off]`） |

---

## [2026-03-27 06:25 PM PKT] Claude Code v2.1.85

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新字段 | 在 frontmatter 表中添加 `paths` — 限制技能激活条件的 glob 模式 | ✅ COMPLETE（在 `user-invocable` 之后作为第 6 个字段添加，计数更新 12 → 13） |

---

## [2026-03-28 06:05 PM PKT] Claude Code v2.1.86

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MED | 变更参数 | 更新 `/add-dir` — 按官方文档添加 `<path>` 必需参数提示 | ✅ COMPLETE（在 Project 标签 #44 处更新） |
| 2 | MED | 变更参数 | 更新 `/branch` — 按官方文档添加 `[name]` 可选参数提示 | ✅ COMPLETE（在 Session 标签 #57 处更新） |
| 3 | MED | 变更参数 | 更新 `/model` — 按官方文档添加 `[model]` 可选参数提示 | ✅ COMPLETE（在 Model 标签 #41 处更新） |
| 4 | MED | 变更参数 | 更新 `/plan` — 按官方文档添加 `[description]` 可选参数提示 | ✅ COMPLETE（在 Model 标签 #43 处更新） |
| 5 | MED | 变更参数 | 更新 `/pr-comments` — 按官方文档添加 `[PR]` 可选参数提示 | ✅ COMPLETE（在 Project 标签 #47 处更新） |
| 6 | MED | 变更参数 | 更新 `/passes` — 移除 `[number]` 参数提示（不在官方文档中） | ✅ COMPLETE（在 Model 标签 #42 处更新） |
| 7 | MED | 变更参数 | 更新 `/rename` — 按官方文档从 `<name>`（必需）改为 `[name]`（可选） | ✅ COMPLETE（在 Session 标签 #62 处更新） |
| 8 | LOW | 变更参数 | 更新 `/compact` — 按官方文档将参数标签从 `[prompt]` 改为 `[instructions]` | ✅ COMPLETE（在 Session 标签 #60 处更新） |
| 9 | LOW | 变更参数 | 更新 `/feedback` — 按官方文档将参数标签从 `[description]` 改为 `[report]` | ✅ COMPLETE（在 Debug 标签 #24 处更新） |

---

## [2026-03-31 06:55 PM PKT] Claude Code v2.1.88

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MED | 描述同步 | 同步所有 43 个命令描述以匹配官方文档 — 行为澄清（`/vim` 切换、`/sandbox` 切换、`/hooks` 查看）、扩展细节（`/effort` 持久性、`/copy` SSH 写入、`/model` effort 箭头）和措辞对齐，涵盖 Auth、Config、Context、Debug、Export、Extensions、Model、Project、Remote 和 Session 标签 | ✅ COMPLETE（所有 64 个描述现在与 code.claude.com/docs/en/commands 的官方文档匹配） |

---

## [2026-04-01 12:26 PM PKT] Claude Code v2.1.89

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | LOW | 变更描述 | 更新 `/init` — 官方文档现在使用 `CLAUDE_CODE_NEW_INIT=1` 而非 `=true` | ✅ COMPLETE（环境变量值从 `=true` 更新为 `=1` 以匹配官方文档） |

---

## [2026-04-02 09:14 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MED | 变更描述 | 更新 `/permissions` — 官方文档扩展描述，包含作用域规则、目录管理和自动模式拒绝审查的交互式对话框 | ✅ COMPLETE（更新描述以匹配官方文档） |
| 2 | MED | 新别名 | 按官方文档为 `/tasks` 命令添加 `/bashes` 别名 | ✅ COMPLETE（在 Debug 标签 #27 处为 /tasks 添加"别名：/bashes"） |

---

## [2026-04-03 08:34 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/powerup` 到 Config 标签 — 通过快速交互式课程和动画演示发现 Claude Code 功能 | ✅ COMPLETE（在 Debug 标签中作为 #26 添加 — 在 v2.1.92 运行中解决） |

---

## [2026-04-04 10:40 PM PKT] Claude Code v2.1.92

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/powerup` 到 Debug 标签 — 通过快速交互式课程和动画演示发现 Claude Code 功能 | ✅ COMPLETE（在 Debug 标签中作为 #26 添加，从 v2.1.91 延续） |
| 2 | HIGH | 新命令 | 添加 `/setup-bedrock` 到 Auth 标签 — 通过交互式向导配置 Amazon Bedrock 认证、区域和模型固定 | ✅ COMPLETE（在 Auth 标签中作为 #3 添加） |
| 3 | HIGH | 新命令 | 添加 `/ultraplan <prompt>` 到 Model 标签 — 在 ultraplan 会话中起草计划，在浏览器中审查，然后远程执行或发回 | ✅ COMPLETE（在 Model 标签中作为 #45 添加） |
| 4 | HIGH | 移除命令 | 从 Config 标签移除 `/vim` — 在 v2.1.92 中移除（max-version：2.1.91），改用 `/config` 编辑器模式 | ✅ COMPLETE（从 Config 标签移除） |
| 5 | HIGH | 移除命令 | 从 Project 标签移除 `/pr-comments [PR]` — 在 v2.1.91 中移除（max-version：2.1.90），直接询问 Claude | ✅ COMPLETE（从 Project 标签移除） |
| 6 | MED | 变更描述 | 更新 `/release-notes` — 现在为"在交互式版本选择器中查看更新日志。选择特定版本查看其发布说明，或选择显示所有版本。" | ✅ COMPLETE（在 Debug 标签 #27 处更新描述） |

---

## [2026-04-08 09:35 PM PKT] Claude Code v2.1.96

没有优先级操作项 — 报告与官方文档完全同步（13 个 frontmatter 字段，65 个内置命令）。

---

## [2026-04-09 11:31 PM PKT] Claude Code v2.1.97

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/autofix-pr [prompt]` 到 Remote 标签 — 生成一个监视当前分支 PR 的 Web 会话，当 CI 失败或审阅者留下评论时推送修复 | ✅ COMPLETE（在 Remote 标签中作为 #51 添加，计数更新 65 → 68） |
| 2 | HIGH | 新命令 | 添加 `/teleport` 到 Remote 标签 — 将 Web 上的 Claude Code 会话拉取到当前终端中。别名：`/tp` | ✅ COMPLETE（在 Remote 标签中作为 #59 添加） |
| 3 | HIGH | 新命令 | 添加 `/web-setup` 到 Remote 标签 — 使用本地 `gh` CLI 凭据将 GitHub 账户连接到 Web 上的 Claude Code | ✅ COMPLETE（在 Remote 标签中作为 #60 添加） |
| 4 | MED | 变更描述 | 更新 `/add-dir` — 官方文档现在包含关于 `.claude/` 配置无法从添加的目录中发现的说明 | ✅ COMPLETE（在 Project 标签 #46 处更新描述） |

---

## [2026-04-13 08:00 PM PKT] Claude Code v2.1.101

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/setup-vertex` 到 Auth 标签 — 通过交互式向导配置 Google Vertex AI 认证、项目、区域和模型固定。仅在设置 `CLAUDE_CODE_USE_VERTEX=1` 时可见 | ✅ COMPLETE（在 Auth 标签中作为 #4 添加，计数更新 68 → 69） |

---

## [2026-04-14 11:13 PM PKT] Claude Code v2.1.107

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新字段 | 在 frontmatter 表中添加 `when_to_use` — 关于 Claude 何时应调用技能的额外上下文，附加到列表中的 `description` 之后（计数 13 → 14） | ✅ COMPLETE（在 `description` 字段之后添加，计数更新 13 → 14） |
| 2 | HIGH | 新命令 | 添加 `/team-onboarding` 到 Project 标签 — 从 Claude Code 使用历史生成团队入职指南（计数 69 → 70） | ✅ COMPLETE（在 Project 标签中作为 #52 添加，计数更新 69 → 70） |
| 3 | MED | 作用域决定 | 5 个内置技能（`/batch`、`/claude-api`、`/debug`、`/loop`、`/simplify`）列在官方文档统一表中，但根据报告当前作用域免责声明被排除 | ❌ INVALID（用户选择保持报告仅限于内置命令 — 保留免责声明） |
| 4 | MED | 变更描述 | 更新 `/doctor` — 添加"按 `f` 让 Claude 修复任何报告的问题" | ✅ COMPLETE（在描述中添加状态图标和 `f` 键修复细节） |
| 5 | MED | 变更描述 | 更新 `/schedule` — 术语从"云定时任务"变更为"routines" | ✅ COMPLETE（更新描述中的术语） |

---

## [2026-04-16 08:20 PM PKT] Claude Code v2.1.110

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MED | 新别名 | 为 `/rewind` 条目添加 `/undo` 别名 — 在 v2.1.108 中添加 | ✅ COMPLETE（在 Session 标签 #70 处添加 `/undo` 与现有 `/checkpoint` 别名并列） |

---

## [2026-04-18 07:54 PM PKT] Claude Code v2.1.114

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新命令 | 添加 `/recap` 到 Session 标签 — 按需生成当前会话的一行摘要（v2.1.108） | ✅ COMPLETE（在 Session 标签中作为 #72 添加，计数更新 70 → 75） |
| 2 | HIGH | 新命令 | 添加 `/focus` 到 Config 标签 — 切换焦点视图，仅显示最后一条提示、工具调用摘要和最终响应（v2.1.110） | ✅ COMPLETE（在 Config 标签中作为 #8 添加） |
| 3 | HIGH | 新命令 | 添加 `/tui [default\|fullscreen]` 到 Config 标签 — 设置终端 UI 渲染器并在保持对话内容的情况下重新启动（v2.1.110） | ✅ COMPLETE（在 Config 标签中作为 #17 添加） |
| 4 | HIGH | 新命令 | 添加 `/ultrareview [PR]` 到 Project 标签 — 在云沙盒中运行深度多代理代码审查（v2.1.111） | ✅ COMPLETE（在 Project 标签中作为 #56 添加） |
| 5 | HIGH | 新命令 | 添加 `/heapdump` 到 Debug 标签 — 将 JavaScript 堆快照和内存分解写入 `~/Desktop` 以诊断高内存使用 | ✅ COMPLETE（在 Debug 标签中作为 #28 添加） |
| 6 | HIGH | 变更描述 | 将 `/review` 从已弃用恢复为实时内置命令，按官方文档说明（"在当前会话中本地审查拉取请求。如需更深入的云端审查，请参阅 `/ultrareview`"）— 反转 v2.1.74 更新 | ✅ COMPLETE（在 Project 标签 #53 处更新描述，现在引用 `/ultrareview`） |
| 7 | MED | 变更描述 | 更新 `/effort` 描述 — 官方现在列出 `xhigh` 级别，并在无参数时打开交互式滑块（v2.1.111） | ✅ COMPLETE（更新参数提示以包含 `xhigh`，描述提及交互式滑块） |
| 8 | MED | 变更描述 | 更新 `/theme` 描述 — 官方添加了"自动（匹配终端）"选项（v2.1.111） | ✅ COMPLETE（在 Config 标签 #16 处的描述中添加"自动（匹配终端）"） |
| 9 | MED | 变更描述 | 更新 `/model` 描述 — 官方指出在对话中途切换前会发出警告（v2.1.108） | ✅ COMPLETE（在 Model 标签 #46 处添加对话中途警告细节） |
| 10 | MED | 新别名 | 按官方文档为 `/schedule` 命令添加 `/routines` 别名 | ✅ COMPLETE（在 Remote 标签 #64 处添加"别名：/routines"） |

---

## [2026-04-24 12:29 AM PKT] Claude Code v2.1.118

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 新字段 | 在 frontmatter 表中添加 `arguments` — 用于 `$name` 替换的命名位置参数（计数 14 → 15） | ✅ COMPLETE（在 `argument-hint` 之后添加，计数更新 14 → 15） |
| 2 | HIGH | 变更描述 | 更新 `/cost` — 现在只是 `/usage` 的别名 | ✅ COMPLETE（描述简化为"`/usage` 的别名"） |
| 3 | HIGH | 变更描述 | 更新 `/stats` — 现在是 `/usage` 的别名，打开统计标签页 | ✅ COMPLETE（描述更新为"`/usage` 的别名。打开统计标签页"） |
| 4 | HIGH | 变更描述 | 更新 `/usage` — 规范命令，吸收了 `/cost` 和 `/stats`；注明了别名 | ✅ COMPLETE（扩展为"显示会话成本、计划使用限制和活动统计。`/cost` 和 `/stats` 是别名"） |
| 5 | MED | 变更参数 | 将 `/voice` 签名更新为 `/voice [hold\|tap\|off]` | ✅ COMPLETE（签名和描述已更新） |
| 6 | MED | 变更描述 | 更新 `/theme` — 添加自定义主题支持（`~/.claude/themes/`、插件、"新建自定义主题…"） | ✅ COMPLETE（在描述中添加了自定义主题细节） |
| 7 | MED | 变更描述 | 更新 `/terminal-setup` — 替换终端列表（移除 Warp；添加 Cursor、Windsurf、Zed） | ✅ COMPLETE（终端列表已替换：VS Code、Cursor、Windsurf、Alacritty、Zed） |
| 8 | LOW | 变更描述 | 更新 `/effort` — 注明 `max` 级别仅限会话使用 | ✅ COMPLETE（在描述中为 `max` 添加"（仅限会话）"限定符） |

---

## [2026-04-26 01:10 PM PKT] Claude Code v2.1.119

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 变更描述 | 更新 `/branch` — 添加 `CLAUDE_CODE_FORK_SUBAGENT` 环境变量说明，解释 `/fork` 的分化（v2.1.117） | ✅ COMPLETE（在 Session 标签 #67 处的描述后附加 fork-subagent 说明） |
| 2 | MED | 变更描述 | 更新 `/focus` — 添加"仅在全屏渲染中可用"限定符（v2.1.110） | ✅ COMPLETE（在 Config 标签 #8 处附加仅限全屏限定符） |
| 3 | MED | 变更描述 | 更新 `/skills` — 添加"按 `t` 按 token 数量排序"（v2.1.110/111） | ✅ COMPLETE（在 Extensions 标签 #42 处附加按 token 数量排序细节） |
| 4 | MED | 变更描述 | 更新 `/clear` — 按官方文档改写以与 `/compact` 对比 | ✅ COMPLETE（在 Session 标签 #69 处将描述替换为"开始新的空上下文对话…改用 `/compact`"） |
| 5 | LOW | 作用域决定 | 6 个内置技能（`/batch`、`/claude-api`、`/debug`、`/fewer-permission-prompts`、`/loop`、`/simplify`）列在上游统一表中但根据报告作用域被排除 | ❌ INVALID（从 v2.1.107 延续 — 用户之前选择保持报告仅限于内置命令） |

---

## [2026-04-29 12:50 AM PKT] Claude Code v2.1.121

没有优先级操作项 — 报告与官方文档完全同步（15 个 frontmatter 字段，75 个内置命令）。

---

## [2026-05-01 03:31 PM PKT] Claude Code v2.1.126

没有优先级操作项 — 报告与官方文档完全同步（15 个 frontmatter 字段，75 个内置命令）。
