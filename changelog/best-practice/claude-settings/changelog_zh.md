# 设置报告 — 变更日志历史

## 状态图例

| 状态 | 含义 |
|--------|---------|
| ✅ `完成 (原因)` | 已采取行动并成功解决 |
| ❌ `无效 (原因)` | 发现结果不正确、不适用或有意为之 |
| ✋ `搁置 (原因)` | 操作推迟 — 等待外部依赖或用户决策 |

---

## [2026-03-05 06:18 AM PKT] Claude Code v2.1.69

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失设置 | 添加 13 个非钩子缺失设置键（`$schema`、`availableModels`、`fastModePerSessionOptIn`、`teammateMode`、`prefersReducedMotion`、`sandbox.filesystem.*`、`sandbox.network.allowManagedDomainsOnly`、`sandbox.enableWeakerNetworkIsolation`、`allowManagedMcpServersOnly`、`blockedMarketplaces`、`includeGitInstructions`、`pluginTrustMessage`、`fileSuggestion` 表格条目） | ✅ 完成（已添加到报告中） |
| 2 | 高 | 缺失环境变量 | 添加缺失的环境变量，包括 `CLAUDE_CODE_DISABLE_ADAPTIVE_THINKING`、`CLAUDE_CODE_DISABLE_1M_CONTEXT`、`CLAUDE_CODE_ACCOUNT_UUID`、`CLAUDE_CODE_DISABLE_GIT_INSTRUCTIONS`、`ENABLE_CLAUDEAI_MCP_SERVERS` 等 | ✅ 完成（已向报告添加 13 个缺失的环境变量） |
| 3 | 高 | 努力默认值 | 将 Max/Team 订阅者的努力级别默认值从"高"更新为"中"；添加 Sonnet 4.6 支持（v2.1.68 更改） | ✅ 完成（已更新默认值并添加 Sonnet 注释） |
| 4 | 中 | 设置层级 | 添加通过 macOS plist/Windows 注册表管理的设置（v2.1.61/v2.1.69）；记录跨作用域的数组合并行为 | ✅ 完成（已添加 plist/注册表和合并注释） |
| 5 | 中 | 沙箱文件系统 | 添加 `sandbox.filesystem.allowWrite`、`denyWrite`、`denyRead` 及路径前缀语义（`//`、`~/`、`/`、`./`） | ✅ 完成（已添加到沙箱表格） |
| 6 | 中 | 权限语法 | 添加 `Agent(name)` 权限模式；记录 `MCP(server:tool)` 语法形式 | ✅ 完成（已添加到工具语法表格） |
| 7 | 中 | 插件缺口 | 添加 `blockedMarketplaces`、`pluginTrustMessage` | ✅ 完成（已添加到插件表格） |
| 8 | 中 | 模型配置 | 添加 `availableModels` 设置 | ✅ 完成（已添加到通用设置表格） |
| 9 | 中 | 可疑键 | 验证 `sandbox.network.deniedDomains`、`sandbox.ignoreViolations`、`pluginConfigs` — 报告中存在但不在官方文档中 | ✋ 搁置（保留在报告中等待验证） |
| 10 | 低 | 标题计数 | 将标题从"38 个设置和 84 个环境变量"更新为实际数量（约 55+ 个设置，约 110+ 个环境变量） | ✅ 完成（已更新标题） |
| 11 | 低 | CLAUDE.md 同步 | 更新 CLAUDE.md 配置层级（添加管理/CLI/用户级别） | ✋ 搁置（等待用户批准） |
| 12 | 低 | 示例更新 | 使用 `$schema`、沙箱文件系统、`Agent(*)` 更新快速参考示例，移除钩子示例 | ✅ 完成（已更新示例） |
| 13 | 中 | 钩子重定向 | 用指向 claude-code-hooks 仓库的重定向替换钩子部分 | ✅ 完成（钩子已外部化到专用仓库） |

---

## [2026-03-07 02:17 PM PKT] Claude Code v2.1.71

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 行为变更 | 修复 `teammateMode`：类型 `boolean` → `string`，默认值 `false` → `"auto"`，描述 → "代理团队显示：auto、in-process、tmux" | ✅ 完成（类型、默认值和描述已更新） |
| 2 | 高 | 新设置 | 添加 `allowManagedPermissionRulesOnly` 到权限表格（布尔值，仅管理） | ✅ 完成（已添加到权限键表格） |
| 3 | 高 | 缺失环境变量 | 添加约 31 个缺失的环境变量，包括已确认的（`CLAUDE_CODE_MAX_OUTPUT_TOKENS`、`CLAUDE_CODE_DISABLE_FAST_MODE`、`CLAUDE_CODE_DISABLE_AUTO_MEMORY`、`CLAUDE_CODE_USER_EMAIL`、`CLAUDE_CODE_ORGANIZATION_UUID`、`CLAUDE_CONFIG_DIR`）和代理报告的（Foundry、Bedrock、mTLS、shell 前缀等） | ✅ 完成（已向表格添加 31 个环境变量） |
| 4 | 中 | 默认值变更 | 修复 `plansDirectory` 默认值从 `.claude/plans/` 改为 `~/.claude/plans` | ✅ 完成（默认值已更新） |
| 5 | 中 | 描述变更 | 修复 `sandbox.enableWeakerNetworkIsolation` 描述为"（仅 macOS）允许访问系统 TLS 信任；降低安全性" | ✅ 完成（描述已更新） |
| 6 | 中 | 作用域修复 | 修复 `extraKnownMarketplaces` 作用域从"任意"改为"项目" | ✅ 完成（作用域和描述已更新） |
| 7 | 中 | 边界违规 | 将 `claude-cli-startup-flags.md` 中的 `CLAUDE_CODE_EFFORT_LEVEL` 替换为对设置报告的交叉引用 | ✅ 完成（已替换为链接） |
| 8 | 中 | 版本徽章 | 将报告版本从 v2.1.69 更新为 v2.1.71 | ✅ 完成（徽章和标题已更新） |
| 9 | 低 | 可疑键 | 验证 `skipWebFetchPreflight`、`sandbox.ignoreViolations`、`sandbox.network.deniedDomains`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` | ✋ 搁置（保留在报告中等待验证 — 从 2026-03-05 重复出现） |
| 10 | 低 | CLAUDE.md 同步 | 更新 CLAUDE.md 配置层级（3 级 → 5+ 级） | ✅ 完成（已更新为 5 级层级，包含管理层） |

---

## [2026-03-12 12:23 PM PKT] Claude Code v2.1.74

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 行为变更 | 修复 `dontAsk` 权限模式描述："自动接受所有工具" → "除非通过 `/permissions` 或 `permissions.allow` 规则预先批准，否则自动拒绝工具" | ✅ 完成（描述已根据官方权限文档更正） |
| 2 | 高 | 新设置 | 添加 `modelOverrides` 到模型配置部分（对象，将 Anthropic 模型 ID 映射到特定提供商的 ID，如 Bedrock ARN） | ✅ 完成（已添加示例和描述） |
| 3 | 高 | 新设置 | 添加 `allow_remote_sessions` 到仅管理设置列表（布尔值，默认为 `true`，控制远程控制/网络会话访问） | ✅ 完成（已添加到权限键表格） |
| 4 | 高 | 默认值变更 | 修复 `$schema` URL 从 `https://www.schemastore.org/...` 改为 `https://json.schemastore.org/...` 根据官方文档 | ✅ 完成（已在描述、示例和来源中更新） |
| 5 | 中 | 描述变更 | 修复 `ANTHROPIC_CUSTOM_HEADERS` 格式描述从"JSON 字符串"改为"名称：值格式，换行分隔" | ✅ 完成（描述已根据官方文档更新） |
| 6 | 中 | 未验证模式 | `askEdits` 和 `viewOnly` 权限模式不在官方文档中 — 仅记录了 5 种模式（default、acceptEdits、plan、dontAsk、bypassPermissions） | ✅ 完成（在表格中标记为"不在官方文档中 — 未验证"） |
| 7 | 中 | 缺失环境变量 | 添加 `CLAUDE_CODE_SESSIONEND_HOOKS_TIMEOUT_MS`、`CLAUDE_CODE_DISABLE_FEEDBACK_SURVEY`、`CLAUDE_CODE_DISABLE_TERMINAL_TITLE`、`CLAUDE_CODE_IDE_SKIP_AUTO_INSTALL`、`CLAUDE_CODE_OTEL_HEADERS_HELPER_DEBOUNCE_MS` | ✅ 完成（已添加 5 个环境变量及 `CLAUDE_CODE_OTEL_HEADERS_HELPER_DEBOUNCE_MS`） |
| 8 | 中 | 新设置 | 添加 `autoMemoryDirectory` 到核心配置（字符串，自定义自动记忆目录）— 版本不确定（代理意见分歧：v2.1.68 与 v2.1.74），不在设置页面上 | ✅ 完成（已添加到 plansDirectory 附近 — 版本未解决） |
| 9 | 低 | 可疑键 | 验证 `skipWebFetchPreflight`、`sandbox.ignoreViolations`、`sandbox.network.deniedDomains`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 仍不在官方文档中 | ✋ 搁置（保留在报告中等待验证 — 从 2026-03-05 重复出现） |
| 10 | 低 | 缺失环境变量 | 添加 `CLAUDE_CODE_SUBAGENT_MODEL` 到环境变量表格（已在模型环境示例块中但表格中缺失） | ✅ 完成（已添加到环境变量表格） |
| 11 | 低 | 示例更新 | 更新快速参考示例以包含 `modelOverrides` 和更正的 `$schema` URL | ✅ 完成（示例已更新两者） |

---

## [2026-03-14 01:35 AM PKT] Claude Code v2.1.75

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 设置层级 | 重构以匹配官方 5 级层级：管理 (#1) > CLI 参数 > 本地 > 项目 > 用户。移除 `~/.claude/settings.local.json` 行。添加管理层级内部优先级（服务器管理 > MDM > 文件 > HKCU）。注意管理层"不能被任何其他级别覆盖，包括 CLI 参数" | ✅ 完成（表格重构为 5 级，管理为 #1，添加了交付方式、内部优先级和文件路径） |
| 2 | 高 | 行为变更 | 修复 `availableModels` 描述：从复杂对象数组（`title`/`modelId`/`effortOptions`）改为简单字符串数组 `["sonnet", "haiku"]` 根据官方文档 | ✅ 完成（描述已更新以匹配官方文档格式） |
| 3 | 高 | 行为变更 | 添加 `cleanupPeriodDays` `0` 值行为："设置为 `0` 会在启动时删除所有现有转录并完全禁用会话持久化" | ✅ 完成（描述中添加了 0 值行为） |
| 4 | 高 | 权限语法 | 在权限部分添加评估顺序说明："规则按顺序评估：先拒绝规则，然后询问，然后允许。第一个匹配的规则胜出。" | ✅ 完成（已在 Bash 通配符说明之前添加评估顺序） |
| 5 | 中 | 描述变更 | 添加 `autoMemoryDirectory` 作用域限制："不接受项目设置（`.claude/settings.json`）。接受来自策略、本地和用户设置" | ✅ 完成（描述中添加了作用域限制） |
| 6 | 中 | 描述变更 | 添加 `permissions.defaultMode` 远程环境说明：远程环境中仅支持 `acceptEdits` 和 `plan`（v2.1.70） | ✅ 完成（描述中添加了远程限制） |
| 7 | 中 | 模型配置 | 添加 Opus 4.6 1M 上下文默认说明：自 v2.1.75 起，Max/Team/Enterprise 计划默认使用 1M 上下文 | ✅ 完成（已添加到努力级别说明） |
| 8 | 中 | 设置层级 | 添加 Windows 管理路径说明：v2.1.75 移除了已弃用的 `C:\ProgramData\ClaudeCode\` 回退 — 使用 `C:\Program Files\ClaudeCode\managed-settings.json` | ✅ 完成（在层级部分添加了弃用说明） |
| 9 | 中 | 显示与用户体验 | 添加 `fileSuggestion` stdin JSON 格式（`{"query": "..."}`）和 15 路径输出限制详情 | ✅ 完成（已在文件建议部分添加 stdin 格式和输出限制） |
| 10 | 中 | 设置层级 | 将数组合并说明从"合并"更新为"连接并去重"根据官方文档 | ✅ 完成（已在层级重要部分更新措辞） |
| 11 | 低 | 可疑键 | `sandbox.ignoreViolations`、`sandbox.network.deniedDomains` 仍不在官方文档或 JSON schema 顶级 | ✋ 搁置（保留在报告中等待验证 — 从 2026-03-05 重复出现） |
| 12 | 低 | 可疑键 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 在 JSON schema 中已确认但不在官方设置页面上 | ✋ 搁置（保留在报告中 — 根据 schema 有效，从 2026-03-05 重复出现） |

---

## [2026-03-15 12:52 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `effortLevel` 到通用设置或模型配置 — 跨会话持久化努力级别（`"low"`、`"medium"`、`"high"`）。已在官方设置页面确认 | ✋ 搁置（等待用户批准） |
| 2 | 高 | 新设置 | 添加工作树设置部分，包含 `worktree.sparsePaths`（数组，sparse-checkout cone 模式）和 `worktree.symlinkDirectories`（数组，符号链接目录以避免重复）。已在官方设置页面确认 | ✋ 搁置（等待用户批准） |
| 3 | 高 | 新设置 | 添加 `feedbackSurveyRate` 到通用设置 — 会话质量调查的概率（0-1）。已在官方设置页面确认 | ✋ 搁置（等待用户批准） |
| 4 | 高 | 缺失环境变量 | 向表格添加 20 个缺失的环境变量：`CLAUDE_CODE_AUTO_COMPACT_WINDOW`、`CLAUDE_CODE_ENABLE_PROMPT_SUGGESTION`、`CLAUDE_CODE_PLAN_MODE_REQUIRED`、`CLAUDE_CODE_TEAM_NAME`、`CLAUDE_CODE_TASK_LIST_ID`、`CLAUDE_ENV_FILE`、`FORCE_AUTOUPDATE_PLUGINS`、`HTTP_PROXY`、`HTTPS_PROXY`、`NO_PROXY`、`MCP_TOOL_TIMEOUT`、`MCP_CLIENT_SECRET`、`MCP_OAUTH_CALLBACK_PORT`、`IS_DEMO`、`SLASH_COMMAND_TOOL_CHAR_BUDGET`、`VERTEX_REGION_CLAUDE_3_5_HAIKU`、`VERTEX_REGION_CLAUDE_3_7_SONNET`、`VERTEX_REGION_CLAUDE_4_0_OPUS`、`VERTEX_REGION_CLAUDE_4_0_SONNET`、`VERTEX_REGION_CLAUDE_4_1_OPUS`。已在官方 /en/env-vars 页面确认 | ✋ 搁置（等待用户批准） |
| 5 | 高 | 缺失环境变量 | 将 `ANTHROPIC_DEFAULT_OPUS_MODEL`、`ANTHROPIC_DEFAULT_SONNET_MODEL`、`MAX_THINKING_TOKENS` 从仅代码块移入通用环境变量表格 | ✋ 搁置（等待用户批准） |
| 6 | 高 | 链接失效 | 修复 `https://claudelog.com/configuration/` — 返回 ECONNREFUSED。移除或用有效来源替换 | ✋ 搁置（等待用户批准） |
| 7 | 中 | 描述变更 | 更新 `cleanupPeriodDays` 描述以添加：当设置为 0 时，"钩子接收空的 `transcript_path`"。根据官方文档 | ✋ 搁置（等待用户批准） |
| 8 | 中 | 未验证环境变量 | 将报告中但不在官方文档中的 7 个环境变量标记为未验证：`CLAUDE_CODE_DISABLE_MCP`、`CLAUDE_CODE_DISABLE_TOOLS`、`CLAUDE_CODE_HIDE_ACCOUNT_INFO`、`CLAUDE_CODE_MAX_TURNS`、`CLAUDE_CODE_PROMPT_CACHING_ENABLED`、`CLAUDE_CODE_SKIP_SETTINGS_SETUP`、`DISABLE_NON_ESSENTIAL_MODEL_CALLS` | ✋ 搁置（等待用户批准） |
| 9 | 中 | 新来源 | 将 `https://code.claude.com/docs/en/env-vars` 添加到来源部分 — 官方环境变量参考页面 | ✋ 搁置（等待用户批准） |
| 10 | 中 | 示例更新 | 更新快速参考示例以包含 `effortLevel` 和 `worktree` 设置 | ✋ 搁置（等待用户批准） |
| 11 | 低 | 可疑键 | `sandbox.ignoreViolations`、`sandbox.network.deniedDomains` 仍不在官方文档沙箱表格中 | ✋ 搁置（保留在报告中等待验证 — 从 2026-03-05 重复出现） |
| 12 | 低 | 可疑键 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 仍在 JSON schema 中但不在官方设置页面上 | ✋ 搁置（保留在报告中 — 根据 schema 有效，从 2026-03-05 重复出现） |

---

## [2026-03-15 01:10 PM PKT] Claude Code v2.1.76

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `effortLevel` 到模型配置 — 跨会话持久化努力级别（`"low"`、`"medium"`、`"high"`）。还在有用命令中添加了 `/effort` 命令并更新了努力级别操作指南部分 | ✅ 完成（已添加到模型覆盖表格，更新了操作指南，添加了 /effort 命令） |
| 2 | 高 | 新设置 | 添加工作树设置部分，包含 `worktree.sparsePaths`（数组，sparse-checkout cone 模式）和 `worktree.symlinkDirectories`（数组，符号链接目录以避免重复） | ✅ 完成（在核心配置中新建工作树设置子部分，包含表格和示例） |
| 3 | 高 | 新设置 | 添加 `feedbackSurveyRate` 到通用设置 — 会话质量调查的概率（0-1） | ✅ 完成（已添加到通用设置表格） |
| 4 | 高 | 缺失环境变量 | 向表格添加 23 个缺失的环境变量（20 个全新 + 3 个来自仅代码块） | ✅ 完成（已将全部 23 个环境变量添加到通用环境变量表格） |
| 5 | 高 | 链接失效 | 先前运行标记 `https://claudelog.com/configuration/` 为 ECONNREFUSED — 现已成功加载 | ✅ 完成（链接已恢复，无需操作） |
| 6 | 中 | 权限语法 | 添加读取/编辑 gitignore 风格路径模式（`//path`、`~/path`、`/path`、`./path`）、词边界通配符详情和旧版 `:*` 弃用说明 | ✅ 完成（已添加路径模式表格、词边界说明和 `:*` 弃用） |
| 7 | 中 | 描述变更 | 更新 `cleanupPeriodDays` 以添加当设置为 0 时"钩子接收空的 `transcript_path`" | ✅ 完成（已添加到描述） |
| 8 | 中 | 未验证环境变量 | 将不在官方文档中的 7 个环境变量标记为未验证 | ✅ 完成（已添加"不在官方文档中 — 未验证"标记） |
| 9 | 中 | 新来源 | 将 `https://code.claude.com/docs/en/env-vars` 和 `https://code.claude.com/docs/en/permissions` 添加到来源部分 | ✅ 完成（已添加两个 URL） |
| 10 | 中 | 示例更新 | 更新快速参考示例以包含 `effortLevel` 和 `worktree` 设置 | ✅ 完成（示例中添加了 effortLevel 和 worktree 块） |
| 11 | 低 | 可疑键 | `sandbox.ignoreViolations`、`sandbox.network.deniedDomains` 仍不在官方文档沙箱表格中 | ✋ 搁置（保留在报告中等待验证 — 从 2026-03-05 重复出现） |
| 12 | 低 | 可疑键 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 仍在 JSON schema 中但不在官方设置页面上 | ✋ 搁置（保留在报告中 — 根据 schema 有效，从 2026-03-05 重复出现） |

---

## [2026-03-17 12:54 PM PKT] Claude Code v2.1.77

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `sandbox.filesystem.allowRead` 到沙箱设置表格 — 在 `denyRead` 区域内重新允许读取访问（数组，默认 `[]`）。在 v2.1.77 变更日志中确认 | ✅ 完成（已添加到沙箱设置表格，位于 denyRead 行之后） |
| 2 | 高 | 描述变更 | 更新 `CLAUDE_CODE_MAX_OUTPUT_TOKENS` 描述：Opus 4.6 的默认值提升至 64k，Opus 4.6 和 Sonnet 4.6 的上限提升至 128k（v2.1.77 变更日志） | ✅ 完成（描述已更新，包含特定模型的默认值和上限） |
| 3 | 高 | 缺失环境变量 | 添加 `CLAUDECODE` 到通用环境变量表格 — 在生成的 shell 环境中设置为 `1`。在官方 /en/env-vars 页面确认 | ✅ 完成（已添加到环境变量表格） |
| 4 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_SKIP_FAST_MODE_NETWORK_ERRORS` 到通用环境变量表格 — 当组织状态检查失败时允许快速模式。在官方 /en/env-vars 页面确认 | ✅ 完成（已添加到环境变量表格） |
| 5 | 中 | 环境变量表格 | 将 `ANTHROPIC_MODEL` 和 `ANTHROPIC_DEFAULT_HAIKU_MODEL` 从仅代码块移入通用环境变量表格。两者均在官方 /en/env-vars 页面确认 | ✅ 完成（已将两者添加到环境变量表格，位于其他 ANTHROPIC_ 变量附近） |
| 6 | 中 | 可疑键升级 | `sandbox.network.deniedDomains` — 连续 8 次运行搁置（自 2026-03-05 起）。不在官方文档页面或 JSON schema 中。根据规则 10B：标记为"不在官方文档中 — 未验证" | ✅ 完成（描述中添加了未验证注释） |
| 7 | 中 | 可疑键升级 | `allow_remote_sessions` — 不在官方文档页面或 JSON schema 中。标记为"不在官方文档中 — 未验证" | ✅ 完成（描述中添加了未验证注释） |
| 8 | 低 | 可疑键解决 | `sandbox.ignoreViolations` — 连续 8 次运行搁置。在 JSON schema 中确认。注释："在 JSON schema 中，不在官方设置页面上" | ✅ 完成（描述中添加了 schema 注释） |
| 9 | 低 | 可疑键解决 | `skipWebFetchPreflight`、`skippedMarketplaces`、`skippedPlugins`、`pluginConfigs` — 连续 8 次运行搁置。全部在 JSON schema 中确认。注释："在 JSON schema 中，不在官方设置页面上" | ✅ 完成（已将 schema 注释添加到全部 4 个描述中） |
| 10 | 低 | 标题计数 | 更新标题环境变量计数从"160+"改为"100+" — 实际表格有 97 个环境变量 | ✅ 完成（标题已更新为"100+ 环境变量"，版本更新为 v2.1.77） |

---

## [2026-03-18 11:53 PM PKT] Claude Code v2.1.78

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失设置 | 添加 `voiceEnabled` 到通用设置表格 — 启用即按即说语音听写（布尔值，由 `/voice` 写入，需要 Claude.ai 账户）。在官方设置页面确认 | ✅ 完成（已添加到通用设置表格，位于 feedbackSurveyRate 之前） |
| 2 | 高 | 缺失设置 | 添加 `filesystem.allowManagedReadPathsOnly` 到沙箱设置表格 — 仅管理，仅信任管理的 `allowRead` 路径（布尔值，默认为 false）。在官方设置页面确认 | ✅ 完成（已添加到沙箱设置表格，位于 enableWeakerNetworkIsolation 之前） |
| 3 | 高 | 显示位置 | 将 `showTurnDuration` 和 `terminalProgressBarEnabled` 从显示设置表格移至单独的"全局配置设置（~/.claude.json）"子部分。官方文档说明："将它们添加到 settings.json 会触发 schema 验证错误" | ✅ 完成（已创建新子部分及表格；已从 settings.json 显示设置表格和示例中移除） |
| 4 | 高 | 默认值变更 | 修复 `MAX_MCP_OUTPUT_TOKENS` 默认值从 50000 改为 25000。官方 /en/env-vars 页面确认默认值：25000 | ✅ 完成（默认值已更新，添加了警告阈值说明） |
| 5 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_NEW_INIT`、`CLAUDE_CODE_PLUGIN_SEED_DIR`、`DISABLE_FEEDBACK_COMMAND` 到环境变量表格。全部在官方 /en/env-vars 页面确认 | ✅ 完成（已将全部 3 个环境变量添加到表格） |
| 6 | 中 | 验证修复 | 从 `allow_remote_sessions` 移除"未验证"注释 — 现已在官方权限页面上确认为仅管理设置。先前运行（v2.1.77 #7）错误地将其标记为未验证 | ✅ 完成（已移除"未验证"注释） |
| 7 | 中 | 环境变量重命名 | 将 `DISABLE_BUG_COMMAND` 更新为 `DISABLE_FEEDBACK_COMMAND` — 官方文档称 `DISABLE_FEEDBACK_COMMAND` 是当前名称，`DISABLE_BUG_COMMAND` 是"旧名称" | ✅ 完成（已重命名并添加别名说明） |
| 8 | 中 | 描述变更 | 更新 `CLAUDE_CODE_EFFORT_LEVEL` 以包含 `max`（仅 Opus 4.6）和 `auto` 值。官方 /en/env-vars 页面确认："值：low、medium、high、max（仅 Opus 4.6）或 auto" | ✅ 完成（描述已更新，包含所有值和优先级说明） |
| 9 | 中 | 描述变更 | 修复 `CLAUDE_CODE_ENABLE_TASKS` 描述 — 官方："设置为 true 以在非交互模式（-p 标志）中启用任务跟踪。任务在交互模式中默认开启。"报告当前称"设置为 false 以禁用" | ✅ 完成（描述已更正以匹配官方文档） |
| 10 | 中 | 描述变更 | 更新 `CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC` 以注明："相当于同时设置 DISABLE_AUTOUPDATER、DISABLE_FEEDBACK_COMMAND、DISABLE_ERROR_REPORTING 和 DISABLE_TELEMETRY" | ✅ 完成（描述已更新，包含等效变量列表） |
| 11 | 中 | 示例更新 | 从快速参考示例中移除 `showTurnDuration` — 根据官方文档，它不属于 settings.json | ✅ 完成（已从快速参考示例和显示与用户体验示例中移除） |
| 12 | 低 | 环境变量默认值 | 验证 `MCP_TIMEOUT` 默认值（报告称 10000）— 官方文档未指定默认值 | ✅ 完成（已移除未经验证的默认值 — 官方文档省略了它） |

---

## [2026-03-19 12:38 PM PKT] Claude Code v2.1.79

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失环境变量 | 添加 `ANTHROPIC_CUSTOM_MODEL_OPTION`、`ANTHROPIC_CUSTOM_MODEL_OPTION_NAME`、`ANTHROPIC_CUSTOM_MODEL_OPTION_DESCRIPTION` 到通用环境变量表格 — 用于向 `/model` 选择器添加自定义条目的模型配置变量。在官方 /en/env-vars 页面确认 | ✅ 完成（已在表格中 ANTHROPIC_BASE_URL 之后添加 3 个环境变量） |
| 2 | 高 | 描述变更 | 将 `CLAUDE_CODE_PLUGIN_SEED_DIR` 从单数更新为复数："一个或多个只读插件种子目录的路径，在 Unix 上用 `:` 分隔，在 Windows 上用 `;` 分隔"。在 v2.1.79 变更日志中更改。在官方 /en/env-vars 页面确认 | ✅ 完成（描述已更新为多目录支持） |
| 3 | 高 | 沙箱路径前缀 | 修复 sandbox.filesystem 路径前缀文档：`/` = 绝对路径（标准 Unix），`./` = 项目相对，`//` = 旧版仍可工作。报告中当前显示相反约定。官方文档明确说明："此语法不同于读取和编辑权限规则" | ✅ 完成（已更新全部 4 个 sandbox.filesystem 条目，使用正确的前缀约定，添加了指向读取/编辑权限规则的交叉引用说明，以及跨作用域合并详情） |
| 4 | 中 | 描述变更 | 扩展 `CLAUDE_CODE_AUTO_COMPACT_WINDOW` 描述 — 当前的"自动压缩窗口行为配置"过于简略。官方文档描述：token 容量、默认值（200K 标准 / 1M 扩展）、与 `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE` 的交互、状态行解耦 | ✅ 完成（扩展描述，包含 token 容量、模型默认值、AUTOCOMPACT_PCT 交互和状态行解耦） |

---

## [2026-03-20 08:41 AM PKT] Claude Code v2.1.80

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `channelsEnabled` 到 MCP 设置表格 — 仅管理布尔值，控制团队和企业用户的频道消息投递。在官方设置页面确认 | ✅ 完成（已添加到 MCP 设置表格，位于 allowManagedMcpServersOnly 之后） |
| 2 | 中 | 版本徽章 | 将报告版本从 v2.1.79 更新为 v2.1.80 | ✅ 完成（徽章和标题已更新） |

---

## [2026-03-21 09:17 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失设置（~/.claude.json） | 添加 `autoConnectIde`（布尔值，默认 `false`）和 `autoInstallIdeExtension`（布尔值，默认 `true`）到全局配置设置表格。在官方设置页面的"全局配置设置"下确认 | ✅ 完成（已将两个键添加到 ~/.claude.json 表格，位于 showTurnDuration 之前） |
| 2 | 高 | 错误设置 | `allow_remote_sessions` 在权限键表格中被列为仅管理布尔值，但官方权限页面说明："远程控制和网络会话的访问不由管理设置键控制。"标记为未验证或移除 | ✅ 完成（重新添加了未验证注释，包含官方文档引用和管理界面链接） |
| 3 | 中 | 版本提升 | 将报告版本徽章从 v2.1.80 更新为 v2.1.81 | ✅ 完成（徽章、标题版本和标题文本已更新） |
| 4 | 中 | 新设置 | 添加 `showClearContextOnPlanAccept` — 在 v2.1.81 变更日志中确认。当为 `true` 时，在计划接受时恢复"清除上下文"选项（默认隐藏）。尚未在官方设置页面上 — 可能是 `~/.claude.json` 键 | ✅ 完成（已添加到全局配置设置表格，附带变更日志来源说明） |
| 5 | 中 | 插件文档 | 在插件设置部分记录 `source: 'settings'` 作为市场来源类型。官方设置页面将其列为 `extraKnownMarketplaces` 的 7 种来源类型之一 | ✅ 完成（已添加全部 7 种来源类型列表和内联市场示例） |
| 6 | 中 | 状态行字段 | 添加 `rate_limits` 字段组到状态行输入字段表格 — 包括 `five_hour.used_percentage`、`five_hour.resets_at`、`seven_day.used_percentage`、`seven_day.resets_at`。在 v2.1.80 中添加 | ✅ 完成（已向状态行输入字段表格添加 4 个 rate_limits 字段） |

---

## [2026-03-23 10:02 PM PKT] Claude Code v2.1.81

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失设置（~/.claude.json） | 添加 `editorMode`（字符串，默认 `"normal"`，值：`"normal"` 或 `"vim"`）到全局配置设置表格。运行 `/vim` 时自动写入。在官方设置页面确认 | ✅ 完成（已添加到全局配置设置表格，位于 autoInstallIdeExtension 之后） |
| 2 | 高 | 文件作用域修复 | 将 `showClearContextOnPlanAccept` 从全局配置设置（~/.claude.json）移至通用设置（settings.json）。官方文档现在将其列在主可用设置表格中，而非全局配置表格。移除过时的注释"尚未在官方设置页面上" | ✅ 完成（已移到通用设置表格，位于 feedbackSurveyRate 之前，移除了过时注释） |
| 3 | 中 | 描述变更 | 修复 `terminalProgressBarEnabled` 支持的终端从"Windows Terminal、iTerm2"改为"ConEmu、Ghostty 1.2.0+ 和 iTerm2 3.6.6+"根据官方文档 | ✅ 完成（终端列表已更新） |
| 4 | 中 | 描述变更 | 在 `availableModels` 描述中添加"配置工具" — 官方文档称"通过 `/model`、`--model`、配置工具或 `ANTHROPIC_MODEL`"。报告当前省略了"配置工具" | ✅ 完成（描述中添加了"配置工具"） |

---

## [2026-03-25 08:16 PM PKT] Claude Code v2.1.83

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `autoMode` 到权限部分 — 包含 `environment`、`allow`、`soft_deny` 数组的对象，用于配置自动模式分类器。不从共享项目设置（`.claude/settings.json`）读取。在用户、本地和管理设置中可用。在官方设置 + 权限页面上确认 | ✅ 完成（已添加到权限键表格，包含完整描述、作用域限制和 `claude auto-mode defaults` 说明） |
| 2 | 高 | 新设置 | 添加 `disableAutoMode` 到权限部分 — 字符串，设置为 `"disable"` 以防止自动模式激活。从 Shift+Tab 循环中移除 `auto`。可在任何设置级别设置，在管理设置中最有用。在官方设置 + 权限页面上确认 | ✅ 完成（已添加到权限键表格，位于 `autoMode` 之后） |
| 3 | 高 | 新权限模式 | 添加 `auto` 到权限模式表格 — 后台分类器替代手动提示。研究预览。需要 Team 计划 + Sonnet/Opus 4.6。在官方权限模式页面上确认 | ✅ 完成（已添加到权限模式表格，包含分类器详情和回退行为） |
| 4 | 高 | 新设置 | 添加 `sandbox.failIfUnavailable` 到沙箱设置表格 — 布尔值，默认 `false`，当沙箱启用但无法启动时出错退出而非在无沙箱模式下运行。在 v2.1.83 变更日志中确认 | ✅ 完成（已添加到沙箱设置表格，位于 `sandbox.enabled` 之后） |
| 5 | 高 | 新设置 | 添加 `disableDeepLinkRegistration` 到通用设置表格 — 布尔值，阻止 `claude-cli://` 协议处理程序注册。在 v2.1.83 变更日志中确认 | ✅ 完成（已添加到通用设置表格，位于 `feedbackSurveyRate` 之前） |
| 6 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB` 到通用环境变量表格 — 设置为 `1` 以从子进程环境（Bash 工具、钩子、MCP stdio 服务器）中剥离 Anthropic 和云提供商凭证。在 v2.1.83 变更日志中确认 | ✅ 完成（已添加到环境变量表格，位于 `CLAUDE_CODE_SUBAGENT_MODEL` 之后） |
| 7 | 高 | 设置层级 | 在管理设置部分添加 `managed-settings.d/` 放置目录 — 与 `managed-settings.json` 一起按字母顺序合并的独立策略片段。在 v2.1.83 变更日志中确认 | ✅ 完成（已作为管理设置交付方式下的要点添加） |
| 8 | 高 | 链接失效 | 修复来源中的 `https://claudelog.com/configuration/` — 返回 403 禁止。移除或用有效来源替换 | ✅ 完成（已替换为经验证有效的 `https://claudelog.com/claude-code-changelog/`） |
| 9 | 中 | 版本徽章 | 将报告版本从 v2.1.81 更新为 v2.1.83 | ✅ 完成（徽章和标题已在阶段 2.6 中更新） |
| 10 | 中 | 示例更新 | 在快速参考示例中添加 `autoMode` 以演示自动模式分类器配置 | ✅ 完成（在 `permissions` 块之前添加了带有 `environment` 数组的 `autoMode` 块） |
| 11 | 中 | 路径变更 | 修复 Windows 注册表路径从 `Software\Anthropic\ClaudeCode` 改为 `SOFTWARE\Policies\ClaudeCode`（HKLM 和 HKCU）。官方文档已更新为使用 `Policies` 子键 | ✅ 完成（已更新为 `HKLM\SOFTWARE\Policies\ClaudeCode` 和 `HKCU\SOFTWARE\Policies\ClaudeCode`，附带优先级说明） |
| 12 | 低 | 缺失别名 | 添加 `opus[1m]` 到模型别名表格 — Opus 4.6 带 1M 上下文，自 v2.1.75 起在 Max/Team/Enterprise 上默认可用 | ✅ 完成（已添加到模型别名表格，位于 `sonnet[1m]` 之后） |

---

## [2026-03-26 01:04 PM PKT] Claude Code v2.1.84

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `defaultShell` 到通用设置 — 字符串，默认 `"bash"`，接受 `"bash"` 或 `"powershell"`。在 Windows 上通过 PowerShell 路由交互式 `!` 命令。需要 `CLAUDE_CODE_USE_POWERSHELL_TOOL=1`。在官方设置页面确认 | ✅ 完成（已添加到通用设置表格，位于 teammateMode 之后） |
| 2 | 高 | 新设置 | 添加 `allowedChannelPlugins` 到 MCP 设置 — 数组，仅管理。可推送消息的频道插件允许列表。设置后将替换默认的 Anthropic 允许列表。需要 `channelsEnabled: true`。在官方设置页面确认 | ✅ 完成（已添加到 MCP 设置表格，位于 channelsEnabled 之后） |
| 3 | 高 | 新设置 | 添加 `useAutoModeDuringPlan` 到权限键 — 布尔值，默认 `true`。当自动模式可用时，计划模式使用自动模式语义。不从共享项目设置读取。在官方设置页面确认 | ✅ 完成（已添加到权限键表格，位于 disableAutoMode 之后） |
| 4 | 高 | 缺失环境变量 | 添加 9 个模型定制环境变量：`ANTHROPIC_DEFAULT_{OPUS,SONNET,HAIKU}_MODEL_{NAME,DESCRIPTION,SUPPORTED_CAPABILITIES}` 用于在 Bedrock/Vertex/Foundry 上定制 `/model` 选择器。在官方 /en/env-vars 页面确认 | ✅ 完成（已在每个基础模型变量之后添加 3 个变量：Haiku、Opus、Sonnet） |
| 5 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_DISABLE_NONSTREAMING_FALLBACK` — 流式失败时禁用非流式回退。防止通过代理重复执行工具。在官方 /en/env-vars 页面确认（v2.1.83 添加，上次运行遗漏） | ✅ 完成（已在 CLAUDE_CODE_DISABLE_FAST_MODE 之后添加） |
| 6 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_USE_POWERSHELL_TOOL` — 在 Windows 上启用 PowerShell 工具（选择加入预览）。仅原生 Windows，非 WSL。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_USE_FOUNDRY 之后添加） |
| 7 | 高 | 链接失效 | 修复来源中的 `https://claudelog.com/claude-code-changelog/` — 返回 403 禁止。替换为官方 GitHub 变更日志 URL | ✅ 完成（已替换为 github.com/anthropics/claude-code/blob/main/CHANGELOG.md） |
| 8 | 中 | 设置层级 | 更新管理层级优先级："基于文件（`managed-settings.d/*.json` + `managed-settings.json`）"并添加"跨层级"限定符。根据官方文档添加层级内合并说明 | ✅ 完成（已更新优先级描述，包含基于文件的层级和跨层级限定符） |
| 9 | 中 | 设置层级 | 扩展放置目录合并语义：systemd 约定、标量覆盖、数组连接+去重、深度合并、隐藏文件排除、数字前缀提示。根据官方设置页面 | ✅ 完成（已扩展完整的 systemd 约定详情和数字前缀提示） |
| 10 | 中 | 注释 | 根据规则 1F 逆完整性检查，在 `disableDeepLinkRegistration` 上添加"在变更日志中，不在官方设置页面上"注释 | ✅ 完成（描述中添加了注释） |
| 11 | 中 | 示例更新 | 在快速参考示例中添加 `defaultShell` 以演示 PowerShell 配置 | ✅ 完成（示例中添加了 "defaultShell": "bash"） |

---

## [2026-03-27 06:32 PM PKT] Claude Code v2.1.85

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失环境变量 | 添加 `CLAUDE_STREAM_IDLE_TIMEOUT_MS` 到通用环境变量表格 — 流式空闲监视器关闭停滞连接前的超时毫秒数（默认：90000）。在官方 /en/env-vars 页面确认。在 v2.1.84 中添加但上次运行遗漏 | ✅ 完成（已在环境变量表格中 CLAUDE_CODE_OTEL_HEADERS_HELPER_DEBOUNCE_MS 之后添加） |
| 2 | 高 | 版本提升 | 将报告版本徽章从 v2.1.84 更新为 v2.1.85 | ✅ 完成（徽章、标题版本和标题文本已在阶段 2.6 中更新） |
| 3 | 中 | 新环境变量 | 添加 `OTEL_LOG_TOOL_DETAILS` 到环境变量表格 — 控制 OpenTelemetry 事件中的 `tool_parameters`。仅 v2.1.85 变更日志（尚未在官方 env-vars 页面上）。添加附带变更日志来源注释 | ✅ 完成（已添加"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上"注释） |
| 4 | 中 | 新环境变量（所有权） | 决定 `CLAUDE_CODE_MCP_SERVER_NAME` 和 `CLAUDE_CODE_MCP_SERVER_URL` 的所有权 — 传递给 MCP `headersHelper` 脚本的环境变量（v2.1.85 变更日志）。可能属于钩子仓库而非设置报告 | ✅ 完成（已添加到设置报告，附带变更日志注释 — 这些可通过 `env` 键配置环境，非仅钩子） |

---

## [2026-03-28 06:10 PM PKT] Claude Code v2.1.86

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 文件作用域 | 将 `teammateMode` 从通用设置（settings.json）移至全局配置设置（~/.claude.json）。官方设置页面将其列在"全局配置设置"下 — 添加到 settings.json 会触发 schema 验证错误（规则 1H）。与 v2.1.78 `showTurnDuration` 修复相同的模式 | ✅ 完成（已从通用设置表格移除，添加到全局配置设置表格，位于 terminalProgressBarEnabled 之后，包含 agent-teams 文档链接） |
| 2 | 高 | 类型 + 注释 | 修复 `disableDeepLinkRegistration`：类型从 `boolean` 改为 `string`（值：`"disable"`），更新描述以匹配官方文档，移除过时的"（在变更日志中，不在官方设置页面上）"注释。现已在官方设置页面确认（第 169 行） | ✅ 完成（类型改为字符串，描述更新以匹配官方文档，变更日志注释已移除） |
| 3 | 高 | 版本提升 | 将报告版本徽章从 v2.1.85 更新为 v2.1.86 | ✅ 完成（徽章和标题已在阶段 2.6 中更新） |

---

## [2026-03-31 07:02 PM PKT] Claude Code v2.1.88

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_NO_FLICKER` 到通用环境变量表格 — 启用无闪烁备屏渲染（v2.1.88）。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_DISABLE_TERMINAL_TITLE 之后添加） |
| 2 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_SCROLL_SPEED` 和 `CLAUDE_CODE_DISABLE_MOUSE` 到通用环境变量表格 — 全屏 UI 控制。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_NO_FLICKER 之后添加） |
| 3 | 高 | 版本提升 | 将报告版本徽章从 v2.1.86 更新为 v2.1.88 | ✅ 完成（徽章、标题版本和标题文本已在阶段 2.6 中更新） |
| 4 | 高 | 链接失效 | 修复来源中的 `https://www.eesel.ai/blog/settings-json-claude-code` — 返回仅 CSS 内容，无可读博客文章 | ✅ 完成（已从来源部分移除失效链接） |
| 5 | 中 | 设置层级 | 添加 `managed-mcp.json` 到基于文件的管理交付方式 — 官方设置页面将其与 `managed-settings.json` 并列为 MCP 服务器配置方式 | ✅ 完成（已添加到设置层级中的文件交付方式要点） |
| 6 | 中 | 插件来源类型 | 将 `url`、`npm`、`file` 市场来源类型注释为"不在官方文档中 — 未验证"（仅 `github`、`git`、`directory`、`hostPattern`、`settings` 已确认） | ✅ 完成（已向全部 3 种来源类型添加未验证注释） |
| 7 | 低 | 标题计数 | 将标题从"60+ 设置"更新为添加后的实际表格计数 | ❌ 无效（计数准确 — 60+ 设置和 125 个环境变量，均在所述范围内） |

---

## [2026-04-01 12:32 PM PKT] Claude Code v2.1.89

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失设置 | 添加 `skipDangerousModePermissionPrompt` 到权限键表格 — 布尔值，跳过绕过模式确认提示。在项目设置中忽略。在官方设置页面确认 | ✅ 完成（已添加到权限键表格，位于 disableBypassPermissionsMode 之后） |
| 2 | 高 | 新设置 | 添加 `showThinkingSummaries` 到通用设置 — 布尔值，默认 `false`。默认不再生成思考摘要；设置为 `true` 恢复。v2.1.89 变更日志 — 尚未在官方设置页面上 | ✅ 完成（已在 feedbackSurveyRate 之前添加，附带变更日志注释） |
| 3 | 高 | 行为变更 | 更新 `cleanupPeriodDays` 描述 — v2.1.89 变更日志称 `0` 现已被拒绝并返回验证错误。矛盾：官方设置页面仍将 `0` 描述为有效。标记给用户 | ✅ 完成（描述已更新，包含变更日志与文档页面之间的矛盾说明） |
| 4 | 高 | 缺失环境变量 | 添加约 46 个在官方 /en/env-vars 页面确认的缺失环境变量：`ANTHROPIC_BEDROCK_BASE_URL`、`ANTHROPIC_VERTEX_BASE_URL`、`ANTHROPIC_BETAS`、`ANTHROPIC_VERTEX_PROJECT_ID`、`CLAUDE_CODE_DISABLE_THINKING`、`DISABLE_INTERLEAVED_THINKING`、`ENABLE_PROMPT_CACHING_1H_BEDROCK`、`DISABLE_AUTO_COMPACT`、`DISABLE_COMPACT`、`CLAUDE_CODE_DISABLE_FILE_CHECKPOINTING`、`CLAUDE_CODE_DISABLE_ATTACHMENTS`、`CLAUDE_CODE_DISABLE_CLAUDE_MDS`、`CLAUDE_CODE_GLOB_HIDDEN`、`CLAUDE_CODE_GLOB_NO_IGNORE`、`CLAUDE_CODE_GLOB_TIMEOUT_SECONDS`、`CLAUDE_CODE_DISABLE_OFFICIAL_MARKETPLACE_AUTOINSTALL`、`CLAUDE_CODE_SYNC_PLUGIN_INSTALL`、`CLAUDE_CODE_SYNC_PLUGIN_INSTALL_TIMEOUT_MS`、`CLAUDE_CODE_AUTO_CONNECT_IDE`、`CLAUDE_CODE_IDE_HOST_OVERRIDE`、`CLAUDE_CODE_IDE_SKIP_VALID_CHECK`、`CLAUDE_CODE_MAX_RETRIES`、`API_TIMEOUT_MS`、`CLAUDE_CODE_OTEL_FLUSH_TIMEOUT_MS`、`CLAUDE_CODE_OTEL_SHUTDOWN_TIMEOUT_MS`、`CLAUDE_ENABLE_STREAM_WATCHDOG`、`CLAUDE_CODE_ENABLE_FINE_GRAINED_TOOL_STREAMING`、`CLAUDE_CODE_DEBUG_LOGS_DIR`、`CLAUDE_CODE_DEBUG_LOG_LEVEL`、`CLAUDE_CODE_ACCESSIBILITY`、`CLAUDE_CODE_SYNTAX_HIGHLIGHT`、`CLAUDE_CODE_RESUME_INTERRUPTED_TURN`、`CLAUDE_CODE_MAX_TOOL_USE_CONCURRENCY`、`CLAUDE_CODE_DISABLE_LEGACY_MODEL_REMAP`、`FALLBACK_FOR_ALL_PRIMARY_MODELS`、`CLAUDE_CODE_GIT_BASH_PATH`、`CLAUDE_AUTO_BACKGROUND_TASKS`、`CLAUDE_AGENT_SDK_DISABLE_BUILTIN_AGENTS`、`CLAUDE_AGENT_SDK_MCP_NO_PREFIX`、`DISABLE_DOCTOR_COMMAND`、`DISABLE_LOGIN_COMMAND`、`DISABLE_LOGOUT_COMMAND`、`DISABLE_UPGRADE_COMMAND`、`DISABLE_EXTRA_USAGE_COMMAND`、`DISABLE_INSTALL_GITHUB_APP_COMMAND`、`CLAUDE_CODE_PLUGIN_CACHE_DIR`、`CLAUDE_CODE_SIMPLE` | ✅ 完成（已将全部 46 个环境变量添加到表格中相关变量附近） |
| 5 | 高 | 版本提升 | 将报告版本徽章从 v2.1.88 更新为 v2.1.89 | ✅ 完成（徽章和标题已在阶段 2.6 中更新） |
| 6 | 中 | 新环境变量 | 添加 `MCP_CONNECTION_NONBLOCKING` 到环境变量表格 — 在 `-p` 模式下设置为 `true` 以跳过 MCP 连接等待。仅 v2.1.89 变更日志，尚未在官方 /en/env-vars 页面上 | ✅ 完成（已在 CLAUDE_AGENT_SDK_MCP_NO_PREFIX 之后添加，附带变更日志注释） |
| 7 | 中 | 所有权边界 | `CLAUDE_CODE_SIMPLE` 在 CLI 启动标志文件中标记为仅启动，但官方 /en/env-vars 页面将其列为可配置。协调所有权 | ✅ 完成（已添加到设置报告环境表格；更新 CLI 文件以交叉引用设置报告） |
| 8 | 中 | 示例更新 | 更新快速参考示例以包含 `showThinkingSummaries`（如果已添加） | ✅ 完成（示例中添加了 showThinkingSummaries: true） |

---

## [2026-04-02 09:24 PM PKT] Claude Code v2.1.90

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 变更类型 + 描述 | 修复 `forceLoginOrgUUID`：类型从 `string` 改为 `string \| string[]`。扩展描述以包含数组行为（接受任何列出的组织而无需预选）、管理设置强制执行（如果账户不在列出的组织中则登录失败）和空数组故障安全行为 | ✅ 完成（类型更新为 string \| 数组，描述扩展了数组行为、管理强制、故障安全语义，示例已更新） |
| 2 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_OAUTH_TOKEN`、`CLAUDE_CODE_OAUTH_REFRESH_TOKEN`、`CLAUDE_CODE_OAUTH_SCOPES` 到通用环境变量表格。全部在官方 /en/env-vars 页面确认 | ✅ 完成（已在 ANTHROPIC_AUTH_TOKEN 之后添加 3 个 OAuth 环境变量） |
| 3 | 高 | 变更描述 + 注释 | 更新 `showThinkingSummaries`：移除"（在 v2.1.89 变更日志中，尚未在官方设置页面上）"注释 — 现已在官方设置页面确认。更新描述以匹配官方："当未设置或为 false（交互模式默认）时，thinking 块被 API 编辑并显示为折叠的存根。编辑只改变你所看到的，不改变模型生成的内容" | ✅ 完成（注释已移除，描述已更新以匹配官方文档） |
| 4 | 高 | 沙箱交叉合并 | 更新 `sandbox.filesystem.allowWrite` 描述以添加"还与来自 `Edit(...)` 允许权限规则的路径合并"。更新 `denyWrite` 以添加"还与来自 `Edit(...)` 拒绝权限规则的路径合并"。更新 `denyRead` 以添加"还与来自 `Read(...)` 拒绝权限规则的路径合并"。在官方设置页面确认 | ✅ 完成（已将交叉合并行为添加到全部 3 个文件系统条目） |
| 5 | 高 | 描述变更 | 简化 `cleanupPeriodDays` 描述：移除矛盾说明，与官方文档对齐，官方文档现在说"最小值为 1，设置为 0 会被拒绝并返回验证错误"。旧行为不再在官方页面上记录 | ✅ 完成（矛盾说明已移除，描述与官方文档对齐，添加了 --no-session-persistence 替代方案） |
| 6 | 高 | 版本提升 | 将报告版本徽章从 v2.1.89 更新为 v2.1.90 | ✅ 完成（徽章、标题版本和标题文本已更新） |
| 7 | 中 | 新环境变量 | 添加 `CLAUDE_CODE_PLUGIN_KEEP_MARKETPLACE_ON_FAILURE` 到环境变量表格 — 在 git pull 失败时保留市场缓存（v2.1.90 变更日志，尚未在官方 /en/env-vars 页面上） | ✅ 完成（已在 CLAUDE_CODE_SYNC_PLUGIN_INSTALL_TIMEOUT_MS 之后添加，附带变更日志注释） |
| 8 | 中 | 钩子重定向计数 | 将重定向文本从"全部 19 个钩子事件"更新为"全部 25 个钩子事件"根据官方钩子页面计数 | ✅ 完成（钩子重定向部分中的计数已更新） |
| 9 | 中 | 所有权边界 | `CLAUDE_CODE_TMPDIR` 在官方 /en/env-vars 页面上列为可通过 `env` 键配置，但 CLI 启动标志报告将其列为仅启动。协调所有权 | ✅ 完成（已添加到设置报告环境表格；更新了 CLI 标志文件以交叉引用设置报告） |

---

## [2026-04-03 08:44 PM PKT] Claude Code v2.1.91

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `disableSkillShellExecution` 到通用设置表格 — 布尔值，禁用技能、自定义斜杠命令和插件命令中的内联 shell 执行。在 v2.1.91 变更日志中确认。尚未在官方设置页面或 JSON schema 中 | ✅ 完成（已在 showThinkingSummaries 之后添加，附带变更日志注释） |
| 2 | 高 | 版本提升 | 将报告版本徽章从 v2.1.90 更新为 v2.1.91 | ✅ 完成（徽章和标题已在阶段 2.6 中更新） |

---

## [2026-04-04 10:48 PM PKT] Claude Code v2.1.92

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `forceRemoteSettingsRefresh` 到通用设置 — 布尔值，仅管理，阻止 CLI 启动直到远程管理设置被新鲜获取（故障安全）。在官方设置页面确认 | ✅ 完成（已添加到通用设置表格，位于 feedbackSurveyRate 之前） |
| 2 | 高 | 缺失环境变量 | 添加 `CLAUDE_REMOTE_CONTROL_SESSION_NAME_PREFIX` 到通用环境变量表格 — 自动生成的远程控制会话名称的前缀，默认为机器主机名。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_ENABLE_TELEMETRY 之前添加） |
| 3 | 中 | 描述变更 | 更新 `disableSkillShellExecution` — 移除"（在 v2.1.91 变更日志中，尚未在官方设置页面上）"注释。现已在官方设置页面确认，附带扩展描述 | ✅ 完成（注释已移除，描述已根据官方文档扩展） |
| 4 | 中 | 描述变更 | 从市场来源类型 `url`、`npm` 和 `file` 中移除"不在官方文档中 — 未验证"标签。官方设置页面现已记录全部 8 种来源类型 | ✅ 完成（未验证注释已移除 — 从 2026-03-31 重复出现，现已解决） |
| 5 | 中 | 描述变更 | 丰富 `cleanupPeriodDays` — 添加"同时控制启动时自动删除孤立子代理工作树的年龄界限"根据官方设置页面 | ✅ 完成（已添加工作树清理详情） |
| 6 | 中 | 描述变更 | 丰富 `disableDeepLinkRegistration` — 添加通过 `%0A` 的多行提示支持根据官方设置页面 | ✅ 完成（已添加多行提示详情） |
| 7 | 中 | 描述变更 | 丰富 `includeGitInstructions` — 更新以包含 git 状态快照和环境变量优先级根据官方设置页面 | ✅ 完成（描述已扩展，包含 git 状态快照和 CLAUDE_CODE_DISABLE_GIT_INSTRUCTIONS 优先级） |
| 8 | 中 | 描述变更 | 丰富 `language` — 添加"同时设置语音听写语言"根据官方设置页面 | ✅ 完成（已添加语音听写详情） |
| 9 | 中 | 描述变更 | 丰富 `allowUnsandboxedCommands` — 根据官方设置页面添加企业策略详情 | ✅ 完成（已扩展故障安全行为和企业用例） |

---

## [2026-04-08 09:51 PM PKT] Claude Code v2.1.96

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_USE_MANTLE`、`ANTHROPIC_BEDROCK_MANTLE_BASE_URL`、`CLAUDE_CODE_SKIP_MANTLE_AUTH` 到通用环境变量表格 — Bedrock Mantle 端点支持（v2.1.94）。全部在官方 /en/env-vars 页面确认 | ✅ 完成（已在相关云提供商变量附近添加） |
| 2 | 高 | 默认值变更 | 更新努力级别部分 — 默认值从"中"改为"高"适用于 API 密钥、Bedrock/Vertex/Foundry、团队和企业用户（v2.1.94）。更新表格默认标记和历史说明 | ✅ 完成（表格更新为高为默认值，历史说明扩展了 v2.1.94 更改） |
| 3 | 高 | 版本提升 | 将报告版本徽章从 v2.1.92 更新为 v2.1.96 | ✅ 完成（徽章、标题版本和标题文本已在阶段 2.6 中更新） |
| 4 | 中 | 过时注释 | 从 `CLAUDE_CODE_PLUGIN_KEEP_MARKETPLACE_ON_FAILURE` 移除"（在 v2.1.90 变更日志中，尚未在官方 env-vars 页面上）" — 现已在官方 /en/env-vars 页面确认。更新描述以匹配官方措辞 | ✅ 完成（注释已移除，描述已根据官方文档更新） |
| 5 | 中 | 描述变更 | 更新 `CLAUDE_CODE_GLOB_HIDDEN` 描述以匹配官方："设置为 `false` 以从 Glob 结果中排除点文件。默认包含。不影响 `@` 文件自动补全、`ls`、Grep 或 Read" | ✅ 完成（描述已根据官方 env-vars 页面重写） |

---

## [2026-04-09 11:39 PM PKT] Claude Code v2.1.97

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `sandbox.network.allowMachLookup` 到沙箱设置表格 — 数组，仅 macOS，XPC/Mach 服务名称，支持尾部 `*` 通配符。在官方设置页面确认 | ✅ 完成（已在沙箱网络子键中 allowManagedDomainsOnly 之后添加） |
| 2 | 高 | 显示与用户体验 | 在状态行配置部分添加 `refreshInterval` 字段 — 可选，每 N 秒重新运行命令，最小值为 1（v2.1.97）。在官方状态行文档中确认 | ✅ 完成（已添加到配置表格及 `padding` 字段，更新了 JSON 示例） |
| 3 | 高 | 显示与用户体验 | 将状态行输入字段表格从 9 个扩展到 30+ 个字段以匹配官方状态行文档。添加 `model.*`、`workspace.*`、`cost.*`、`session_id`、`session_name`、`transcript_path`、`version`、`output_style.name`、`vim.mode`、`agent.name`、`worktree.*` 字段 | ✅ 完成（已根据官方状态行文档从 9 个扩展到 30 个字段） |
| 4 | 高 | 版本提升 | 将报告版本徽章从 v2.1.96 更新为 v2.1.97 | ✅ 完成（徽章和标题已在阶段 2.6 中更新） |
| 5 | 中 | 字段命名 | 修复状态行输入字段表格中的 `current_usage` → `context_window.current_usage` | ✅ 完成（已重命名并添加完整路径和扩展描述） |
| 6 | 中 | 所有权边界 | 添加 `CCR_FORCE_BUNDLE` 到 `claude-cli-startup-flags.md` — `claude --remote` 打包的仅启动变量。在官方 /en/env-vars 页面上但不在任一文件中 | ✅ 完成（已添加到 CLI 启动标志环境变量表格） |
| 7 | 中 | 描述变更 | 更新 `CLAUDE_CODE_GLOB_NO_IGNORE` 描述以匹配官方："设置为 `false` 以使 Glob 工具遵守 `.gitignore` 模式。默认情况下，Glob 返回所有匹配文件，包括被 gitignore 的文件。不影响 `@` 文件自动补全" | ✅ 完成（描述已根据官方 env-vars 页面重写） |
| 8 | 中 | 描述变更 | 更新 `editorMode` 描述 — 移除过时的 `/vim` 引用（在 v2.1.94 中移除），将配置标签从"键绑定模式"改为"编辑器模式"根据官方文档 | ✅ 完成（已移除 /vim 引用，配置标签已更新） |

---

## [2026-04-13 08:10 PM PKT] Claude Code v2.1.101

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_CERT_STORE` 到通用环境变量表格 — TLS 的 CA 证书来源，逗号分隔（`bundled`、`system`）。默认值：`bundled,system`。系统存储需要原生二进制。v2.1.101。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_CLIENT_KEY_PASSPHRASE 之后添加） |
| 2 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_PERFORCE_MODE` 到通用环境变量表格 — 设置为 `1` 以启用 Perforce 感知的写保护。如果目标文件缺少所有者写位，编辑/写入/NotebookEdit 会失败并显示 `p4 edit` 提示。v2.1.98。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_SCRIPT_CAPS 之后添加） |
| 3 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_SCRIPT_CAPS` 到通用环境变量表格 — JSON 对象，限制当设置了 `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB` 时每个会话的脚本调用次数。键是与命令文本匹配的子字符串；值是整数调用限制。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_SUBPROCESS_ENV_SCRUB 之后添加） |
| 4 | 高 | 版本提升 | 将报告版本徽章从 v2.1.97 更新为 v2.1.101 | ✅ 完成（徽章、标题版本和标题文本已在阶段 2.6 中更新） |
| 5 | 中 | 描述变更 | 更新 `disableSkillShellExecution` — 添加 ` ```! `（三重反引号 shell）块语法和"来自用户、项目、插件或附加目录来源"限定符根据官方设置页面 | ✅ 完成（描述已根据官方文档扩展） |
| 6 | 中 | 所有权边界 | 添加 `DISABLE_AUTOUPDATER` 到设置报告环境变量表格 — 在官方 /en/env-vars 页面上列为可通过 `env` 键配置，当前仅在 CLI 启动标志文件中。添加附带 CLI 标志文件的交叉引用 | ✅ 完成（已添加到设置报告，位于 DISABLE_TELEMETRY 之前；CLI 标志文件已更新交叉引用） |

---

## [2026-04-14 11:22 PM PKT] Claude Code v2.1.107

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `viewMode` 到通用设置表格 — 字符串，值 `"default"`、`"verbose"`、`"focus"`。启动时的默认转录视图模式，覆盖粘性 Ctrl+O 选择。在官方设置页面确认 | ✅ 完成（已在通用设置中 showClearContextOnPlanAccept 之后添加） |
| 2 | 高 | 缺失环境变量 | 添加 5 个在官方 /en/env-vars 页面确认的缺失环境变量：`ANTHROPIC_CUSTOM_MODEL_OPTION_SUPPORTED_CAPABILITIES`、`CLAUDE_CODE_DISABLE_VIRTUAL_SCROLL`、`CLAUDE_ENABLE_BYTE_WATCHDOG`、`CLAUDE_CODE_MAX_CONTEXT_TOKENS`、`CLAUDE_CODE_SKIP_PROMPT_HISTORY` | ✅ 完成（已在环境表格中相关变量附近添加） |
| 3 | 高 | 描述变更 | 更新 `disableAllHooks` 描述 — 添加"和任何自定义状态行"根据官方设置页面第 180 行 | ✅ 完成（已在钩子重定向部分内联更新） |
| 4 | 高 | 默认值变更 | 修复全局配置设置表格中 `teammateMode` 默认值从 `"in-process"` 改为 `"auto"`。官方文档将 `auto` 描述为主要行为。在 v2.1.86 文件作用域移动期间退化 | ✅ 完成（默认值已更新为"auto" — 从 2026-03-07 重复出现，v2.1.86 移动导致的回归） |
| 5 | 中 | 描述变更 | 更新 `CLAUDE_STREAM_IDLE_TIMEOUT_MS` 描述 — 区分字节监视器（默认/最小 300000ms）和事件监视器（默认 90000ms）。根据官方 /en/env-vars 页面 | ✅ 完成（描述已扩展双监视器详情，附带指向 CLAUDE_ENABLE_BYTE_WATCHDOG 的交叉引用） |
| 6 | 中 | 注释修复 | 从 `CLAUDE_CODE_GIT_BASH_PATH` 中移除"（仅启动）" — 官方 /en/env-vars 页面将其列为可配置环境 | ✅ 完成（描述已根据官方文档重写，仅启动注释已移除） |
| 7 | 中 | 示例更新 | 在快速参考示例中 `showThinkingSummaries` 之后添加 `viewMode` | ✅ 完成（示例中添加了 "viewMode": "default"） |
| 8 | 中 | 过时注释 | `OTEL_LOG_TOOL_DETAILS` 仍标记为"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上" — 经 10+ 版本和 7 次连续运行确认仍不在官方页面上 | ✋ 搁置（注释准确 — 保持原样等待官方文档更新） |
| 7 | 中 | 所有权边界 | 添加 `CCR_FORCE_BUNDLE` 到设置报告环境变量表格 — 在官方 /en/env-vars 页面上列为可通过 `env` 键配置，当前仅在 CLI 启动标志文件中。添加附带 CLI 标志文件的交叉引用 | ✅ 完成（已添加到设置报告，位于 CLAUDE_CODE_GIT_BASH_PATH 之前；CLI 标志文件已更新交叉引用） |

---

## [2026-04-16 08:25 PM PKT] Claude Code v2.1.110

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 缺失设置 | 添加 `minimumVersion` 到通用设置表格 — 字符串，阻止自动更新器降级到特定版本以下。在官方设置页面确认 | ✅ 完成（已添加到通用设置表格，位于 autoUpdatesChannel 之后） |
| 2 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_TMUX_TRUECOLOR` 到通用环境变量表格 — 设置为 `1` 以允许在 tmux 内使用 24 位真彩色输出。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_CODE_NO_FLICKER 之前添加） |
| 3 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_REMOTE` 到通用环境变量表格 — 只读，在云会话中设置为 `true`。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_REMOTE_CONTROL_SESSION_NAME_PREFIX 之前添加） |
| 4 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_REMOTE_SESSION_ID` 到通用环境变量表格 — 只读，云会话 ID。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 CLAUDE_REMOTE_CONTROL_SESSION_NAME_PREFIX 之前添加） |
| 5 | 高 | 反向环境变量检查 | 将 `ENABLE_PROMPT_CACHING_1H_BEDROCK` 标记为"不在官方文档中 — 未验证"。不再在官方 /en/env-vars 页面上。根据规则 5D | ✅ 完成（已添加未验证注释及弃用说明） |
| 6 | 中 | 新设置（变更日志） | 添加 `autoScrollEnabled` 到通用设置 — 布尔值，在全屏模式中禁用对话自动滚动。仅 v2.1.110 变更日志，尚未在官方设置页面上 | ✅ 完成（已在 feedbackSurveyRate 之前添加，附带变更日志注释） |
| 7 | 中 | 新设置（变更日志） | 添加 `tui` 到通用设置 — 无闪烁渲染模式设置（`/tui fullscreen`）。仅 v2.1.110 变更日志，尚未在官方设置页面上 | ✅ 完成（已在 feedbackSurveyRate 之前添加，附带变更日志注释） |
| 8 | 中 | 新环境变量（变更日志） | 添加 `ENABLE_PROMPT_CACHING_1H` 到环境变量表格 — 1 小时提示缓存 TTL（替换已弃用的 `ENABLE_PROMPT_CACHING_1H_BEDROCK`）。仅 v2.1.108 变更日志，尚未在官方 /en/env-vars 页面上 | ✅ 完成（已在 DISABLE_PROMPT_CACHING 之前添加，附带变更日志注释） |
| 9 | 中 | 新环境变量（变更日志） | 添加 `FORCE_PROMPT_CACHING_5M` 到环境变量表格 — 强制 5 分钟 TTL。仅 v2.1.108 变更日志，尚未在官方 /en/env-vars 页面上 | ✅ 完成（已在 DISABLE_PROMPT_CACHING 之前添加，附带变更日志注释） |
| 10 | 中 | 努力级别表格 | 在努力级别表格中添加 `Max` 行 — 仅 Opus 4.6，在环境变量中有记载但表格中缺失 | ✅ 完成（已作为努力级别表格的第一行添加） |
| 11 | 中 | 沙箱描述 | 添加平台特定说明：`allowUnixSockets`（仅 macOS）、`allowAllUnixSockets`（Linux/WSL2 详情）、`enableWeakerNestedSandbox`（仅 Linux/WSL2） | ✅ 完成（所有 3 个描述均已更新平台特定说明根据官方文档） |
| 12 | 低 | 仅变更日志环境变量 | 考虑添加 `CLAUDE_CODE_ENABLE_AWAY_SUMMARY`（v2.1.108）、`OTEL_LOG_USER_PROMPTS`（v2.1.101）、`OTEL_LOG_TOOL_CONTENT`（v2.1.101）— 均为仅变更日志，不在官方 env-vars 页面上。根据规则 8A 推迟，直到官方文档确认 | ✋ 搁置（推迟 — 仅变更日志，未经官方文档确认） |

---

## [2026-04-18 07:56 PM PKT] Claude Code v2.1.114

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 版本提升 | 将报告版本徽章从 v2.1.110 更新为 v2.1.114，标题"As of v2.1.110" → "As of v2.1.114" | ✅ 完成（徽章和标题文本已更新） |
| 2 | 高 | 新设置 | 添加 `awaySummaryEnabled` 到通用设置表格 — 布尔值，控制是否生成空闲会话摘要（"away summary"）。在官方设置页面确认。与 `CLAUDE_CODE_ENABLE_AWAY_SUMMARY` 环境变量配对 | ✅ 完成（已添加到通用设置表格，位于 `tui` 和 `feedbackSurveyRate` 之间，附带配对说明） |
| 3 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_ENABLE_AWAY_SUMMARY` 到通用环境变量表格 — 选择退出 away summary/会话摘要。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 `FORCE_PROMPT_CACHING_5M` 之后添加 — 重复问题已解决，首次出现 2026-04-16） |
| 4 | 高 | 缺失值 | 在 `effortLevel` 有效值中添加 `xhigh`（第 497 行）— v2.1.111 为 Opus 4.7 引入了 `xhigh`。当前仅列出 `"low"`、`"medium"`、`"high"` | ✅ 完成（描述已更新，包含 `"xhigh"` 值、Opus 4.7 支持和回退行为） |
| 5 | 高 | 努力级别表格 | 在努力级别表格中添加 `xhigh` 行（位于 Max 和 High 之间）— 仅 Opus 4.7，v2.1.111 引入 | ✅ 完成（XHigh 行已添加；默认标记更新为"Opus 4.6/Sonnet 4.6 默认"；说明部分扩展了 v2.1.111 Opus 4.7 上的 xhigh 默认值） |
| 6 | 高 | 文件作用域移动 | 将 `autoScrollEnabled` 从通用设置（第 88 行）移至全局配置设置（`~/.claude.json`）表格 — 官方文档将其列为 `~/.claude.json` 键，而非 `settings.json`。默认 `true`。根据规则 1H。添加到 settings.json 可能触发 schema 验证错误 | ✅ 完成（已从通用设置移除，添加到全局配置设置表格，位于 `autoInstallIdeExtension` 和 `editorMode` 之间，默认 `true`） |
| 7 | 高 | 过时注释 | 从 `tui` 描述（第 89 行）中移除"（在 v2.1.110 变更日志中，尚未在官方设置页面上）" — 现已正式记录。根据官方文档更新描述：`"fullscreen"` 或 `"default"` | ✅ 完成（注释已移除，描述已更新，包含值和 v2.1.110 参考） |
| 8 | 高 | 新设置 | 添加 `externalEditorContext` 到全局配置设置（`~/.claude.json`）表格 — 在官方设置页面的"全局配置设置"部分确认。根据规则 1A | ✅ 完成（已添加到全局配置设置表格，位于 `editorMode` 之后，默认 `true`） |
| 9 | 高 | 过时注释 | 从 `sandbox.network.deniedDomains`（第 388 行）中移除"（不在官方文档中 — 未验证）" — 在 v2.1.113 变更日志中正式添加。根据官方文档更新描述（优先于 `allowedDomains`）。根据规则 10B，经过 11 次连续搁置后解除阻塞 | ✅ 完成（注释已移除，描述已重写，包含优先级和 glob 支持说明 — 重复问题已解决，首次出现 2026-03-05） |
| 10 | 中 | 示例更新 | 更新快速参考示例（第 938–1023 行）以包含 `awaySummaryEnabled`、`tui: "fullscreen"` 和 `effortLevel: "xhigh"`，展示 v2.1.111–v2.1.114 的新增功能 | ✅ 完成（示例中添加了全部 3 个键；`effortLevel` 从 `"medium"` 提升为 `"xhigh"`） |
| 11 | 中 | 标题设置计数 | 验证添加 `awaySummaryEnabled` 和 `externalEditorContext` 后"60+ 设置"计数仍然准确；环境变量计数"175+"仍然合理 | ✅ 完成（两个计数仍在所述范围内 — 净增 +2 设置，+1 环境变量，标题"60+"和"175+"准确） |
| 12 | 低 | 交叉链接 | 为 `CLAUDE_CODE_SIMPLE` 和 `CLAUDE_CODE_EFFORT_LEVEL` 在设置报告和 `claude-cli-startup-flags.md` 之间添加双向交叉链接。当前为单向；启动标志文件链接到设置报告但设置报告没有链接回去 | ✅ 完成（已为两个环境变量添加指向 `./claude-cli-startup-flags.md#environment-variables` 的交叉引用链接） |
| 13 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_DETAILS` 在 11+ 次连续运行后仍标记为"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上"。根据规则 10B：考虑解决 — 通过官方文档确认或移除。当前代理研究确认仍不在官方文档中 | ✋ 搁置（保留 — 从 2026-04-14 v2.1.107 重复出现，注释仍然准确） |
| 14 | 低 | 可疑键重复 | `OTEL_LOG_USER_PROMPTS`、`OTEL_LOG_TOOL_CONTENT` 仍为仅变更日志。根据规则 8A 推迟 | ✋ 搁置（保留 — 从 2026-04-16 v2.1.110 重复出现） |

---

## [2026-04-24 12:27 AM PKT] Claude Code v2.1.118

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 新设置 | 添加 `wslInheritsWindowsSettings` 到仅管理设置（仅 Windows HKLM 注册表 / `C:\Program Files\ClaudeCode\managed-settings.json` — WSL 继承 Windows 策略链）。在官方设置页面确认 | ✅ 完成（已添加到通用设置表格，位于 `forceRemoteSettingsRefresh` 之后，包含完整描述和 v2.1.118 归属） |
| 2 | 高 | 行为变更 | 更新 `autoMode` 描述以记录 `"$defaults"` 标记 — 允许在内置规则旁边添加自定义规则，而非替换它们（v2.1.118）。在官方设置页面确认 | ✅ 完成（描述已更新 — 标记继承行为已在文档中内联记录，附带 v2.1.118 归属） |
| 3 | 高 | 新环境变量（变更日志） | 添加 `DISABLE_UPDATES` 到环境变量表格 — 完全阻止所有更新路径，包括手动 `claude update`（比 `DISABLE_AUTOUPDATER` 更严格）。仅 v2.1.118 变更日志，尚未在官方 /en/env-vars 页面上 | ✅ 完成（已在 `DISABLE_AUTOUPDATER` 之后添加，附带仅变更日志注释） |
| 4 | 中 | 过时可疑键 | 从权限模式表格中移除 `askEdits` 和 `viewOnly` 行 — 官方权限页面仅列出 6 种模式（`default`、`acceptEdits`、`plan`、`auto`、`dontAsk`、`bypassPermissions`）。自 v2.1.74（2026-03-12）以来报告一直将两者标记为"未验证"。根据规则 10B（5+ 次运行搁置升级），通过移除解决 | ✅ 完成（两行均已移除 — 重复问题已解决，首次出现 2026-03-12） |
| 5 | 中 | 过时可疑键 | 从权限键表格中移除 `allow_remote_sessions` — 官方权限页面明确注明"远程控制和网络会话的访问不由管理设置键控制。"管理员通过 Claude Code 管理设置 UI 管理此项。首次添加于 v2.1.74（2026-03-12）作为推测性管理设置；此后从未被记录 | ✅ 完成（已从权限键表格中移除 — 重复问题已解决，首次出现 2026-03-12） |
| 6 | 中 | 行为变更 | 更新 `cleanupPeriodDays` 描述 — v2.1.117 扩展了扫描范围，也清理 `~/.claude/tasks/`、`~/.claude/shell-snapshots/` 和 `~/.claude/backups/`（之前仅转录和孤立工作树） | ✅ 完成（描述已重写以覆盖完整的扫描范围，附带 v2.1.117 归属） |
| 7 | 中 | 努力级别说明 | 在努力级别部分添加 v2.1.117 Pro/Max 默认努力值变更 — Opus 4.6 和 Sonnet 4.6 上 Pro/Max 订阅者的默认值从 `medium` 改为 `high`。当前说明仅提及早期 v2.1.94 对 API 密钥/Bedrock/Vertex/Foundry/团队/企业用户的更改 | ✅ 完成（努力级别说明已扩展 v2.1.117 Pro/Max 对齐语句） |
| 8 | 低 | 示例更新 | 更新快速参考示例以展示 v2.1.118 功能 — `wslInheritsWindowsSettings` 或 `autoMode.soft_deny` 中的 `"$defaults"` 标记 | ✅ 完成（已在快速参考的 autoMode 块中添加 `"soft_deny": ["$defaults", "Never run terraform apply"]`） |
| 9 | 低 | 新环境变量（变更日志） | 考虑添加 `CLAUDE_CODE_FORK_SUBAGENT` 到环境变量表格 — 在外部构建上启用分叉子代理。仅 v2.1.117 变更日志，尚未在官方 /en/env-vars 页面上 | ✅ 完成（已在 `OTEL_LOG_RAW_API_BODIES` 之后添加，附带仅变更日志注释） |
| 10 | 低 | 新环境变量（变更日志） | 考虑添加 `OTEL_LOG_RAW_API_BODIES` 到环境变量表格 — 将完整的 API 请求/响应主体作为 OpenTelemetry 日志事件发出。仅 v2.1.111 变更日志，尚未在官方 /en/env-vars 页面上 | ✅ 完成（已在 `OTEL_LOG_TOOL_DETAILS` 之后添加，附带仅变更日志注释） |
| 11 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_DETAILS` 在 12+ 次连续运行后仍为"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上"。根据规则 10B，推迟等待官方文档更新 | ✋ 搁置（保留 — 从 2026-04-14 v2.1.107 重复出现） |
| 12 | 低 | 可疑键重复 | `OTEL_LOG_USER_PROMPTS`、`OTEL_LOG_TOOL_CONTENT` 仍为仅变更日志。根据规则 8A 推迟 | ✋ 搁置（保留 — 从 2026-04-16 v2.1.110 重复出现） |
| 13 | 无效 | 虚假漂移声明 | `workflow-claude-settings-agent` 报告 `sandbox.allowUnsandboxedCommands` 默认值错误（声称文档说 `false`）。经与官方设置页面验证 — 记录的默认值为 **`true`**。报告保持正确 | ❌ 无效（代理报告与官方文档在重新验证后矛盾） |

---

## [2026-04-26 01:10 PM PKT] Claude Code v2.1.119

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 版本提升 | 将报告版本徽章从 v2.1.118 更新为 v2.1.119，标题"As of v2.1.118" → "As of v2.1.119" | ✅ 完成（徽章、标题版本和标题文本已在阶段 2.6 中更新） |
| 2 | 高 | 新设置 | 添加 `prUrlTemplate` 到归属设置表格 — 字符串，URL 模板，控制提交归属中的 PR 徽章如何链接到 PR UI。适用于自托管 GitLab/Bitbucket/GitHub Enterprise 实例。在 v2.1.119 变更日志中确认 | ✅ 完成（已添加到归属设置表格，位于 `attribution.pr` 和 `includeCoAuthoredBy` 之间，附带 v2.1.119 归属和自托管用例） |
| 3 | 高 | 缺失环境变量 | 添加 `CLAUDE_CODE_HIDE_CWD` 到通用环境变量表格 — 设置为 `1` 以隐藏启动徽标横幅中的当前工作目录。在屏幕录制或共享会话中 CWD 路径敏感时有用。在 v2.1.119 变更日志中确认 | ✅ 完成（已在环境变量表格中 `CLAUDE_CODE_DISABLE_MOUSE` 之后添加，与其他 UI/显示变量分组） |
| 4 | 高 | 行为变更 | 更新 `auto` 权限模式描述（第 247 行）— 移除过时的 `--enable-auto-mode` 标志引用（该标志已在 v2.1.111 中移除）。根据官方权限文档，当前描述为："自动批准工具调用，并进行后台安全检查，验证操作是否与您的请求一致。目前为研究预览。"自动模式现已在默认的 Shift+Tab 循环中 | ✅ 完成（描述已使用官方措辞重写；移除了 `--enable-auto-mode` 标志引用；注明了自 v2.1.111 起 Shift+Tab 循环包含以及 `--permission-mode auto` 作为当前入口点） |
| 5 | 中 | 行为变更 | 更新插件设置中 `blockedMarketplaces` 的描述 — 注明 v2.1.119 对 `hostPattern` 和 `pathPattern` 匹配的强制执行。被阻止的源现在在下载触及文件系统之前被正确拒绝 | ✅ 完成（描述已扩展，包含 hostPattern/pathPattern 匹配器和 v2.1.119 预下载强制详情） |
| 6 | 中 | 语音设置扩展 | 将 `voiceEnabled`（布尔值，第 81 行）扩展为根据 v2.1.118 记录完整的 `voice` 对象 — 支持 `enabled`（布尔值）、`mode`（`"hold"` 或 `"tap"`）和 `autoSubmit`（布尔值）。保留 `voiceEnabled` 作为旧版别名，并标记为已弃用 | ✅ 完成（已添加新的 `voice` 对象行，包含全部 3 个字段；`voiceEnabled` 行更新为已弃用的旧版别名，指向 `voice` 对象） |
| 7 | 中 | 新子命令 | 在有用命令表格中添加 `claude plugin tag` — 在 v2.1.118 中添加，用于在市场中对插件版本打标签 | ✅ 完成（已在有用命令表格中的 `/plugin` 之后添加，附带 v2.1.118 归属和从市场仓库运行的使用说明） |
| 8 | 低 | 来源 URL 漂移 | `https://json.schemastore.org/claude-code-settings.json` 现在 301 重定向到 `https://www.schemastore.org/claude-code-settings.json`。v2.1.74 #4 明确将其修复为另一方向。来源仍通过重定向解析 — 决定是否切换或保留重定向 | ❌ 无效（URL 仍通过 301 重定向正确解析；切换会导致与 v2.1.74 #4 修复的来回波动，没有功能上的好处。仅在 schemastore 弃用重定向时重新评估） |
| 9 | 低 | MCP OAuth 说明 | 在 MCP 服务器部分添加简短的 MCP OAuth RFC 9728 说明 — 在 v2.1.111 中添加。信息性，非设置键 | ✅ 完成（已在 MCP 设置表格上方添加块引用标注，包含 RFC 9728 链接、`/.well-known/oauth-protected-resource` 发现端点，以及符合规范的服务器不再需要 `apiKeyHelper`/`headersHelper` 的说明） |
| 10 | 低 | 快速参考更新 | 一旦新键添加完成，在归属块之后的快速参考示例中添加 `prUrlTemplate` | ✅ 完成（已在示例中的 `attribution` 块之后添加 `"prUrlTemplate": "https://gitlab.example.com/{owner}/{repo}/-/merge_requests/{number}"`） |
| 11 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_DETAILS` 在 13+ 次连续运行后仍为"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上"。根据规则 10B，推迟等待官方文档更新 | ✋ 搁置（保留 — 从 2026-04-14 v2.1.107 重复出现） |
| 12 | 低 | 可疑键重复 | `OTEL_LOG_USER_PROMPTS`、`OTEL_LOG_TOOL_CONTENT` 仍为仅变更日志。根据规则 8A 推迟 | ✋ 搁置（保留 — 从 2026-04-16 v2.1.110 重复出现） |
| 13 | 无效 | 虚假漂移声明 | `claude-code-guide` 代理报告 `attribution.pr` 是新的 v2.1.119 设置。经与当前报告（第 149 行）验证 — 已在归属设置表格中记录 | ❌ 无效（已在报告中） |
| 14 | 无效 | 虚假漂移声明 | `claude-code-guide` 代理声称 `sandbox.network.deniedDomains` 是在 v2.1.116 中添加的。工作流代理和报告（第 386 行）均确认 v2.1.113 引入（匹配最近的 v2.1.114 变更日志条目，该条目解决了其先前的未验证状态）。保留报告值 | ❌ 无效（代理与特定报告代理 + 先前变更日志矛盾） |

---

## [2026-04-29 12:49 AM PKT] Claude Code v2.1.121

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 版本提升 | 将报告版本徽章从 v2.1.119 → v2.1.121，标题"As of v2.1.119" → "As of v2.1.121" | ✅ 完成（徽章在阶段 2.6 中更新，标题文本更新为 v2.1.121） |
| 2 | 高 | 新设置 | 添加 `sshConfigs` 到新的工作空间与团队子部分（对象[]，必需：`id`/`name`/`sshHost`；可选：`sshPort`/`sshIdentityFile`/`startDirectory`）。在桌面版中提供 SSH 连接下拉菜单。根据官方设置页面第 14 节 | ✅ 完成（已添加新的工作空间与团队子部分，包含键表格、字段参考表格和 JSON 示例） |
| 3 | 高 | 新 MCP 选项 | 添加 `alwaysLoad` 到 MCP 设置 — 每个服务器的布尔选项，免除服务器工具搜索延迟；适用于所有服务器类型；需要 v2.1.121+。每工具变体通过 `_meta: {"anthropic/alwaysLoad": true}`。在官方 MCP 页面上确认 | ✅ 完成（已在 MCP 服务器下添加新的"每个服务器工具加载"子部分，包含理由、JSON 示例和每工具 `_meta` 变体） |
| 4 | 高 | 状态行字段 | 添加 `effort.level`（low/medium/high/xhigh/max）和 `thinking.enabled` 到状态行输入字段表格（v2.1.121）。在官方状态行文档中确认 | ✅ 完成（两个字段已在 `agent.name` 行之后添加，附带 v2.1.121 归属） |
| 5 | 高 | 文件作用域迁移 | 将 `autoScrollEnabled`、`editorMode`、`showTurnDuration`、`teammateMode`、`terminalProgressBarEnabled` 从全局配置设置（`~/.claude.json`）表格移至主显示设置表格（settings.json）。添加历史说明："v2.1.119 之前的版本将这些存储在 `~/.claude.json` 中"。逆转了 v2.1.78/v2.1.86/v2.1.107/v2.1.114 的规则 1H 发现 — 官方文档现在明确将它们在"可用设置"下列出，附带历史说明 | ✅ 完成（5 个键已添加到显示设置表格，附带每个键的历史说明；已从全局配置设置表格中移除；在全局配置设置序言中添加了 v2.1.119 迁移标注） |
| 6 | 高 | 缺失环境变量 | 添加 `AI_AGENT` 到环境变量表格 — 由 Claude Code 注入子进程的环境变量（类似于 `CLAUDECODE`）。仅 v2.1.120 变更日志 — 相应注释 | ✅ 完成（已在 `CLAUDECODE` 行之后添加，附带仅变更日志注释） |
| 7 | 高 | 缺失环境变量 | 添加 `OTEL_LOG_USER_PROMPTS` 到环境变量表格 — 控制 OTel LLM 请求跨度中的 `user_system_prompt` 字段。v2.1.121 变更日志。**重复问题**（首次出现 2026-04-16 v2.1.110）— 曾根据规则 8A 推迟，但现在根据新的 v2.1.121 变更日志提及而可操作 | ✅ 完成（已在 `OTEL_LOG_RAW_API_BODIES` 之后添加，附带仅变更日志注释 — 重复问题已解决，首次出现 2026-04-16） |
| 8 | 中 | 权限行为 | 在权限部分添加 v2.1.121 `--dangerously-skip-permissions` 排除说明。重新验证官方权限模式文档：变化在于，在 bypassPermissions 下，对 `.claude/commands/`、`.claude/agents/`、`.claude/skills/` 和 `.claude/worktrees/` 的写入**豁免**于受保护路径提示 — 即这些子目录现为自动批准，与代理最初构想的相反 | ✅ 完成（描述已添加到权限模式表格中的 `bypassPermissions` 行，根据官方文档使用更正的框架 — 豁免而非限制） |
| 9 | 中 | 描述变更 | 更新 `language` 设置描述 — v2.1.121 也将语言应用于终端标签页标题 | ✅ 完成（终端标签页标题行为已附加到 `language` 描述，附带 v2.1.121 归属） |
| 10 | 中 | 有用命令 | 更新 `/effort` 行以包含 `xhigh` 值（当前仅列出 `low`/`medium`/`high`） | ✅ 完成（`/effort` 行现已列出 `low`、`medium`、`high`、`xhigh`（仅 Opus 4.7，v2.1.111）和 `max`（仅 Opus 4.6）） |
| 11 | 低 | 技能变量说明 | 添加简短的 `${CLAUDE_EFFORT}` 技能模板变量说明（v2.1.120）— 信息性，严格来说不是设置键 | ✅ 完成（已添加到努力级别说明部分，作为"技能模板变量"语句，附带 v2.1.120 归属） |
| 12 | 低 | 示例更新 | 更新快速参考示例以展示 v2.1.121 功能（MCP `alwaysLoad`、`sshConfigs` 或新的状态行字段） | ✅ 完成（在快速参考示例中添加了带有 `alwaysLoad: true` 的 `mcpServers` 块和 `sshConfigs` 块） |
| 13 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_DETAILS` 在 14+ 次连续运行后仍为"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上"。根据规则 10B，推迟等待官方文档更新 | ✋ 搁置（保留 — 从 2026-04-14 v2.1.107 重复出现） |
| 14 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_CONTENT` 仍为仅变更日志。根据规则 8A 推迟 | ✋ 搁置（保留 — 从 2026-04-16 v2.1.110 重复出现） |
| 15 | 高 | 链接失效 | 修复第 237 行和第 238 行的两个 `[auto mode](/en/permission-modes#eliminate-prompts-with-auto-mode)` 链接（在 `autoMode` 和 `disableAutoMode` 描述中）— 相对路径缺少域名前缀。替换为 `https://code.claude.com/docs/en/permission-modes#eliminate-prompts-with-auto-mode`。锚点在官方权限模式页面上验证有效 | ✅ 完成（两个链接均已更新为绝对 `https://code.claude.com/docs/en/permission-modes#eliminate-prompts-with-auto-mode` URL） |

---

## [2026-05-01 03:29 PM PKT] Claude Code v2.1.126

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | 高 | 版本提升 | 将报告版本徽章从 v2.1.121 → v2.1.126，标题"As of v2.1.121" → "As of v2.1.126" | ✅ 完成（徽章在阶段 2.6 中更新，主体标题文本更新为 v2.1.126） |
| 2 | 高 | 新设置 | 添加 `preferredNotifChannel` 到显示设置表格 — 字符串，默认 `"auto"`，值：`"auto"`、`"terminal_bell"`、`"iterm2"`、`"iterm2_with_bell"`、`"kitty"`、`"ghostty"`、`"notifications_disabled"`。任务完成和权限提示通知的方法。在官方设置页面确认 | ✅ 完成（已添加到显示设置表格，位于 `terminalProgressBarEnabled` 之后，包含完整枚举值、默认值和 `/en/terminal-config` 交叉链接） |
| 3 | 高 | 新环境变量 | 添加 `ANTHROPIC_BEDROCK_SERVICE_TIER` 到环境变量表格 — Bedrock 服务层级（`default`、`flex` 或 `priority`）；作为 `X-Amzn-Bedrock-Service-Tier` 头发送。v2.1.122。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 `ANTHROPIC_BEDROCK_MANTLE_BASE_URL` 之后添加，附带 v2.1.122 归属和 `/en/amazon-bedrock#service-tiers` 交叉链接） |
| 4 | 高 | 新环境变量 | 添加 `CLAUDE_CODE_PROVIDER_MANAGED_BY_HOST` 到环境变量表格 — 由嵌入 Claude Code 的主机平台设置；当设置时，settings.json 中的提供商/认证环境变量被忽略；遥测遵循标准 `DISABLE_TELEMETRY` 选择退出而非在 Bedrock/Vertex/Foundry 上自动禁用。v2.1.126。在官方 /en/env-vars 页面确认 | ✅ 完成（已在 `ANTHROPIC_BEDROCK_SERVICE_TIER` 之后添加，包含完整描述、忽略变量列表和 v2.1.126 归属） |
| 5 | 中 | 权限模式 | 更新 `bypassPermissions` 描述（第 248 行）— v2.1.126 将豁免扩展为也绕过对 `.claude/`、`.git/`、`.vscode/` 和 shell 配置文件的写入。灾难性删除命令仍会提示。基于 v2.1.121 的 `.claude/commands/`、`.claude/agents/`、`.claude/skills/`、`.claude/worktrees/` 豁免 | ✅ 完成（描述已扩展 v2.1.126 对 `.claude/`、`.git/`、`.vscode/` 和 shell 配置文件的豁免；保留了灾难性删除安全网） |
| 6 | 中 | 描述变更 | 丰富 `defaultShell` 描述 — v2.1.126：当 PowerShell 启用时（`CLAUDE_CODE_USE_POWERSHELL_TOOL=1`），它被视为**主** shell。v2.1.120：当 Git for Windows 不可用时，PowerShell 是回退 shell。同时注明 v2.1.126 PowerShell 7 检测（Microsoft Store、无 PATH 的 MSI、.NET 全局工具） | ✅ 完成（描述已丰富 v2.1.120 回退行为、v2.1.126 主 shell 切换和 PowerShell 7 检测来源） |
| 7 | 低 | spinnerTipsOverride 说明 | 可选地丰富 `spinnerTipsOverride.excludeDefault` 描述（第 580 行），附带 v2.1.121 详情"抑制基于时间的旋转提示"。当前根据官方设置页面措辞准确，但缺少 v2.1.121 变更日志细化 | ✅ 完成（描述已扩展 `excludeDefault` 语义，根据官方文档和 v2.1.121 基于时间提示抑制细化） |
| 8 | 低 | /config 持久化说明 | 在设置层级部分添加简短的 `/config` 现在将更改持久化到 `~/.claude/settings.json`（v2.1.126）的说明。信息性，非新键 | ✅ 完成（已在设置层级下的 v2.1.75 Windows 路径说明之后添加 v2.1.126 `> 说明` 块） |
| 9 | 低 | 示例更新 | 更新快速参考示例以展示 v2.1.122–v2.1.126 功能 — `preferredNotifChannel` 和一个 `ANTHROPIC_BEDROCK_SERVICE_TIER` 环境变量示例 | ✅ 完成（已在 `prefersReducedMotion` 之后添加 `"preferredNotifChannel": "terminal_bell"`，并在 `env` 块中添加 `"ANTHROPIC_BEDROCK_SERVICE_TIER": "priority"`） |
| 10 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_DETAILS` 在 16+ 次连续运行后仍为"在 v2.1.85 变更日志中，尚未在官方 env-vars 页面上"。根据规则 10B，推迟等待官方文档更新 | ✋ 搁置（保留 — 从 2026-04-14 v2.1.107 重复出现） |
| 11 | 低 | 可疑键重复 | `OTEL_LOG_TOOL_CONTENT` 仍为仅变更日志。根据规则 8A 推迟 | ✋ 搁置（保留 — 从 2026-04-16 v2.1.110 重复出现） |
| 12 | 无效 | 虚假漂移声明 | `workflow-claude-settings-agent` 报告 `autoSummaryEnabled` 是独立于 `awaySummaryEnabled` 的设置（高置信度声明）。直接与官方设置页面验证 — `autoSummaryEnabled` **不存在**；仅记录了 `awaySummaryEnabled` | ❌ 无效（代理与直接文档验证矛盾） |
| 13 | 无效 | 虚假漂移声明 | `workflow-claude-settings-agent` 声称 `Agent` 权限规则语法应为 `Agent(agent:name)` 并带有 `agent:` 前缀。与官方设置页面验证 — 仅引用 `Agent` 规则，未显示 `agent:` 前缀语法。报告现有的 `Agent(name)` 形式与既定惯例一致；没有来源确认前缀变体 | ❌ 无效（没有来源验证的证据支持 `agent:` 前缀） |
| 14 | 无效 | 虚假漂移声明 | `workflow-claude-settings-agent` 标记核心配置中 `model` 默认值（`"default"`）和 `language` 默认值（`"english"`）在外观上错误，因为官方文档显示 `-`。报告的值是描述未设置时行为的说明性占位符；翻转为 `-` 会丢失信息，没有任何面向用户的好处 | ❌ 无效（外观重新验证，无面向用户的好处） |
