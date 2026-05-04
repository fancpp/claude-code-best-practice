# 充分利用 Opus 4.7 的 6 个技巧 — 来自 Boris Cherny

Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 4 月 16 日分享的一系列技巧 — 在亲身使用 Opus 4.7 数周后。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 背景

在亲自使用 Opus 4.7 数周后，Boris 感到"难以置信地高效"，并分享了六种充分利用新模型的方法 — 从权限自动化到努力程度调节再到验证模式。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/0.png" alt="Boris Cherny 介绍推文 — 亲身使用 Opus 4.7" width="50%" /></a>

---

## 1/ 自动模式 — 不再有权限提示

Opus 4.7 喜欢执行复杂、长期运行的任务：深度研究、重构代码、构建复杂功能、迭代直到达到性能基准。过去，你要么需要在这些长时间任务中"保姆式"地看管模型，要么使用 `--dangerously-skip-permissions`。

Anthropic 最近推出了**自动模式**作为更安全的替代方案。在此模式下，权限提示被路由到基于模型的分类器，由它决定命令是否安全运行：

- 如果安全，自动批准
- 如果有风险，暂停并询问

这意味着模型运行时不再需要看管。更重要的是，这意味着你可以并行运行更多 Claude 实例 — 如果安全，你可以将注意力切换到下一个 Claude。

自动模式现已面向 Max、Teams 和 Enterprise 用户提供 Opus 4.7 版本。在 CLI 中使用 **Shift+Tab** 在"询问权限"→"计划模式"→"自动模式"之间切换，或在桌面版或 VS Code 的下拉菜单中选择。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/1.png" alt="Boris Cherny 谈自动模式" width="50%" /></a>

---

## 2/ 新的 /fewer-permission-prompts 技能

Anthropic 发布了一个新的 `/fewer-permission-prompts` 技能。它会扫描你的会话历史，找到安全但反复请求权限的常见 bash 和 MCP 命令。然后推荐一个命令列表，供你添加到权限允许列表中。

使用它来优化权限设置，避免不必要的权限提示，尤其是如果你不使用自动模式的话。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/2.png" alt="Boris Cherny 谈 /fewer-permission-prompts 技能" width="50%" /></a>

---

## 3/ 回顾

Anthropic 本周早些时候推出了**回顾**功能，为 Opus 4.7 做准备。回顾是代理所做工作和下一步计划的简短摘要。

当返回一个几分钟或几小时前开始的长时间运行的会话时，非常有用：

```
* 思考了 6 分 27 秒

* 回顾：修复提交后文字偏移 bug。样式闪烁部分
  已作为 PR #29869 发布（自动合并已开启，已发布到 stamps）。下一步：
  我需要一个屏幕录制来捕捉 `cc -c` 上剩余的横向重排
  以针对那个独立的原因。（在 /config 中禁用回顾）
```

如果你不需要回顾，可以在 `/config` 中禁用它。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/3.png" alt="Boris Cherny 谈回顾" width="50%" /></a>

---

## 4/ 专注模式

Boris 一直很喜欢 CLI 中的新**专注模式**，它隐藏所有中间工作，只专注于最终结果。模型已经达到了他通常信任它运行正确命令和做出正确编辑的程度。他只看最终结果。

使用 `/focus` 切换开关。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/4.png" alt="Boris Cherny 谈专注模式" width="50%" /></a>

---

## 5/ 配置你的努力程度

Opus 4.7 使用**自适应思考**而非思考预算。要调节模型思考更多或更少，请调节努力程度。

- **较低努力** — 更快的响应和更少的 token 使用
- **较高努力** — 最高的智能和能力

滑块呈现五个级别：`low` · `medium` · `high` · `xhigh` · `max` — 左侧为速度，右侧为智能。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/5.png" alt="Boris Cherny 谈努力程度" width="50%" /></a>

---

## 6/ 为 Claude 提供验证其工作的方法

最后，确保 Claude 有办法验证其工作。这一直很重要 — 现在 4.7 能发挥出 Claude 的 2-3 倍能力，所以比以往任何时候都更重要。

验证方式因任务而异：

- **后端工作** — 让 Claude 运行你的服务器/服务进行端到端测试
- **前端工作** — 使用 [Claude Chromium 扩展](https://code.claude.com/docs/en/chrome) 让 Claude 能够控制你的浏览器
- **桌面应用** — 使用 Computer Use

Boris 现在的提示看起来像 `Claude do blah blah /go`，其中 `/go` 是一个技能：

1. 使用 bash、浏览器或 computer use 进行端到端测试
2. 运行 `/simplify`
3. 提交 PR

对于长时间运行的工作，验证更为重要 — 当你回来查看任务时，你知道代码是有效的。

<a href="https://x.com/bcherny"><img src="assets/boris-26-4-16/6.png" alt="Boris Cherny 谈验证" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 4 月 16 日](https://x.com/bcherny)
