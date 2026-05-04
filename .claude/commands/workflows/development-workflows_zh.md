---
description: 通过并行研究全部 11 个工作流仓库来更新开发工作流表格
---

# 工作流 — 开发工作流

通过并行研究 11 个仓库来更新 `README.md` 中的开发工作流表格。启动代理，合并结果，展示更改，经批准后更新表格。

---

## 11 个仓库

| # | 仓库 | 所有者 |
|---|------|-------|
| 1 | `github/spec-kit` | GitHub (John Lam / Den Delimarsky) |
| 2 | `Fission-AI/OpenSpec` | Fission-AI (@0xTab) |
| 3 | `humanlayer/humanlayer` | HumanLayer (Dex Horthy) |
| 4 | `affaan-m/everything-claude-code` | Affaan Mustafa |
| 5 | `gsd-build/get-shit-done` | Lex Christopherson |
| 6 | `obra/superpowers` | Jesse Vincent |
| 7 | `garrytan/gstack` | Garry Tan (YC CEO) |
| 8 | `bmad-code-org/BMAD-METHOD` | BMAD Code Org |
| 9 | `EveryInc/compound-engineering-plugin` | Every.to |
| 10 | `Yeachan-Heo/oh-my-claudecode` | Yeachan Heo (@bellman_ych) |
| 11 | `mattpocock/skills` | Matt Pocock |

---

## 表格格式

README 表格包含以下列：

```markdown
| Name | ★ | Workflow | <img src="!/tags/a.svg" height="14"> | <img src="!/tags/c.svg" height="14"> | <img src="!/tags/s.svg" height="14"> |
```

- **Name**: `[Short Name](github-url)` — 使用项目名称，而非 owner/repo
- **★**: 星级数四舍五入到 `k`（例如 98k、10k、4.1k）。不足 1000 显示确切数字
- **Workflow**: 规范的端到端流水线，以 shields.io 徽章从左到右的扁平序列表示，用 ` → ` 连接。每一步都是仓库中实际的命令/技能/代理名称（例如 `/speckit.plan`、`bmad-create-prd`、`subagent-driven-development`）。**仅扁平形式** — 无括号，无英文限定词（"loop"、"per story"、"parallel waves"），无 `+` 连接符。如果某一步骤包含重要的内部子步骤，则将其列为主链中的同级项，并用**黄色（`fff3b0`）**标记为子循环；顶层步骤保持浅蓝色（`ddf4ff`）。跟踪 README 的"使用方式"/"工作流"部分，找到规范的快乐路径：想法 → 规格/计划 → 任务 → 实现 → 审查 → 发布。
- **Agent/Command/Skill 数量**: 仅显示数字（例如 `25`、`0`、`108+`）

### 工作流徽章编码（shields.io）

每一步渲染为一个 **HTML `<img>` 标签，带有 `align="middle"`**（而非 Markdown 图片语法），以使箭头与徽章保持垂直居中。两种背景颜色：

| 颜色 | 十六进制 | 使用时机 |
|---|---|---|
| 浅蓝色 | `ddf4ff` | 顶层工作流步骤 |
| 柔黄色 | `fff3b0` | 子循环步骤（在父步骤内按任务/故事/直到验证通过时重复） |

模板：

```html
<img src="https://img.shields.io/badge/<ENCODED>-ddf4ff" alt="<plain-label>" align="middle">    <!-- 顶层 -->
<img src="https://img.shields.io/badge/<ENCODED>-fff3b0" alt="<plain-label>" align="middle">    <!-- 子循环 -->
```

`align="middle"` 将徽章的垂直中心置于文本基线，从而使 ` → ` 箭头在每个徽章上居中，而非停在徽章底部。如果没有它，箭头在 GitHub 渲染中会明显下坠到徽章下方。

在表格关闭后，**始终包含以下图例**作为单独一行的引用：

```markdown
> *注：黄色标签是子循环 — 在父步骤内重复的步骤（例如按任务、按故事，或直到验证条件通过）。*
```

URL 中 `<ENCODED>` 部分的编码规则：

| 输入字符 | 编码结果 |
|---|---|
| `/`（前导斜杠） | `%2F` |
| `-`（字面连字符） | `--` |
| `_`（字面下划线） | `__` |
| ` `（空格） | `_` |
| `+` | `%2B` |
| `.` 和 `:` | 保持不变 |

示例：
- `/grill-me` → `%2Fgrill--me`
- `/speckit.plan` → `%2Fspeckit.plan`
- `/opsx:propose` → `%2Fopsx:propose`
- `bmad-create-epics-and-stories` → `bmad--create--epics--and--stories`

用字面箭头 ` → `（空格-箭头-空格）连接步骤，**位于**一个 img 标签的结束 `>` 和下一个的开始 `<` **之间**。

**不要**将子步骤包裹在括号中或用英文标注（"loop"、"per story"、"+"、"parallel waves"）。如果某一步骤有内部循环，只需在扁平链中将内部步骤名称列为同级项。

**排序方式**：按星数降序排列（最高的在前）。

---

## 阶段 0：读取当前状态

读取以下文件：

1. `README.md` — `## ⚙️ DEVELOPMENT WORKFLOWS` 表格（注意当前的星数、工作流流水线、数量）
2. `changelog/development-workflows/changelog.md` — 以前的变更日志条目

---

## 阶段 1：启动 2 个研究代理

**立即**在**单条消息**中同时启动两个代理（并行）。每个使用 `subagent_type: "development-workflows-research-agent"`。

### 代理 1（4 个仓库）

> 研究以下 4 个 Claude Code 工作流仓库：
>
> **仓库 1: github/spec-kit** (https://github.com/github/spec-kit)
> **仓库 2: affaan-m/everything-claude-code** (https://github.com/affaan-m/everything-claude-code)
> **仓库 3: obra/superpowers** (https://github.com/obra/superpowers)
> **仓库 4: mattpocock/skills** (https://github.com/mattpocock/skills)
>
> 对于**每个**仓库，返回：
>
> 1. **Stars** — 使用 GitHub API `https://api.github.com/repos/{owner}/{repo}`，读取 `stargazers_count`。四舍五入到 `k`。
> 2. **Agent 数量** — 统计 `agents/` 或 `.claude/agents/` 中的 `.md` 文件数。对于 obra，还要统计由 skills 分发的隐式子代理。对于 mattpocock，数量为 0（纯技能仓库）。
> 3. **Skill 数量** — 统计 `skills/` 或 `.claude/skills/` 中的文件夹数。对于 mattpocock，统计仓库根目录下 `skills/` 中的文件夹数。
> 4. **Command 数量** — 统计 `commands/` 或 `.claude/commands/` 中的 `.md` 文件数。对于 spec-kit，统计 `templates/commands/` 中的文件数。对于 mattpocock，数量为 0（技能充当斜杠命令）。
> 5. **Workflow** — 规范的端到端流水线，以步进名称的扁平从左到右序列表示，用 ` → ` 连接。跟踪 README 的"使用方式"/"工作流"部分，找到快乐路径：想法 → 规格/计划 → 任务 → 实现 → 审查 → 发布。使用仓库中实际的命令/技能/代理名称。**仅扁平形式** — 无括号，无英文限定词（"loop"、"per story"、"parallel waves"），无 `+` 连接符。如果某一步骤有内部子步骤，将其列为主链中的同级项。将每一步标记为 `top`（顶层）或 `sub`（子循环，在父步骤内重复），以便编排器为其着色。输出为纯文本 — 编排器会将每个步骤编码为 shields.io HTML img 徽章。
> 6. **值得注意的变化** — 最近有什么重大变化？新的代理/技能/命令、主要版本？
>
> 每个仓库返回结构化报告：
> ```
> REPO: github/spec-kit
> STARS: <number>k
> AGENTS: <count>
> COMMANDS: <count>
> SKILLS: <count>
> WORKFLOW: <step1>(top) → <step2>(top) → <step3>(sub) → ... → <stepN>(top)
> CHANGES: <changes or "No significant changes">
> ```

### 代理 2（7 个仓库）

> 研究以下 7 个 Claude Code 工作流仓库：
>
> **仓库 1: Fission-AI/OpenSpec** (https://github.com/Fission-AI/OpenSpec)
> **仓库 2: humanlayer/humanlayer** (https://github.com/humanlayer/humanlayer)
> **仓库 3: gsd-build/get-shit-done** (https://github.com/gsd-build/get-shit-done)
> **仓库 4: garrytan/gstack** (https://github.com/garrytan/gstack)
> **仓库 5: bmad-code-org/BMAD-METHOD** (https://github.com/bmad-code-org/BMAD-METHOD)
> **仓库 6: EveryInc/compound-engineering-plugin** (https://github.com/EveryInc/compound-engineering-plugin)
> **仓库 7: Yeachan-Heo/oh-my-claudecode** (https://github.com/Yeachan-Heo/oh-my-claudecode)
>
> 对于**每个**仓库，返回：
>
> 1. **Stars** — 使用 GitHub API `https://api.github.com/repos/{owner}/{repo}`，读取 `stargazers_count`。四舍五入到 `k`。
> 2. **Agent 数量** — 统计 `agents/` 或 `.claude/agents/` 中的 `.md` 文件数。对于 BMAD，统计 `src/bmm-skills/` 中的 agent-persona 技能。对于 compound-engineering-plugin，统计 `plugins/compound-engineering/agents/` 所有子目录中的 `.md` 文件数。对于 oh-my-claudecode，统计仓库根目录下 `agents/` 中的 `.md` 文件数。
> 3. **Skill 数量** — 统计 `skills/` 或 `.claude/skills/` 中的文件夹数。对于 gstack，技能是根目录下带有 SKILL.md 的目录。对于 BMAD，统计 `src/bmm-skills/` 和 `src/core-skills/` 中的所有技能。对于 compound-engineering-plugin，统计 `plugins/compound-engineering/skills/` 加上 `plugins/coding-tutor/skills/` 中的文件夹数。对于 oh-my-claudecode，统计仓库根目录下 `skills/` 中的文件夹数。
> 4. **Command 数量** — 统计 `commands/` 或 `.claude/commands/` 中的 `.md` 文件数。对于 GSD，统计 `commands/gsd/` 中的文件数。对于 OpenSpec，统计 `/opsx:*` 命令数。对于 BMAD，数量为 0（命令在安装时生成）。对于 compound-engineering-plugin，统计 `.claude/commands/` 加上 `plugins/coding-tutor/commands/` 中的 `.md` 文件数。对于 oh-my-claudecode，数量为 0（技能充当斜杠命令）。
> 5. **Workflow** — 规范的端到端流水线，以步进名称的扁平从左到右序列表示，用 ` → ` 连接。跟踪 README 的"使用方式"/"工作流"部分，找到快乐路径：想法 → 规格/计划 → 任务 → 实现 → 审查 → 发布。使用仓库中实际的命令/技能/代理名称。**仅扁平形式** — 无括号，无英文限定词（"loop"、"per story"、"parallel waves"），无 `+` 连接符。如果某一步骤有内部子步骤，将其列为主链中的同级项。将每一步标记为 `top`（顶层）或 `sub`（子循环，在父步骤内重复），以便编排器为其着色。输出为纯文本 — 编排器会将每个步骤编码为 shields.io HTML img 徽章。
> 6. **值得注意的变化** — 最近有什么重大变化？新的代理/技能/命令、主要版本？
>
> 每个仓库返回结构化报告：
> ```
> REPO: Fission-AI/OpenSpec
> STARS: <number>k
> AGENTS: <count>
> COMMANDS: <count>
> SKILLS: <count>
> WORKFLOW: <step1>(top) → <step2>(top) → <step3>(sub) → ... → <stepN>(top)
> CHANGES: <changes or "No significant changes">
> ```

---

## 阶段 2：比较与报告

**等待两个代理。** 然后将发现结果与当前表格进行比较并展示：

```
Development Workflows — Update Report
══════════════════════════════════════

Changes Found:
  <repo>: ★ <old>k → <new>k | agents <old>→<new> | commands <old>→<new> | skills <old>→<new>
  <repo>: workflow updated: <old workflow> → <new workflow>
  ...

No Changes:
  <repo>: ✓ (all values match)
  ...

Action Items:
#  | Type        | Action                                | Status
1  | Star        | Update <repo> ★ from Xk to Yk         | NEW/RECURRING
2  | Count       | Update <repo> agents from X to Y      | NEW/RECURRING
3  | Workflow    | Update <repo> workflow pipeline       | NEW/RECURRING
4  | Sort        | Move <repo> (stars changed)           | NEW/RECURRING
```

与以前的变更日志条目进行比较，并将项目标记为 `NEW`、`RECURRING` 或 `RESOLVED`。

---

## 阶段 2.5：追加到变更日志

**强制性** — 始终在向用户展示之前执行。

读取 `changelog/development-workflows/changelog.md`，然后**追加**一个新条目。如果文件不存在，则先创建状态图例，然后添加第一个条目。

```markdown
---

## [<YYYY-MM-DD HH:MM AM/PM PKT>] Development Workflows Update

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

执行时，编辑 `README.md` 中的 `## ⚙️ DEVELOPMENT WORKFLOWS` 表格：
- 逐行更新星数、数量**和工作流列**
- 保持排序顺序：星数降序（最高的在前）
- 精确匹配现有格式（图标、徽章 URL、链接样式）
- 对于工作流列，将代理返回的每个纯文本步骤编码为 shields.io HTML img 徽章，遵循表格格式部分的规定。标记为 `(top)` 的步骤使用 `ddf4ff`，标记为 `(sub)` 的步骤使用 `fff3b0`。用 ` → ` 连接。
- 确保表格后紧跟着图例 `> *注：黄色标签是子循环 — 在父步骤内重复的步骤（例如按任务、按故事，或直到验证条件通过）。*`；如果缺失，请添加。

---

## 规则

1. **同时启动两个代理** — 单条消息，绝不按顺序
2. **绝不猜测** — 仅使用代理提供的数据
3. **不要自动执行** — 先展示报告，等待批准
4. **始终追加变更日志**并**始终更新徽章** — 强制性
5. **按星数降序排序** — 星数最高的在前
6. **工作流徽章使用带有 align="middle" 的 HTML img** — `<img src="https://img.shields.io/badge/<ENCODED>-<COLOR>" alt="<plain-label>" align="middle">`。`align="middle"` 是必需的，以使 ` → ` 箭头与徽章保持垂直居中。两种颜色：顶层步骤使用 `ddf4ff`，子循环步骤使用 `fff3b0`。编码规则：空格用 `_`，连字符用 `--`，下划线用 `__`，`/` 用 `%2F`，`+` 用 `%2B`。点和冒号保持不变。用 ` → ` 连接步骤。当上游仓库中的任何步骤名称发生变化时，始终更新 Workflow 列。
7. **代理、命令、技能是不同的** — 从各自的目录统计，不要混淆
8. **统一四舍五入星数** — 使用 `k` 后缀（98k、10k、4.1k）。不足 1000 显示确切数字
9. **与以前的变更日志比较** — 将项目标记为 NEW、RECURRING 或 RESOLVED
10. **工作流列是强制性的且为扁平形式** — 每行都必须有 Workflow 单元格。跟踪 README 的"使用方式"/规范快乐路径；不要编造虚构的流水线。**无括号、无英文限定词、无 `+` 连接符** — 如果某一步骤有内部子步骤，将其列在扁平链中作为同级项并着色为黄色（`fff3b0`）；顶层步骤保持蓝色（`ddf4ff`）。
11. **子循环图例是强制性的** — 表格后必须立即出现 `> *注：黄色标签是子循环 — 在父步骤内重复的步骤（例如按任务、按故事，或直到验证条件通过）。*` 这一行。如果被删除则恢复；永远不要修改措辞。
