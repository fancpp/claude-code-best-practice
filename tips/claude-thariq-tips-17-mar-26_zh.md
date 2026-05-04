# 从构建 Claude Code 中汲取的教训：如何运用 Skills — Thariq

一份全面指南，介绍 Anthropic 如何在内部使用 Skills，由 Thariq ([@trq212](https://x.com/trq212)) 于 2026 年 3 月 17 日分享。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

Skills 已成为 Claude Code 中最常用的扩展点之一。它们灵活、易于创建且易于分发。但这种灵活性也让人难以确定什么是最佳实践。Thariq 分享了在 Anthropic 内部大量使用 Skills（数百个活跃的 Skills）所汲取的教训。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/1.png" alt="Thariq 介绍推文" width="50%" /></a>

---

## 什么是 Skills？

一个常见的误解是 skills 只是"markdown 文件"，但最有趣的部分在于它们是**文件夹**，可以包含脚本、资源、数据等——这些是智能体可以发现、探索和操作的内容。Skills 还具有多种配置选项，包括注册动态钩子。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/2.png" alt="什么是 Skills？" width="50%" /></a>

---

## Skills 的类型

在整理所有 skills 后，团队注意到它们聚集为 9 个反复出现的类别。最好的 skills 能清晰地归入一个类别；令人困惑的 skills 则横跨多个类别。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/3.png" alt="Skills 类型网格" width="50%" /></a>

---

### 1/ 库与 API 参考

解释如何正确使用库、CLI 或 SDK 的 Skills。这些可以是针对内部库或 Claude Code 有时难以处理的常见库。它们通常包含一个参考代码片段文件夹和一份编写脚本时应避免的陷阱列表。

**示例：** billing-lib, internal-platform-cli, frontend-design

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/4.png" alt="库与 API 参考" width="50%" /></a>

---

### 2/ 产品验证

描述如何测试或验证代码是否正常工作的 Skills。这些通常与外部工具（如 Playwright、tmux 等）配合使用。验证 skills 对于确保 Claude 输出的正确性极为有用。值得让一名工程师花一周时间专门打磨你的验证 skills。

**示例：** signup-flow-driver, checkout-verifier, tmux-cli-driver

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/5.png" alt="产品验证" width="50%" /></a>

---

### 3/ 数据获取与分析

连接到你的数据和监控栈的 Skills。这些可能包含用于获取数据的库（含凭据）、特定的仪表板 ID 等，以及关于常见工作流或获取数据方式的说明。

**示例：** funnel-query, cohort-compare, grafana

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/6.png" alt="数据获取与分析" width="50%" /></a>

---

### 4/ 业务流程与团队自动化

将重复性工作流自动化成一个命令的 Skills。这些通常是指令相当简单的技能，但可能对其他 skills 或 MCP 有较复杂的依赖。将先前的结果保存在日志文件中可以帮助模型保持一致性，并反思之前的工作流执行情况。

**示例：** standup-post, create-\<ticket-system\>-ticket, weekly-recap

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/7.png" alt="业务流程与团队自动化" width="50%" /></a>

---

### 5/ 代码脚手架与模板

为代码库中的特定功能生成框架模板的 Skills。你可以将这些 skills 与可组合的脚本结合起来。当你的脚手架有纯代码无法覆盖的自然语言需求时，它们尤其有用。

**示例：** new-\<framework\>-workflow, new-migration, create-app

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/8.png" alt="代码脚手架与模板" width="50%" /></a>

---

### 6/ 代码质量与审查

在你的组织内部强制执行代码质量并帮助审查代码的 Skills。这些可以包含确定性的脚本或工具以最大化健壮性。你可能希望将这些 skills 作为钩子的一部分或 GitHub Action 中自动运行。

**示例：** adversarial-review, code-style, testing-practices

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/9.png" alt="代码质量与审查" width="50%" /></a>

---

### 7/ CI/CD 与部署

帮助你获取、推送和部署代码库中代码的 Skills。这些 skills 可能引用其他 skills 来收集数据。

**示例：** babysit-pr, deploy-\<service\>, cherry-pick-prod

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/10.png" alt="CI/CD 与部署" width="50%" /></a>

---

### 8/ Runbooks

根据症状（如 Slack 线程、告警或错误签名），进行多工具调查并生成结构化报告的 Skills。

**示例：** \<service\>-debugging, oncall-runner, log-correlator

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/11.png" alt="Runbooks" width="50%" /></a>

---

### 9/ 基础设施运维

执行日常维护和运维流程的 Skills——其中一些涉及具有破坏性的操作，需要防护措施。这些使工程师更容易在关键操作中遵循最佳实践。

**示例：** \<resource\>-orphans, dependency-management, cost-investigation

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/12.png" alt="基础设施运维" width="50%" /></a>

---

## 制作 Skills 的技巧

撰写有效 skills 的 9 条最佳实践，以及分发和衡量的指导。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/13.png" alt="制作 Skills 的技巧网格" width="50%" /></a>

---

### 技巧 1：不要陈述显而易见的事情

Claude Code 对你的代码库了解很多，Claude 也很懂编码，包括许多默认观点。如果你发布的技能主要是关于知识的，试着聚焦于能让 Claude 跳出常规思维的信息。前端设计技能是一个很好的例子——它是通过与客户反复迭代来改善 Claude 的设计品味而构建的，避免了像 Inter 字体和紫色渐变这类经典模式。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/14.png" alt="不要陈述显而易见的事情" width="50%" /></a>

---

### 技巧 2：建立陷阱章节

任何技能中信号价值最高的内容就是"陷阱"章节。这些章节应该基于 Claude 使用你的技能时遇到的常见失败点来构建。理想情况下，你会随着时间的推移更新你的技能来捕捉这些陷阱。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/15.png" alt="建立陷阱章节" width="50%" /></a>

---

### 技巧 3：使用文件系统和渐进式披露

一个 skill 是一个文件夹，而不仅仅是一个 markdown 文件。你应该把整个文件系统视为一种上下文工程和渐进式披露的形式。告诉 Claude 你的 skill 里有哪些文件，它会在适当的时候读取它们。最简单的形式是指向其他 markdown 文件——例如，将详细的函数签名和使用示例拆分到 `references/api.md` 中。你可以拥有参考资料、脚本、示例等的文件夹。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/16.png" alt="渐进式披露" width="50%" /></a>

---

### 技巧 4：避免过度限制 Claude

Claude 通常会尽量遵循你的指示，而由于 skills 的可重用性很高，你需要注意不要过于具体。给 Claude 提供它需要的信息，但也要给它根据情况调整的灵活性。与其给出规定性的逐步指令，不如给出目标和约束条件。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/17.png" alt="避免过度限制 Claude" width="50%" /></a>

---

### 技巧 5：思考好设置

某些 skills 可能需要根据用户的上下文进行设置。一个好的模式是将这些设置信息存储在 skill 目录中的 `config.json` 文件中。如果配置尚未设置，智能体可以向用户询问信息。你可以指示 Claude 使用 AskUserQuestion 工具进行结构化的多项选择题。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/18.png" alt="思考好设置" width="50%" /></a>

---

### 技巧 6：Description 字段是为模型写的

当 Claude Code 启动会话时，它会构建一个所有可用 skill 及其描述的列表。Claude 扫描这个列表来判断"这个请求有没有对应的 skill？"这意味着 description 字段不是摘要——它是描述**何时触发**这个 skill。为模型而写。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/19.png" alt="Description = 触发器" width="50%" /></a>

---

### 技巧 7：记忆与数据存储

某些 skills 可以通过在其中存储数据来包含一种记忆形式。你可以将数据存储在简单的仅追加文本日志文件或 JSON 文件中，也可以复杂到使用 SQLite 数据库。当你升级 skill 时，存储在 skill 目录中的数据可能会被删除，所以使用 `${CLAUDE_PLUGIN_DATA}` 作为每个插件的稳定文件夹来存储数据。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/20.png" alt="记忆与数据存储" width="50%" /></a>

---

### 技巧 8：存储脚本并生成代码

你可以给 Claude 最强大的工具之一就是代码。给 Claude 脚本和库，可以让 Claude 把精力花在组合上，决定下一步做什么，而不是重复造轮子。然后 Claude 可以即时生成脚本，将这些功能组合起来进行更高级的分析。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/21.png" alt="存储脚本并生成代码" width="50%" /></a>

---

### 技巧 9：按需钩子

Skills 可以包含仅在调用该 skill 时激活的钩子，并且持续到会话结束。用于那些你不想一直运行但有时非常有用、更定制化的钩子。

**示例：**
- `/careful` — 通过 PreToolUse 匹配器在 Bash 中阻止 rm -rf、DROP TABLE、force-push、kubectl delete
- `/freeze` — 阻止任何不在特定目录中的 Edit/Write

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/22.png" alt="按需钩子" width="50%" /></a>

---

## 分发 Skills

与团队共享 skills 的两种方式：
- **检入到你的仓库**（在 `.claude/skills` 下）——最适合在相对较少的仓库上协作的小团队
- **制作一个插件**并建立一个 Claude Code 插件市场，用户可以上传和安装插件

每个检入的 skill 也会给模型上下文增加一点负担。随着规模扩大，内部插件市场允许你分发 skills，让你的团队决定安装哪些。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/23.png" alt="分发 Skills" width="50%" /></a>

---

## 管理市场

并没有一个集中的团队来决定哪些 skills 进入市场。相反，尝试有机地找到最有用的 skills。上传到 GitHub 的沙盒文件夹中，并通过 Slack 或其他论坛将人们指向那里。一旦一个 skill 获得了关注（由 skill 所有者决定），他们可以提交 PR 将其移入市场。发布前的策展很重要，以避免冗余的 skills。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/24.png" alt="管理市场" width="50%" /></a>

---

## 组合 Skills

你可能希望有相互依赖的 skills。例如，一个文件上传 skill 上传文件，和一个 CSV 生成 skill 生成 CSV 并上传。这种依赖管理目前还没有原生内置于市场或 skills 中，但你可以直接通过名称引用其他 skills，如果它们已安装，模型就会调用它们。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/25.png" alt="组合 Skills" width="50%" /></a>

---

## 衡量 Skills

要了解一个 skill 的表现如何，使用一个 PreToolUse 钩子来记录公司内部的 skill 使用情况。这样你就可以找到哪些 skills 很受欢迎，或者哪些与预期相比触发不足。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/26.png" alt="衡量 Skills" width="50%" /></a>

---

## 结论

Skills 是智能体极其强大且灵活的工具，但一切都还处于早期阶段，我们都在摸索如何最好地使用它们。请把这更多地看作是我们已验证有效的一些实用技巧的集合，而非一份权威指南。理解 skills 最好的方法是开始使用、尝试，并看看什么对你有效。我们的大多数 skills 都是从几行文字和一个陷阱开始的，并随着时间的推移因为人们不断在 Claude 遇到新的边缘情况时添加内容而变得更好。

<a href="https://x.com/trq212/status/2033949937936085378"><img src="assets/thariq-26-3-17/27.png" alt="结论" width="50%" /></a>

---

## 来源

- [Thariq (@trq212) 在 X 上 — 2026 年 3 月 17 日](https://x.com/trq212/status/2033949937936085378)
- [Skilljar — 智能体 Skills 课程](https://code.claude.com/docs/en/skills)
- [Skill 创建器](https://code.claude.com/docs/en/skills)
