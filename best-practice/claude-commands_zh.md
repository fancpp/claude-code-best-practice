# 命令最佳实践

![Last Updated](https://img.shields.io/badge/Last_Updated-May%2001%2C%202026%203%3A31%20PM%20PKT-white?style=flat&labelColor=555) ![Version](https://img.shields.io/badge/Claude_Code-v2.1.126-blue?style=flat&labelColor=555)<br>
[![Implemented](https://img.shields.io/badge/Implemented-2ea44f?style=flat)](../implementation/claude-commands-implementation.md)

Claude Code 命令 — 前置元数据字段和官方内置斜杠命令。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code Best Practice</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 前置元数据字段（15个）

| 字段 | 类型 | 必需 | 描述 |
|-------|------|----------|-------------|
| `name` | string | 否 | 显示名称和 `/slash-command` 标识符。省略时默认为目录名称 |
| `description` | string | 推荐 | 命令的功能描述。显示在自动补全中，供 Claude 用于自动发现 |
| `when_to_use` | string | 否 | 关于 Claude 何时应调用该技能的额外上下文 — 触发短语或示例请求。附加到 `description` 中，计入 1,536 字符上限 |
| `argument-hint` | string | 否 | 自动补全时显示的提示（例如 `[issue-number]`、`[filename]`） |
| `arguments` | string/list | 否 | 命令内容中 `$name` 替换的命名位置参数。接受空格分隔的字符串或 YAML 列表 — 名称按顺序映射到参数位置 |
| `disable-model-invocation` | boolean | 否 | 设置为 `true` 可防止 Claude 自动调用此命令 |
| `user-invocable` | boolean | 否 | 设置为 `false` 可从 `/` 菜单中隐藏 — 命令仅作为背景知识 |
| `paths` | string/list | 否 | 限制何时激活此技能的 Glob 模式。接受逗号分隔的字符串或 YAML 列表。设置后，Claude 仅在处理匹配模式的文件时自动加载该技能 |
| `allowed-tools` | string | 否 | 此命令激活时无需权限提示即可使用的工具 |
| `model` | string | 否 | 运行此命令时使用的模型（例如 `haiku`、`sonnet`、`opus`） |
| `effort` | string | 否 | 调用时覆盖模型的思考深度级别（`low`、`medium`、`high`、`max`） |
| `context` | string | 否 | 设置为 `fork` 可在隔离的子代理上下文中运行命令 |
| `agent` | string | 否 | 当 `context: fork` 设置时的子代理类型（默认：`general-purpose`） |
| `shell` | string | 否 | `` !`command` `` 代码块的 Shell — 接受 `bash`（默认）或 `powershell`。需要 `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` |
| `hooks` | object | 否 | 作用于该命令的生命周期钩子 |

---

## ![Official](../!/tags/official.svg) **（75个）**

| # | 命令 | 标签 | 描述 |
|---|---------|-----|-------------|
| 1 | `/login` | ![Auth](https://img.shields.io/badge/Auth-2980B9?style=flat) | 登录您的 Anthropic 账户 |
| 2 | `/logout` | ![Auth](https://img.shields.io/badge/Auth-2980B9?style=flat) | 退出您的 Anthropic 账户 |
| 3 | `/setup-bedrock` | ![Auth](https://img.shields.io/badge/Auth-2980B9?style=flat) | 通过交互式向导配置 Amazon Bedrock 认证、区域和模型固定。仅在设置 `CLAUDE_CODE_USE_BEDROCK=1` 时可见。首次使用 Bedrock 的用户也可以从登录页面进入此向导 |
| 4 | `/setup-vertex` | ![Auth](https://img.shields.io/badge/Auth-2980B9?style=flat) | 通过交互式向导配置 Google Vertex AI 认证、项目、区域和模型固定。仅在设置 `CLAUDE_CODE_USE_VERTEX=1` 时可见。首次使用 Vertex AI 的用户也可以从登录页面进入此向导 |
| 5 | `/upgrade` | ![Auth](https://img.shields.io/badge/Auth-2980B9?style=flat) | 打开升级页面以切换到更高的计划层级 |
| 6 | `/color [color\|default]` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 设置当前会话的提示栏颜色。可用颜色：`red`、`blue`、`green`、`yellow`、`purple`、`orange`、`pink`、`cyan`。使用 `default` 重置 |
| 7 | `/config` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 打开设置界面以调整主题、模型、输出样式和其他偏好。别名：`/settings` |
| 8 | `/focus` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 切换焦点视图，仅显示最后一个提示、工具调用摘要和最终响应。有助于减少长时间会话中的视觉噪音。仅在全屏渲染中可用 |
| 9 | `/keybindings` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 打开或创建您的按键绑定配置文件 |
| 10 | `/permissions` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 管理工具权限的允许、询问和拒绝规则。打开交互式对话框，您可以按范围查看规则、添加或删除规则、管理工作目录以及审查最近的自动模式拒绝。别名：`/allowed-tools` |
| 11 | `/privacy-settings` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 查看和更新您的隐私设置。仅 Pro 和 Max 计划订阅者可用 |
| 12 | `/sandbox` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 切换沙箱模式。仅在支持的平台上可用 |
| 13 | `/statusline` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 配置 Claude Code 的状态行。描述您想要的内容，或不带参数运行以自动从您的 Shell 提示符配置 |
| 14 | `/stickers` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 订购 Claude Code 贴纸 |
| 15 | `/terminal-setup` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 配置终端的 Shift+Enter 和其他快捷键的按键绑定。仅在需要此功能的终端中可见，如 VS Code、Cursor、Windsurf、Alacritty 或 Zed |
| 16 | `/theme` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 更改颜色主题。包括浅色和深色变体、色盲无障碍（daltonized）主题、使用终端调色板的 ANSI 主题、跟随终端浅色/深色模式的"自动（匹配终端）"选项，以及从 `~/.claude/themes/` 或插件加载的自定义主题。选择"新建自定义主题…"来创建您自己的主题 |
| 17 | `/tui [default\|fullscreen]` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 设置终端 UI 渲染器并重新启动 Claude Code，保持当前对话不变。`default` 使用内联渲染；`fullscreen` 使用备用屏幕 TUI |
| 18 | `/voice [hold\|tap\|off]` | ![Config](https://img.shields.io/badge/Config-F39C12?style=flat) | 切换语音听写，或在特定模式下启用。需要 Claude.ai 账户 |
| 19 | `/context` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | 以彩色网格可视化当前上下文使用情况。显示针对上下文密集型工具的优化建议、内存膨胀和容量警告 |
| 20 | `/cost` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | `/usage` 的别名 |
| 21 | `/extra-usage` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | 配置额外使用量，以便在达到速率限制时继续工作 |
| 22 | `/insights` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | 生成分析您 Claude Code 会话的报告，包括项目领域、交互模式和摩擦点 |
| 23 | `/stats` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | `/usage` 的别名。在统计选项卡上打开 |
| 24 | `/status` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | 打开设置界面（状态选项卡），显示版本、模型、账户和连接状态。可在 Claude 响应时工作，无需等待当前响应完成 |
| 25 | `/usage` | ![Context](https://img.shields.io/badge/Context-8E44AD?style=flat) | 显示会话成本、计划使用限制和活动统计。`/cost` 和 `/stats` 是别名 |
| 26 | `/doctor` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 诊断并验证您的 Claude Code 安装和设置。结果以状态图标显示。按 `f` 让 Claude 修复任何报告的问题 |
| 27 | `/feedback [report]` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 提交关于 Claude Code 的反馈。别名：`/bug` |
| 28 | `/heapdump` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 将 JavaScript 堆快照和内存分解写入 `~/Desktop`，用于诊断高内存使用情况。在提交关于内存增长的错误报告时很有用 |
| 29 | `/help` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 显示帮助和可用命令 |
| 30 | `/powerup` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 通过快速交互式课程和动画演示发现 Claude Code 功能 |
| 31 | `/release-notes` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 在交互式版本选择器中查看变更日志。选择特定版本查看其发布说明，或选择显示所有版本 |
| 32 | `/tasks` | ![Debug](https://img.shields.io/badge/Debug-E74C3C?style=flat) | 列出和管理后台任务。别名：`/bashes` |
| 33 | `/copy [N]` | ![Export](https://img.shields.io/badge/Export-7F8C8D?style=flat) | 将最后一条助手响应复制到剪贴板。传入数字 `N` 可复制倒数第 N 条响应：`/copy 2` 复制倒数第二条。当存在代码块时，显示交互式选择器以选择单个块或完整响应。在选择器中按 `w` 可将选择写入文件而不是剪贴板，这在使用 SSH 时很有用 |
| 34 | `/export [filename]` | ![Export](https://img.shields.io/badge/Export-7F8C8D?style=flat) | 将当前对话导出为纯文本。提供文件名时，直接写入该文件。不提供时，打开对话框以复制到剪贴板或保存到文件 |
| 35 | `/agents` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理代理配置 |
| 36 | `/chrome` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 配置 Chrome 中的 Claude 设置 |
| 37 | `/hooks` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 查看工具事件的钩子配置 |
| 38 | `/ide` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 IDE 集成并显示状态 |
| 39 | `/mcp` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 MCP 服务器连接和 OAuth 认证 |
| 40 | `/plugin` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 管理 Claude Code 插件 |
| 41 | `/reload-plugins` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 重新加载所有活动插件以应用待定更改，无需重新启动。报告每个重新加载组件的计数，并标记任何加载错误 |
| 42 | `/skills` | ![Extensions](https://img.shields.io/badge/Extensions-16A085?style=flat) | 列出可用技能。按 `t` 可按令牌数量排序 |
| 43 | `/memory` | ![Memory](https://img.shields.io/badge/Memory-3498DB?style=flat) | 编辑 `CLAUDE.md` 记忆文件，启用或禁用自动记忆，以及查看自动记忆条目 |
| 44 | `/effort [low\|medium\|high\|xhigh\|max\|auto]` | ![Model](https://img.shields.io/badge/Model-E67E22?style=flat) | 设置模型的思考深度级别。可用级别取决于模型，包括 `low`、`medium`、`high`、`xhigh` 和 `max`（仅限会话）。不带参数时，打开交互式滑块选择级别。`auto` 重置为模型默认值。立即生效，无需等待当前响应完成 |
| 45 | `/fast [on\|off]` | ![Model](https://img.shields.io/badge/Model-E67E22?style=flat) | 打开或关闭快速模式 |
| 46 | `/model [model]` | ![Model](https://img.shields.io/badge/Model-E67E22?style=flat) | 选择或更改 AI 模型。对于支持的模型，使用左/右箭头调整思考深度级别。更改立即生效，无需等待当前响应完成。在已有先前输出的对话中切换时，Claude 会在应用更改前发出警告 |
| 47 | `/passes` | ![Model](https://img.shields.io/badge/Model-E67E22?style=flat) | 与朋友分享一周免费的 Claude Code。仅当您的账户符合条件时可见 |
| 48 | `/plan [description]` | ![Model](https://img.shields.io/badge/Model-E67E22?style=flat) | 直接从提示进入计划模式。传入可选的描述以进入计划模式并立即开始该任务，例如 `/plan fix the auth bug` |
| 49 | `/ultraplan <prompt>` | ![Model](https://img.shields.io/badge/Model-E67E22?style=flat) | 在 ultraplan 会话中起草计划，在浏览器中审阅，然后远程执行或将其发回终端 |
| 50 | `/add-dir <path>` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 为当前会话添加文件访问的工作目录。大部分 `.claude/` 配置不会从添加的目录中发现 |
| 51 | `/diff` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 打开交互式差异查看器，显示未提交的更改和每轮差异。使用左/右箭头可在当前 git diff 和单个 Claude 轮次之间切换，上/下浏览文件 |
| 52 | `/init` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 使用 `CLAUDE.md` 指南初始化项目。设置 `CLAUDE_CODE_NEW_INIT=1` 可使用交互式流程，该流程还会逐步引导完成技能、钩子和个人记忆文件 |
| 53 | `/review` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 本地审查当前会话中的 Pull Request。如需更深入的基于云的审查，请参见 `/ultrareview` |
| 54 | `/security-review` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 分析当前分支上待定的更改是否存在安全漏洞。审查 git diff 并识别诸如注入、认证问题和数据暴露等风险 |
| 55 | `/team-onboarding` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 从您的 Claude Code 使用历史生成团队入门指南。分析过去 30 天的会话、命令和 MCP 服务器使用情况 |
| 56 | `/ultrareview [PR]` | ![Project](https://img.shields.io/badge/Project-27AE60?style=flat) | 在云沙箱中运行对给定 Pull Request 的深度多代理代码审查。生成带有优先排序发现的结构化审查；补充本地的 `/review` 命令 |
| 57 | `/autofix-pr [prompt]` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 启动 Web 会话上的 Claude Code，监视当前分支的 PR，并在 CI 失败或审阅者留下评论时推送修复。通过 `gh pr view` 从检出的分支检测打开的 PR；要监视不同的 PR，先检出其分支。需要 `gh` CLI 和 Web 版 Claude Code 的访问权限 |
| 58 | `/desktop` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 在 Claude Code Desktop 应用中继续当前会话。仅限 macOS 和 Windows。别名：`/app` |
| 59 | `/install-github-app` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 为仓库设置 Claude GitHub Actions 应用。引导您选择仓库并配置集成 |
| 60 | `/install-slack-app` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 安装 Claude Slack 应用。打开浏览器完成 OAuth 流程 |
| 61 | `/mobile` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 显示下载 Claude 移动应用的二维码。别名：`/ios`、`/android` |
| 62 | `/remote-control` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 使此会话可从 claude.ai 进行远程控制。别名：`/rc` |
| 63 | `/remote-env` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 配置使用 `--remote` 启动的 Web 会话的默认远程环境 |
| 64 | `/schedule [description]` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 创建、更新、列出或运行例程。Claude 以对话方式引导您完成设置。别名：`/routines` |
| 65 | `/teleport` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 将 Web 会话上的 Claude Code 拉入此终端：打开选择器，然后获取分支和对话。也可作为 `/tp` 使用。需要 claude.ai 订阅 |
| 66 | `/web-setup` | ![Remote](https://img.shields.io/badge/Remote-5D6D7E?style=flat) | 使用本地 `gh` CLI 凭据将您的 GitHub 账户连接到 Web 上的 Claude Code。如果 GitHub 未连接，`/schedule` 会自动提示此操作 |
| 67 | `/branch [name]` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 在当前对话的此点创建一个分支。别名：`/fork`。当设置 `CLAUDE_CODE_FORK_SUBAGENT` 时，`/fork` 改为生成一个分支子代理，不再作为此命令的别名 |
| 68 | `/btw <question>` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 快速提问一个旁侧问题，不添加到对话中 |
| 69 | `/clear` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 以空上下文开始新对话。之前的对话在 `/resume` 中仍然可用。要在继续同一对话的同时释放上下文，请改用 `/compact`。别名：`/reset`、`/new` |
| 70 | `/compact [instructions]` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 压缩对话，可选择附带焦点指令 |
| 71 | `/exit` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 退出 CLI。别名：`/quit` |
| 72 | `/recap` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 按需生成当前会话的单行摘要，不影响正在进行的对话 |
| 73 | `/rename [name]` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 重命名当前会话并在提示栏上显示名称。不提供名称时，从对话历史自动生成 |
| 74 | `/resume [session]` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 按 ID 或名称恢复对话，或打开会话选择器。别名：`/continue` |
| 75 | `/rewind` | ![Session](https://img.shields.io/badge/Session-4A90D9?style=flat) | 将对话和/或代码回退到之前的一点，或从选定的消息生成摘要。参见检查点机制。别名：`/checkpoint`、`/undo` |

诸如 `/debug` 之类的捆绑技能也可能出现在斜杠命令菜单中，但它们不是内置命令。

---

## 来源

- [Claude Code Slash Commands](https://code.claude.com/docs/en/slash-commands)
- [Claude Code Interactive Mode](https://code.claude.com/docs/en/interactive-mode)
- [Claude Code CHANGELOG](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
