---
description: 通过并行研究全部 5 个技能集合仓库来更新技能集合表格
---

# 工作流 — 技能集合

通过并行研究 5 个仓库来更新 `README.md` 中的技能集合表格。启动研究代理，合并结果，展示更改，经批准后更新表格。

---

## 5 个仓库

| # | 仓库 | 所有者 |
|---|------|-------|
| 1 | `anthropics/skills` | Anthropic（官方） |
| 2 | `wshobson/agents` | William Shobson |
| 3 | `mattpocock/skills` | Matt Pocock |
| 4 | `K-Dense-AI/scientific-agent-skills` | K-Dense-AI |
| 5 | `VoltAgent/awesome-agent-skills` | VoltAgent（精选 awesome 列表） |

---

## 表格格式

README 表格包含以下列：

```markdown
| Name | ★ | <img src="!/tags/s.svg" height="14"> |
```

- **Name**: `[Short Name](github-url)` — 使用仓库的短名称（例如 `mattpocock/skills`，或者如果所有者就是项目名称则直接使用 `skills`），而非完整的 owner/repo，除非有歧义
- **★**: 星数四舍五入到 `k`（例如 125k、35k、1.2k）。不足 1000 显示确切数字
- **Skill 数量**: 仅显示数字。对于技能是*链接*而非文件的精选列表，使用 `N+ (curated list)` 格式

**排序方式**：按星数降序排列（最高的在前）。

---

## 阶段 0：读取当前状态

读取以下文件：

1. `README.md` — `## 🧰 SKILL COLLECTIONS` 表格（注意当前的星数和技能数量）
2. `changelog/skill-collections/changelog.md` — 以前的变更日志条目（可能尚不存在）

---

## 阶段 1：启动研究代理

**立即**启动一个覆盖全部 5 个仓库的 `development-workflows-research-agent`。（现有研究代理是通用的 — 它可以为任何仓库统计技能/星数等。）

> 研究以下 5 个 Claude Code **技能集合**仓库。每个主要是 `SKILL.md` 文件的库，而非完整的工作流方法论。
>
> **仓库 1: anthropics/skills** (https://github.com/anthropics/skills) — Anthropic 官方技能仓库
> **仓库 2: wshobson/agents** (https://github.com/wshobson/agents) — 插件范围的技能（技能嵌套在领域插件下）
> **仓库 3: mattpocock/skills** (https://github.com/mattpocock/skills) — 面向 TypeScript
> **仓库 4: K-Dense-AI/scientific-agent-skills** (https://github.com/K-Dense-AI/scientific-agent-skills) — 科学/研究垂直领域
> **仓库 5: VoltAgent/awesome-agent-skills** (https://github.com/VoltAgent/awesome-agent-skills) — 精选 awesome 列表（链接到外部技能，而非仓库中的 SKILL.md 文件）
>
> 对于**每个**仓库，返回：
>
> 1. **Stars** — 使用 GitHub API `https://api.github.com/repos/{owner}/{repo}`，读取 `stargazers_count`。四舍五入到 `k`。
> 2. **Skill 数量** — 通过 GitHub git tree API 统计仓库中的 `SKILL.md` 文件数：
>    `https://api.github.com/repos/{owner}/{repo}/git/trees/HEAD?recursive=1` 并搜索路径中的 `SKILL.md`。
>    - 对于 `wshobson/agents`：技能嵌套在 `plugins/<domain>/skills/` 内 — 统计所有插件中的所有 SKILL.md。
>    - 对于 `VoltAgent/awesome-agent-skills`：统计 README.md 中*列出*的技能数（例如列表项/表格行）。明确标记为"curated list, not files"。
>    - 对于 `K-Dense-AI/scientific-agent-skills`：`skills/` 下的子目录可能使用 SKILL.md 或 `.md`；统计仓库使用的格式，并报告具体方式。
>    - 对于 `anthropics/skills`：技能位于 `skills/` 下的子目录中，内部包含 `SKILL.md`。
>    - 对于 `mattpocock/skills`：仅包括**活跃**技能，不包括已弃用的技能（如果明显，则同时注明两个数字）。
> 3. **值得注意的变化** — 过去 30 天内是否有重大新增或删除？
>
> 每个仓库返回结构化报告：
> ```
> REPO: anthropics/skills
> STARS: <number>k (<exact>)
> SKILLS: <count> (<file pattern used, e.g., "SKILL.md files via git tree">)
> NOTES: <anything unusual — flat .md vs SKILL.md, deprecated skills, language variants, curated-list disclaimer>
> CHANGES: <changes or "No significant changes">
> CONFIDENCE: <0-1>
> ```

---

## 阶段 2：比较与报告

**等待代理。** 然后将发现结果与当前表格进行比较并展示：

```
Skill Collections — Update Report
══════════════════════════════════

Changes Found:
  <repo>: ★ <old>k → <new>k | skills <old>→<new>
  ...

No Changes:
  <repo>: ✓ (all values match)
  ...

Action Items:
#  | Type   | Action                              | Status
1  | Star   | Update <repo> ★ from Xk to Yk       | NEW/RECURRING
2  | Count  | Update <repo> skills from X to Y    | NEW/RECURRING
3  | Sort   | Move <repo> (rank changed)          | NEW/RECURRING
4  | Add    | New collection candidate: <repo>     | NEW
```

与以前的变更日志条目进行比较，并将项目标记为 `NEW`、`RECURRING` 或 `RESOLVED`。

---

## 阶段 2.5：追加到变更日志

**强制性** — 始终在向用户展示之前执行。

读取 `changelog/skill-collections/changelog.md`，然后**追加**一个新条目。如果文件不存在，则先创建状态图例，然后添加第一个条目。

```markdown
---

## [<YYYY-MM-DD HH:MM AM/PM PKT>] Skill Collections Update

| # | Priority | Type | Action | Status |
|---|----------|------|--------|--------|
| 1 | HIGH/MED/LOW | <type> | <action> | <status> |
```

通过 `TZ=Asia/Karachi date "+%Y-%m-%d %I:%M %p PKT"` 获取时间。状态必须是以下之一：
- `COMPLETE (reason)` | `INVALID (reason)` | `ON HOLD (reason)`

始终追加，从不覆盖。

---

## 阶段 2.6：更新最后更新徽章

**强制性** — 在阶段 2.5 之后执行。

更新 `README.md` 第 4 行的徽章。通过 `TZ=Asia/Karachi date "+%b %d, %Y %-I:%M %p PKT"` 获取时间，进行 URL 编码，替换徽章中的日期。不要将其记录为操作项。

---

## 阶段 3：执行

询问用户：**(1) 全部执行** | **(2) 执行特定项** | **(3) 跳过**

执行时，编辑 `README.md` 中的 `## 🧰 SKILL COLLECTIONS` 表格：
- 逐行更新星数和技能数量
- 保持排序顺序：星数降序（最高的在前）
- 精确匹配现有格式（链接样式、星数的 k 后缀）

---

## 规则

1. **一个研究代理，5 个仓库** — 单条消息，内部并行子请求
2. **绝不猜测** — 仅使用代理提供的数据
3. **不要自动执行** — 先展示报告，等待批准
4. **始终追加变更日志**并**始终更新徽章** — 强制性
5. **按星数降序排序** — 星数最高的在前
6. **统一四舍五入星数** — 使用 `k` 后缀（125k、35k、1.2k）。不足 1000 显示确切数字
7. **Awesome 列表是不同的** — 对于链接到外部技能的仓库（VoltAgent），数量是"README 中列出的项目数"，而非仓库中的文件数；始终标注 `(curated list)`
8. **与以前的变更日志比较** — 将项目标记为 NEW、RECURRING 或 RESOLVED
9. **重用 `development-workflows-research-agent`** — 不要创建新的代理
