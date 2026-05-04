# 技能集合变更日志

**状态图例:**

| 状态 | 含义 |
|--------|---------|
| `COMPLETE (原因)` | 已采取行动并成功解决 |
| `INVALID (原因)` | 发现结果不正确、不适用或有意为之 |
| `ON HOLD (原因)` | 行动推迟，等待外部依赖或用户决定 |

---

## [2026-04-28 16:39 PKT] 技能集合更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | LOW | 初始运行 | 在 README 中创建了 SKILL COLLECTIONS 部分，包含 5 个仓库：anthropics/skills (125k/17)、wshobson/agents (35k/152)、mattpocock/skills (33k/17)、K-Dense-AI/scientific-agent-skills (20k/134)、VoltAgent/awesome-agent-skills (19k/1,100+ 精选) | COMPLETE (来自 research-agent 发现的初始播种，2026-04-28 会话) |

---

## [2026-04-29 00:52 PKT] 技能集合更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MEDIUM | 星标 | 将 mattpocock/skills ★ 从 33k 更新为 36k (精确值 36,476) | NEW |
| 2 | MEDIUM | 数量 | 将 mattpocock/skills 技能数量从 17 更新为 18 (添加了 setup-matt-pocock-skills，deprecated/ 文件夹于 2026-04-28 重组) | NEW |
| 3 | LOW | 星标 | 将 wshobson/agents ★ 从 35k 更新为 34k (精确值 34,477 — 略有下降) | NEW |
| 4 | MEDIUM | 排序 | 将 mattpocock/skills 行移到 wshobson/agents 行上方 (因星标变化导致的排名交换) | NEW |
| 5 | LOW | 数量 | 将 VoltAgent/awesome-agent-skills 精选数量从 1,100+ 更新为 930+ (实际 README 要点解析；徽章多报了约 170) | NEW |
| 6 | LOW | 无变化 | anthropics/skills (125k/17) 和 K-Dense-AI/scientific-agent-skills (20k/134) — 值匹配，无需编辑 | COMPLETE (已验证，无漂移) |

---

## [2026-05-01 15:31 PKT] 技能集合更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | MEDIUM | 星标 | 将 anthropics/skills ★ 从 125k 更新为 127k (精确值 126,746) | NEW |
| 2 | HIGH | 星标 | 将 mattpocock/skills ★ 从 36k 更新为 51k (精确值 50,819 — 约 3 天内 +15k 激增，可能为外部推广) | NEW |
| 3 | LOW | 星标 | 将 wshobson/agents ★ 从 34k 更新为 35k (精确值 34,595) | NEW |
| 4 | LOW | 星标 | 将 VoltAgent/awesome-agent-skills ★ 从 19k 更新为 20k (精确值 19,729) | NEW |
| 5 | LOW | 无变化 | 所有 5 个技能数量稳定 (anthropics 17、mattpocock 18、wshobson 152、scientific 134、voltagent 930-curated) | COMPLETE (已验证，无漂移) |
| 6 | LOW | 排序 | 顺序保持不变 — scientific (19,829) 仍以约 100 星优势领先 voltagent (19,729)；无需行重新排序 | COMPLETE (已验证) |

---

## [2026-05-01 16:05 PKT] 技能集合更新

| # | 优先级 | 类型 | 操作 | 状态 |
|---|----------|------|--------|--------|
| 1 | HIGH | 添加 | 在第 4 行（wshobson/agents (35k) 和 scientific-agent-skills (20k) 之间）添加了 addyosmani/agent-skills (27k 星 / 21 个 SKILL.md 文件)；用户请求的手动添加 | COMPLETE (已插入 SKILL COLLECTIONS 表格) |
| 2 | LOW | 备注 | 该仓库具有双重分类 — 同时添加到 DEVELOPMENT WORKFLOWS 表格，因为它提供完整的 /spec → /plan → /build → /test → /review → /ship 生命周期，而不仅仅是 SKILL.md 库 | COMPLETE (已交叉引用) |
