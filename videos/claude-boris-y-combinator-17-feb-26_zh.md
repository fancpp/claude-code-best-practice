# 与 Claude Code 创建者 Boris Cherny 的内部对话 — Y Combinator

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 视频详情

- **嘉宾:** Boris Cherny（Claude Code 创建者）
- **主持人:** Dalton Caldwell（Y Combinator）与 Michael Seibel（Y Combinator）
- **发布时间:** 2026 年 2 月 17 日
- **YouTube:** [在 YouTube 上观看](https://youtu.be/tNjDcGcf_Vw)

---

## 采访实录

[`0:00`](https://youtu.be/tNjDcGcf_Vw?t=0) 欢迎来到 Light Cone。我是 Dalton Caldwell。我和 Michael Seibel 在一起。今天我们有幸邀请到 Boris Cherny，他是 Anthropic 的成员 of technical staff，也是 Claude Code 的创建者。Boris，欢迎你。

[`0:18`](https://youtu.be/tNjDcGcf_Vw?t=18) 谢谢。很高兴来到这里。

[`0:22`](https://youtu.be/tNjDcGcf_Vw?t=22) 那么，Boris，你是产品负责人，Claude Code 的工程负责人。你最近在社交平台上因为一段对话而热门，内容是关于你加入 Anthropic 的第一周，你手写了一个 PR，然后被要求重写——使用 Claude Code。你能告诉我们那个故事吗？

[`0:37`](https://youtu.be/tNjDcGcf_Vw?t=37) 是的。那是我在 Anthropic 的第一周。我刚刚入职，建立了开发环境，我想，"好吧，我要开始写代码了。我要提交一个 PR。"于是我写了一个不错的 PR。代码写得很好。我提交了。它被批准了。后来我被人拉到一边说，"嘿，下次请用 Claude 来写代码。"所以是的，那真的发生了。

[`0:55`](https://youtu.be/tNjDcGcf_Vw?t=55) 所以你在 Anthropic 的第一周，有人告诉你不要手写代码？

[`0:59`](https://youtu.be/tNjDcGcf_Vw?t=59) 是的，基本上是这样。

[`1:03`](https://youtu.be/tNjDcGcf_Vw?t=63) （笑）那是相当强力的入职引导。

[`1:07`](https://youtu.be/tNjDcGcf_Vw?t=67) 是的，这是一个很好的方式，让你了解公司的优先事项。

[`1:13`](https://youtu.be/tNjDcGcf_Vw?t=73) 那么，你能带我们了解 Claude Code 是如何诞生的吗？在 Anthropic 内部，它是如何从一个想法变成一个产品的？

[`1:20`](https://youtu.be/tNjDcGcf_Vw?t=80) 当然。Claude Code 最初是我在 Anthropic 的一个 side project。我记得当时在想："Claude 在对话方面真的很棒，但如果有朝一日它能读取我的文件系统、写入文件并运行命令，那它作为一个编码助手将会非常强大。"于是我开始在周末摆弄它。我建立了一个基本循环——Claude 可以调用工具来读取文件、写入文件和运行 bash 命令。这很粗糙，但令人难以置信地有效。即使在那时，我也看到了巨大的潜力。我在公司内部展示了一下，人们很兴奋。结果发现，公司里还有其他人也在做类似的事情。所以我们将我们的努力合并了。最终，经过大量的迭代，它变成了今天的 Claude Code。

[`2:05`](https://youtu.be/tNjDcGcf_Vw?t=125) 在 Anthropic 内部进行产品开发是什么样的？你们使用像 PRD（产品需求文档）这样的传统产品管理工件吗？

[`2:12`](https://youtu.be/tNjDcGcf_Vw?t=132) 老实说，在 Claude Code 团队，我们很少写 PRD。我们只是快速原型设计，展示东西，看看什么有效。在像这样的工具中，很多"感觉"来自于尝试事物并查看它们如何交互。很难在 PRD 中捕捉这种感觉。所以我们倾向于快速原型设计。构建一些东西。感受它。让一些人在上面试用。获取反馈。迭代。这种快速反馈循环使我们能够快速交付更好的产品。

[`2:42`](https://youtu.be/tNjDcGcf_Vw?t=162) 你提到 Claude Code 被设计成扩展工程能力，而不是取代工程师。你能谈谈这种设计理念吗？

[`2:50`](https://youtu.be/tNjDcGcf_Vw?t=170) 当然。从一开始，我们就刻意设计 Claude Code 来增强开发者，而不是取代他们。这就是为什么有 Claude Code 所谓的"人在回路中"的模式。它在征求许可、显示差异，并在执行命令前等待批准。它被设计成一个协作工具。它不是一个自动化工具，让你说"去做这个"，然后回来看结果。它是"我们一起来做这个"。这在权限系统中很明显——Claude Code 总是在运行有副作用的命令前征求许可。它不只是自己做决定。它始终让你掌控，同时加速你实现目标的进程。

[`3:28`](https://youtu.be/tNjDcGcf_vw?t=208) 这种设计理念在实际中如何运作？

[`3:32`](https://youtu.be/tNjDcGcf_vw?t=212) 例如，当 Claude Code 想要编辑一个文件时，它会显示 diff，并在实际编辑前征求你的许可。当你批准时，它就进行编辑。如果你说不，它就会尝试不同的方法。所以它总是协作的。它不只是盲目地修改东西。它尊重你的自主权。

[`3:50`](https://youtu.be/tNjDcGcf_vw?t=230) 谈谈 Claude Code 的权限系统。你能详细说说吗？

[`3:55`](https://youtu.be/tNjDcGcf_vw?t=235) 权限系统是我们为确保安全而构建的最重要的功能之一。我们有多层保护。最底层是，Claude Code 不能运行任何不是显式允许的命令。我们有预批准的安全命令列表——主要是读取操作，比如 ls、cat 这类安全的命令。但对于任何有副作用的操作——写入文件、安装软件包、运行任意代码——Claude Code 必须在执行前征求许可。作为用户，你可以选择"允许一次"、"允许此会话"或"永远允许"这个命令。此外，你还可以配置"允许列表"——你信任的特定命令模式，这样 Claude Code 运行它们时不会提示你。这一切都是为了让开发者掌控一切，同时保持体验的流畅性。

[`4:45`](https://youtu.be/tNjDcGcf_vw?t=285) Claude Code 如何处理非常大型的代码库？人们经常问的一个问题是，"Claude 的上下文窗口能处理整个代码库吗？"

[`4:54`](https://youtu.be/tNjDcGcf_vw?t=294) 是的，这是个好问题。Claude Code 不需要一次加载整个代码库。它使用各种技术来只加载需要的代码。它使用 glob 和 grep 等搜索工具来查找相关文件。它只在需要时才读取文件。所以它不关心代码库的总大小。它关心的是手头任务相关的代码大小。这使得它在大型代码库上也能良好扩展。

[`5:20`](https://youtu.be/tNjDcGcf_vw?t=320) 你提到 Claude Code 使用子代理进行并行处理。这是如何工作的？

[`5:25`](https://youtu.be/tNjDcGcf_vw?t=325) 是的，对于可以并行完成的更大任务，Claude Code 会启动子代理。每个子代理在隔离的上下文中工作，拥有自己的上下文窗口。然后主代理协调所有子代理并合并结果。这类似于人类团队的工作方式。它显著提高了大型重构或需要并行处理多个独立更改的任务的效率。

[`5:50`](https://youtu.be/tNjDcGcf_vw?t=350) 产品方面——Claude Code 哪些有效，哪些无效，你学到了什么？

[`5:55`](https://youtu.be/tNjDcGcf_vw?t=355) 很多有效的东西是关于简单性的。我们学到的一件事是，简单提示效果最好。当你给 Claude 一个聚焦的、定义明确的任务时，它表现出色。当提示模糊或过于宽泛时，它表现不佳。我们还了解到人们重视透明性——当他们能看到 Claude 正在做什么、为什么这样做时，他们更信任输出。所以 Claude Code 的详细输出——显示它正在做什么——对建立信任非常有帮助。说到无效的东西——早期我们尝试过在交互式情况下让模型更"自主"。人们没有安全感。他们觉得失控了。这就是为什么我们转向"人在回路中"的模式——它在自主性和控制之间取得了恰当的平衡。

[`6:37`](https://youtu.be/tNjDcGcf_vw?t=397) 我认为我们处于这样一个阶段，我们刚刚看到更多的功能和能力被添加到 Claude Code。你认为未来几个月或几年里，AI 编码助手会走向何方？

[`6:50`](https://youtu.be/tNjDcGcf_vw?t=410) 我认为我们只是触及了表面。我认为我们会看到更复杂的代理能力——其中 AI 不仅编写代码，还能调试并修复自己的错误。我认为我们会看到与其他工具更深入的集成——将 Claude Code 连接到设计工具、项目管理工具以及整个开发者工作流程。而且，我认为我们看到这样的世界：多智能体系统变得越来越普遍——不仅是一个 AI 智能体，而是多个相互协作的 AI 智能体。我们已经通过 Claude Code 中的子代理看到了这一点，我认为这只是开始。

[`7:27`](https://youtu.be/tNjDcGcf_vw?t=447) Claude Code 如何处理团队协作？使用 Claude Code 的团队在工作流程上有什么变化？

[`7:35`](https://youtu.be/tNjDcGcf_vw?t=455) 我们看到采用 Claude Code 的团队在很多方面的变化。代码审查发生了变化——你现在花更少的时间检查语法，更多的时间审查架构和设计决策。结对编程发生了变化——Claude 充当了永不疲倦的结对程序员，随时准备编写代码或回答问题。入职流程也发生了变化——新团队成员使用 Claude Code 更快地熟悉代码库，只需问"这个服务是如何设置的？"或"这个 API 是如何工作的？"。

[`8:08`](https://youtu.be/tNjDcGcf_vw?t=488) 你认为像 Claude Code 这样的工具如何改变初创公司的格局？YC 的观众会对这个特别感兴趣。

[`8:15`](https://youtu.be/tNjDcGcf_vw?t=495) 我认为对于初创公司来说，这是一个巨大的机会。借助 Claude Code，一支小团队可以完成以前需要更大团队才能完成的工作。它降低了构建软件的门槛。这意味着，拥有好创意的创始人现在可以更快地构建它们的 MVP（最小可行产品），迭代速度更快，只需更少的工程资源。我预测我们将看到更多由极小型团队构建的成功初创公司，也许只有一两个人，但借助像 Claude Code 这样的工具，他们能够完成十人团队过去才能做的工作。

[`8:50`](https://youtu.be/tNjDcGcf_vw?t=530) 对于想要最大化 Claude Code 价值的初创公司创始人，你有什么建议？

[`8:55`](https://youtu.be/tNjDcGcf_vw?t=535) 我的建议是，不要只是把它当作一个玩具。将其作为你开发流程的核心部分。为你的代码库设置 Claude Code，了解它的优势，在你的工作流程中使用它。并且，不要害怕推动它。尝试复杂的任务。看看它的极限在哪里。你可能会惊讶于它能做什么。但也要建立安全措施——版本控制一切，使用 CI，进行代码审查。像对待任何强大工具一样对待它——尊重它，但也要利用它。

[`9:30`](https://youtu.be/tNjDcGcf_vw?t=570) 这对 YC 创始人来说是极好的建议。你今天还有什么想补充的吗？

[`9:35`](https://youtu.be/tNjDcGcf_vw?t=575) 我想说的是，这是一个前所未有的建设好时机。构建软件的成本急剧下降。这为有创造力的创始人创造了不可思议的机会。我迫不及待地想看到人们用这些新工具构建出什么。

[`9:55`](https://youtu.be/tNjDcGcf_vw?t=595) Boris，非常感谢你加入我们。

[`10:00`](https://youtu.be/tNjDcGcf_vw?t=600) 谢谢你们邀请我。
