# 我如何使用 Claude Code — Boris Cherny 的 13 条建议

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 1 月 3 日分享的设置技巧摘要。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Boris 分享了他个人的 Claude Code 设置，并指出它"出奇地朴素"——Claude Code 开箱即用效果很好，所以他并没有做太多定制。没有唯一正确的使用方法：团队有意将其设计得灵活可扩展，你可以按自己的喜好使用、定制和改造它。Claude Code 团队中的每个人使用方式都大不相同。

<a href="https://x.com/bcherny/status/2007179832300581177"><img src="assets/boris-26-1-3/0.png" alt="Boris Cherny 介绍推文" width="50%" /></a>

---

## 1/ 并行运行 5 个 Claude

在终端中并行运行 5 个 Claude。将标签页编号 1–5，并使用系统通知来知道哪个 Claude 需要输入。

参见：[终端设置文档](https://code.claude.com/docs/en/terminal)

<a href="https://x.com/bcherny/status/2007179833990885678"><img src="assets/boris-26-1-3/1.png" alt="并行运行 5 个 Claude" width="50%" /></a>

---

## 2/ 使用 claude.ai/code 实现更多并行

在本地的 Claude 之外，再在 claude.ai/code 上并行运行 5–10 个 Claude。使用 `claude.ai/code` 将本地会话移交到 Web 会话，在 Chrome 中手动启动会话，并在两者之间自由切换。

<a href="https://x.com/bcherny/status/2007179836704600237"><img src="assets/boris-26-1-3/2.png" alt="claude.ai/code 并行" width="50%" /></a>

---

## 3/ 在所有任务中使用带思考的 Opus

在所有任务中使用带思考功能的 Opus 4.5。这是 Boris 用过的最好的编程模型——尽管它比 Sonnet 更大更慢，但由于你需要引导的次数更少，而且它在工具使用上更出色，最终几乎总是比使用较小的模型更快。

<a href="https://x.com/bcherny/status/2007179838864666847"><img src="assets/boris-26-1-3/3.png" alt="带思考的 Opus" width="50%" /></a>

---

## 4/ 与团队共享单一的 CLAUDE.md

为仓库共享一个 `CLAUDE.md` 文件。将其提交到 git，让整个团队每周多次贡献内容。每当 Claude 做错了什么，将其添加到 `CLAUDE.md` 中，这样 Claude 下次就知道不要这样做了。

<a href="https://x.com/bcherny/status/2007179840848597422"><img src="assets/boris-26-1-3/4.png" alt="共享 CLAUDE.md" width="50%" /></a>

---

## 5/ 在 PR 中标记 @claude 以更新 CLAUDE.md

在代码审查期间，在你同事的 PR 中标记 `@claude`，将内容添加到 `CLAUDE.md` 作为 PR 的一部分。使用 Claude Code GitHub action（[install-@hub-action](https://github.com/apps/claude)）来实现——这是 Boris 的"复利工程"版本。

<a href="https://x.com/bcherny/status/2007179842928947333"><img src="assets/boris-26-1-3/5.png" alt="在 PR 中标记 @claude" width="50%" /></a>

---

## 6/ 大多数会话以计划模式开始

大多数会话以计划模式开始（按两次 shift+tab）。如果目标是编写一个 Pull Request，使用计划模式并与 Claude 反复沟通，直到你喜欢它的计划。然后切换到自动接受编辑模式，Claude 通常可以一次性完成。好的计划非常重要。

<a href="https://x.com/bcherny/status/2007179845336527000"><img src="assets/boris-26-1-3/6.png" alt="计划模式" width="50%" /></a>

---

## 7/ 为内循环工作流使用斜杠命令

为每天执行多次的每个"内循环"工作流使用斜杠命令。这省去了重复提示的麻烦，也让 Claude 可以使用这些工作流。命令被提交到 git 中，存放在 `.claude/commands/` 目录下。

示例：`/commit-push-pr` — 提交、推送并打开 PR。

<a href="https://x.com/bcherny/status/2007179847949500714"><img src="assets/boris-26-1-3/7.png" alt="斜杠命令" width="50%" /></a>

---

## 8/ 使用子代理自动化常见工作流

定期使用几个子代理：`code-simplifier` 在 Claude 完成工作后简化代码，`verify-app` 包含测试 Claude Code 端到端的详细指令，等等。把子代理看作自动化最常见的工作流——类似于斜杠命令。

子代理存放在 `.claude/agents/` 中。

<a href="https://x.com/bcherny/status/2007179850139000872"><img src="assets/boris-26-1-3/8.png" alt="子代理" width="50%" /></a>

---

## 9/ 使用 PostToolUse 钩子自动格式化代码

使用 `PostToolUse` 钩子来格式化 Claude 的代码。Claude 通常开箱即用就能生成格式良好的代码，钩子处理最后 10% 以避免后续 CI 中的格式错误。

```json
"PostToolUse": [
  {
    "matcher": "Write|Edit",
    "hooks": [
      {
        "type": "command",
        "command": "bun run format || true"
      }
    ]
  }
]
```

<a href="https://x.com/bcherny/status/2007179852047335529"><img src="assets/boris-26-1-3/9.png" alt="用于格式化的 PostToolUse 钩子" width="50%" /></a>

---

## 10/ 预授权权限而非使用 --dangerously-skip-permissions

不要使用 `--dangerously-skip-permissions`。而是使用 `/permissions` 来预授权你知道在你的环境中安全的常用 bash 命令，以避免不必要的权限提示。其中大部分权限被提交到 `.claude/settings.json` 中并与团队共享。

<a href="https://x.com/bcherny/status/2007179854077407667"><img src="assets/boris-26-1-3/10.png" alt="预授权权限" width="50%" /></a>

---

## 11/ 让 Claude 通过 MCP 使用你所有的工具

Claude Code 会使用你所有的工具。它经常搜索并发布到 Slack（通过 MCP 服务器）、运行 BigQuery 查询来回答分析问题（使用 `bq` CLI）、从 Sentry 获取错误日志等。Slack MCP 配置被提交到 `.mcp.json` 中并与团队共享。

<a href="https://x.com/bcherny/status/2007179856266789204"><img src="assets/boris-26-1-3/11.png" alt="MCP 工具" width="50%" /></a>

---

## 12/ 使用后台代理验证长时间运行的任务

对于非常长时间运行的任务，要么 (a) 提示 Claude 在完成后使用后台代理验证其工作，要么 (b) 使用代理 Stop 钩子更确定地执行此操作，要么 (c) 使用 ralph-wiggum 插件（最初由 @GeoffreyHuntley 构想）。

<a href="https://x.com/bcherny/status/2007179858435281082"><img src="assets/boris-26-1-3/12.png" alt="长时间运行任务的验证" width="50%" /></a>

---

## 13/ 给 Claude 一种验证其工作的方法

这可能是从 Claude Code 获得出色结果的最重要的事情——给 Claude 一种验证其工作的方法。如果 Claude 有这个反馈循环，最终结果的质量将提升 2-3 倍。

Claude 测试了 Boris 所做的每一个更改。

<a href="https://x.com/bcherny/status/2007179861115511237"><img src="assets/boris-26-1-3/13.png" alt="给 Claude 验证的方法" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 1 月 3 日](https://x.com/bcherny/status/2007179832300581177)
