# Squash 合并与 PR 大小分布 — Boris Cherny 的技巧

总结 Boris Cherny（[@bcherny](https://x.com/bcherny)），Claude Code 的创建者，于 2026 年 3 月 25 日分享的洞见。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code 最佳实践</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 1/ 单日 266 次贡献 — 始终 Squash

Boris 分享了他的 GitHub 贡献图，显示 **3 月 24 日有 266 次贡献** — 来自 **141 个 PR，始终 squash**，每个 PR 的中位数为 **118 行**。

- Squash 合并将分支上的所有提交合并为目标分支上的单个提交 — 保持历史记录整洁和线性
- 每个 PR = 一个提交，便于回滚整个功能，并简化 `git bisect`
- 在高速度的 AI 辅助工作流（141 个 PR/天）中，squash 是务实的选择 — 分支内的"修复 lint"、"试试这个"等单个提交只是噪音

<a href="https://x.com/bcherny/status/2038552880018538749"><img src="assets/boris-26-3-25/1.png" alt="Boris Cherny — 266 次贡献，始终 squash" width="50%" /></a>

---

## 2/ PR 大小分布 — 保持 PR 小型化

Boris 分享了这 141 个 PR 的大小分布，总计 **45,032 行变更**（新增 + 删除）：

| 指标 | 行数（新增+删除） | 含义 |
|--------|---------------:|---------|
| **p50** | **118** | 中位数 PR 大小 — 一半的 PR 在 118 行或以下 |
| p90 | 498 | 90% 的 PR 在 500 行以下 |
| **p99** | **2,978** | 只有约 1 个 PR 超过约 3K 行 |
| 最小值 | 2 | 最小的 PR — 一个快速的 2 行修复 |
| 最大值 | 10,459 | 最大的单个 PR — 可能是迁移或生成的代码 |

- **中位数 118 行**意味着大多数 PR 专注且可审查，即使在每天 141 个 PR 的情况下也是如此
- 分布严重右偏 — 偶尔的大 PR 是不可避免的（批量重命名、迁移），但常态是小而精
- 小型 PR 降低合并冲突风险，更易于审查，并与 squash 合并完美配合，实现干净的回滚

<a href="https://x.com/bcherny/status/2038552880018538749"><img src="assets/boris-26-3-25/2.png" alt="Boris Cherny — PR 大小分布表" width="50%" /></a>

---

## 来源

- [Boris Cherny (@bcherny) 在 X 上 — 2026 年 3 月 25 日](https://x.com/bcherny)
