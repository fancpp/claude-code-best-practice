# 使用 Claude Code 的 10 个技巧 — 来自 Claude Code 团队

Claude Code 创建者 Boris Cherny ([@bcherny](https://x.com/bcherny)) 于 2026 年 2 月 1 日分享的团队技巧总结。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Boris 分享了直接来自 Claude Code 团队的使用技巧。团队使用 Claude 的方式与 Boris 个人使用方式不同。请记住：没有唯一正确的使用 Claude Code 的方式——每个人的设置都不同。你应该尝试找出适合你的方法！

<a href="https://x.com/bcherny/status/2017742741636321619"><img src="assets/boris-26-2-1/0.png" alt="Boris Cherny 介绍推文" width="50%" /></a>

---

## 1/ 并行做更多事

同时启动 3–5 个 git worktree，每个运行自己独立的 Claude 会话。这是最大的生产力提升，也是团队的首选技巧。Boris 个人使用多个 git checkout，但 Claude Code 团队的大多数人更喜欢 worktree——这就是 `@amorisscode` 在 Claude Desktop 应用中为它们构建原生支持的原因！

有些人还会命名他们的 worktree 并设置 shell 别名（`2a`、`2b`、`2c`），这样可以通过一次按键在它们之间切换。其他人则有一个专门的"分析"worktree，仅用于读取日志和运行 BigQuery。

参见：[Worktrees 文档](https://code.claude.com/docs/en/common...)

<a href="https://x.com/bcherny/status/2017742743125299476"><img src="assets/boris-26-2-1/1.png" alt="并行做更多事" width="50%" /></a>

---

## 2/ 每个复杂任务都以计划模式开始

将你的精力投入到计划中，这样 Claude 就能一次性完成实现。

一个人用第一个 Claude 写计划，然后启动第二个 Claude 像高级工程师一样审查它。

另一个人说，一旦事情出问题，他们就切换回计划模式重新规划。不要继续推进。他们还明确告诉 Claude 进入计划模式进行验证步骤，而不仅仅是构建阶段。

<a href="https://x.com/bcherny/status/2017742745365057733"><img src="assets/boris-26-2-1/2.png" alt="每个复杂任务都以计划模式开始" width="50%" /></a>

---

## 3/ 投资你的 CLAUDE.md

每次纠正后，以"更新你的 CLAUDE.md，这样你就不会再犯同样的错误"结束。Claude 在为自己编写规则方面出奇地擅长。

无情地编辑你的 `CLAUDE.md`。持续迭代，直到 Claude 的错误率明显下降。

一位工程师让 Claude 为每个任务/项目维护一个笔记目录，每次 PR 后更新。然后他们将 `CLAUDE.md` 指向它。

<a href="https://x.com/bcherny/status/2017742747067945390"><img src="assets/boris-26-2-1/3.png" alt="投资你的 CLAUDE.md" width="50%" /></a>

---

## 4/ 创建你自己的技能并提交到 Git

在项目间重复使用。来自团队的技巧：

- 如果你一天做某事超过一次，就把它变成技能或命令
- 构建一个 `/techdebt` 斜杠命令，在每次会话结束时运行，查找并消除重复代码
- 设置一个斜杠命令，将 7 天的 Slack、GDrive、Asana 和 GitHub 同步到一个上下文转储中
- 构建类似分析工程师的代理，用于编写 dbt 模型、审查代码以及测试开发环境中的变更

参见：[使用技能扩展 Claude — Claude Code 文档](https://code.claude.com/docs/en/skills)

<a href="https://x.com/bcherny/status/2017742748984742078"><img src="assets/boris-26-2-1/4.png" alt="创建你自己的技能" width="50%" /></a>

---

## 5/ Claude 自己修复大部分 Bug

团队是这样做的：

启用 Slack MCP，然后将 Slack 的 bug 讨论粘贴到 Claude 中，只需说"修复"。无需任何上下文切换。

或者，直接说"去修复失败的 CI 测试"。不要微观管理怎么做。

将 Claude 指向 docker 日志来排查分布式系统——它在这方面出奇地有能力。

<a href="https://x.com/bcherny/status/2017742750473720121"><img src="assets/boris-26-2-1/5.png" alt="Claude 自己修复大部分 Bug" width="50%" /></a>

---

## 6/ 提升你的提示技巧

a. **挑战 Claude。** 说"质问我这些更改，除非我通过你的测试，否则不要提 PR。"让 Claude 做你的审查员。或者说"证明我这样做是可行的"，让 Claude 比较 main 分支和你的特性分支的行为差异。

b. **在平庸的修复之后，** 说："基于你现在知道的一切，放弃这个并实现优雅的解决方案。"

c. **编写详细的规格说明**并在移交工作前减少歧义。你越具体，输出就越好。

<a href="https://x.com/bcherny/status/2017742752566632544"><img src="assets/boris-26-2-1/6.png" alt="提升你的提示技巧" width="50%" /></a>

---

## 7/ 终端和环境设置

团队喜欢 Ghostty！多人喜欢它的同步渲染、24 位色彩和正确的 unicode 支持。

为了更容易地管理多个 Claude，使用 `/statusline` 自定义你的状态栏，始终显示上下文使用情况和当前 git 分支。许多人还会对终端标签进行颜色编码和命名，有时使用 tmux——每个任务/worktree 一个标签。

使用语音输入。你说话比打字快 3 倍，你的提示也会因此变得更详细。（在 macOS 上按 fn 两次）

参见：[终端设置文档](https://code.claude.com/docs/en/termin...)

<a href="https://x.com/bcherny/status/2017742753971769626"><img src="assets/boris-26-2-1/7.png" alt="终端和环境设置" width="50%" /></a>

---

## 8/ 使用子代理

a. 在任何你想让 Claude 投入更多计算资源的问题后添加"使用子代理"。

b. 将独立任务卸载给子代理，以保持你主代理的上下文窗口干净和专注。

c. 通过钩子将权限请求路由到 Opus 4.5——让它扫描攻击并自动批准安全的请求。参见：[钩子文档](https://code.claude.com/docs/en/hooks#...)

<a href="https://x.com/bcherny/status/2017742755737555434"><img src="assets/boris-26-2-1/8.png" alt="使用子代理" width="50%" /></a>

---

## 9/ 使用 Claude 进行数据和数据分析

让 Claude Code 使用"bq"CLI 即时拉取和分析指标。团队在代码库中有一个 BigQuery 技能，每个人都在 Claude Code 中直接使用它进行分析查询。Boris 个人已经 6 个多月没写过一行 SQL 了。

这对任何有 CLI、MCP 或 API 的数据库都适用。

<a href="https://x.com/bcherny/status/2017742757666902374"><img src="assets/boris-26-2-1/9.png" alt="使用 Claude 进行数据和数据分析" width="50%" /></a>

---

## 10/ 使用 Claude 学习

来自团队的一些用 Claude Code 学习的技巧：

a. 在 `/config` 中启用"解释型"或"学习型"输出风格，让 Claude 解释其变更背后的"原因"。

b. 让 Claude 生成一个可视化的 HTML 演示来解释你不熟悉的代码。它做的幻灯片出奇地好！

c. 让 Claude 绘制新的协议和代码库的 ASCII 图表，帮助你理解它们。

d. 构建一个间隔重复学习技能：你解释你的理解，Claude 提出后续问题填补空白，存储结果。

<a href="https://x.com/bcherny/status/2017742759218794768"><img src="assets/boris-26-2-1/10.png" alt="使用 Claude 学习" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X — 2026 年 2 月 1 日](https://x.com/bcherny/status/2017742741636321619)
