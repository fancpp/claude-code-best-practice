# 技能最佳实践

![Last Updated](https://img.shields.io/badge/Last_Updated-May%2001%2C%202026%203%3A30%20PM%20PKT-white?style=flat&labelColor=555) ![Version](https://img.shields.io/badge/Claude_Code-v2.1.126-blue?style=flat&labelColor=555)<br>
[![Implemented](https://img.shields.io/badge/Implemented-2ea44f?style=flat)](../implementation/claude-skills-implementation.md)

Claude Code 技能 — frontmatter 字段和官方内置技能。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## Frontmatter 字段（15 个）

| 字段 | 类型 | 必需 | 描述 |
|-------|------|----------|-------------|
| `name` | string | 否 | 显示名称和 `/slash-command` 标识符。省略时默认为目录名 |
| `description` | string | 推荐 | 技能的功能描述。在自动补全中显示，并被 Claude 用于自动发现 |
| `when_to_use` | string | 否 | 关于 Claude 何时应调用技能的额外上下文 — 触发短语和示例请求。附加到技能列表中的 `description` 之后，计入 1,536 字符上限 |
| `argument-hint` | string | 否 | 自动补全时显示的提示（例如 `[issue-number]`、`[filename]`） |
| `arguments` | string/list | 否 | 用于技能内容中 `$name` 替换的命名位置参数。接受空格分隔的字符串或 YAML 列表 — 名称按顺序映射到参数位置 |
| `disable-model-invocation` | boolean | 否 | 设置为 `true` 可防止 Claude 自动调用此技能 |
| `user-invocable` | boolean | 否 | 设置为 `false` 可从 `/` 菜单中隐藏 — 技能仅作为后台知识，用于代理预加载 |
| `allowed-tools` | string | 否 | 此技能激活时无需权限提示即可使用的工具 |
| `model` | string | 否 | 此技能运行时使用的模型（例如 `haiku`、`sonnet`、`opus`） |
| `effort` | string | 否 | 调用时覆盖模型 effort 级别（`low`、`medium`、`high`、`xhigh`、`max`） |
| `context` | string | 否 | 设置为 `fork` 可在隔离的子代理上下文中运行技能 |
| `agent` | string | 否 | 设置 `context: fork` 时的子代理类型（默认：`general-purpose`） |
| `hooks` | object | 否 | 作用域为此技能的生命周期钩子 |
| `paths` | string/list | 否 | 限制技能自动激活的 glob 模式。接受逗号分隔的字符串或 YAML 列表 — Claude 仅在与匹配文件交互时加载该技能 |
| `shell` | string | 否 | 用于 `` !`command` `` 块的 shell — `bash`（默认）或 `powershell`。需要 `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` |

---

## ![Official](../!/tags/official.svg) **（6 个）**

| # | 技能 | 描述 |
|---|-------|-------------|
| 1 | `simplify` | 审查已更改代码的复用性、质量和效率 — 重构以消除重复 |
| 2 | `batch` | 批量对多个文件运行命令 |
| 3 | `debug` | 调试失败的命令或代码问题 |
| 4 | `loop` | 按循环间隔运行提示或斜杠命令（最长 3 天） |
| 5 | `claude-api` | 使用 Claude API 或 Anthropic SDK 构建应用 — 在导入 `anthropic` / `@anthropic-ai/sdk` 时触发 |
| 6 | `fewer-permission-prompts` | 扫描对话记录中常见的只读 Bash/MCP 调用，并将优先级允许列表添加到 `.claude/settings.json` 以减少权限提示 |

另见：[官方技能仓库](https://github.com/anthropics/skills/tree/main/skills) 获取社区维护的可安装技能。

---

## 来源

- [Claude Code 技能 — 文档](https://code.claude.com/docs/en/skills)
- [单体仓库中的技能发现](../reports/claude-skills-for-larger-mono-repos.md)
- [Claude Code 更新日志](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
