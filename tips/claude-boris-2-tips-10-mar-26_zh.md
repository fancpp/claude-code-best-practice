# 代码审查与测试时间计算 — Boris Cherny 的技巧

总结 Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 3 月 10 日分享的洞见。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 1/ 引入代码审查

Claude Code 新增功能：**代码审查**。一个代理团队会对每个 PR 进行深度审查。

- 首先为 Anthropic 自身团队构建 — 今年每位工程师的代码产出提升了 **200%**，而审查成了瓶颈
- Boris 已经使用了几周，发现它能捕捉到许多他自己可能注意不到的真实 bug
- 当 PR 打开时，Claude 会派遣一个代理团队来寻找 bug

<a href="https://x.com/bcherny/status/2031089411820228645"><img src="assets/boris-26-3-10/0.png" alt="Boris Cherny 宣布代码审查" width="50%" /></a>

---

## 2/ 测试时间计算与多上下文窗口

大致来说，你投入编程问题的 token 越多，结果就越好。Boris 称之为**测试时间计算**。

- 使用**独立的上下文窗口**会让结果更好 — 这就是子代理的工作原理，也是为什么一个代理可能引入 bug，而另一个（使用完全相同的模型）能发现它们
- 类似于工程团队：如果 Boris 引入了一个 bug，他的同事在审查代码时比他本人更可靠地发现它
- 最终，代理可能会写出完美的无 bug 代码 — 在那之前，**多个不相关的上下文窗口**通常是一个好方法

<a href="https://x.com/bcherny/status/2031151689219321886"><img src="assets/boris-26-3-10/1.png" alt="Boris Cherny 谈测试时间计算" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 3 月 10 日](https://x.com/bcherny)
