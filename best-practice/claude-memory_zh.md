# Claude 记忆

通过 CLAUDE.md 文件的持久上下文 — 如何编写它们以及在单体仓库中如何加载。

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code Best Practice</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

## 1. 编写好的 CLAUDE.md

一个结构良好的 CLAUDE.md 是提高 Claude Code 对您项目输出质量的最有效方式。Humanlayer 有一份优秀的指南，涵盖应包含什么、如何结构以及常见陷阱。

- [Humanlayer - Writing a good Claude.md](https://www.humanlayer.dev/blog/writing-a-good-claude-md)

---

## 2. 大型单体仓库中的 CLAUDE.md

在单体仓库中使用 Claude Code 时，了解 CLAUDE.md 文件如何加载到上下文中对于有效组织项目指令至关重要。

<p align="center">
  <a href="https://x.com/bcherny/status/2016339448863355206"><img src="assets/claude-memory/claude-memory-monorepo.jpg" alt="CLAUDE.md 在单体仓库中的加载" width="600"></a>
</p>

### 两种加载机制

Claude Code 使用两种不同的机制来加载 CLAUDE.md 文件：

#### 祖先加载（沿目录树向上）

当您启动 Claude Code 时，它会从当前工作目录**向上**向文件系统根目录遍历，并沿途加载找到的每个 CLAUDE.md。这些文件在**启动时立即加载**。

#### 后代加载（沿目录树向下）

当前工作目录下子目录中的 CLAUDE.md 文件**在启动时不会加载**。它们仅在 Claude 在会话期间读取这些子目录中的文件时才会被包含。这被称为**懒加载**。

### 单体仓库结构示例

考虑一个典型的分隔不同组件的单体仓库：

```
/mymonorepo/
├── CLAUDE.md          # 根级指令（所有组件共享）
├── frontend/
│   └── CLAUDE.md      # 前端特定指令
├── backend/
│   └── CLAUDE.md      # 后端特定指令
└── api/
    └── CLAUDE.md      # API 特定指令
```

### 场景 1：从根目录运行 Claude Code

当您从 `/mymonorepo/` 运行 Claude Code 时：

```bash
cd /mymonorepo
claude
```

| 文件 | 启动时加载？ | 原因 |
|------|-------------------|--------|
| `/mymonorepo/CLAUDE.md` | 是 | 这是您的当前工作目录 |
| `/mymonorepo/frontend/CLAUDE.md` | 否 | 仅在您读取/编辑 `frontend/` 中的文件时加载 |
| `/mymonorepo/backend/CLAUDE.md` | 否 | 仅在您读取/编辑 `backend/` 中的文件时加载 |
| `/mymonorepo/api/CLAUDE.md` | 否 | 仅在您读取/编辑 `api/` 中的文件时加载 |

### 场景 2：从组件目录运行 Claude Code

当您从 `/mymonorepo/frontend/` 运行 Claude Code 时：

```bash
cd /mymonorepo/frontend
claude
```

| 文件 | 启动时加载？ | 原因 |
|------|-------------------|--------|
| `/mymonorepo/CLAUDE.md` | 是 | 这是一个祖先目录 |
| `/mymonorepo/frontend/CLAUDE.md` | 是 | 这是您的当前工作目录 |
| `/mymonorepo/backend/CLAUDE.md` | 否 | 目录树的不同分支 |
| `/mymonorepo/api/CLAUDE.md` | 否 | 目录树的不同分支 |

### 关键要点

1. **祖先始终在启动时加载** — Claude 沿目录树向上遍历并加载找到的所有 CLAUDE.md 文件。这确保您始终可以访问根级的、仓库范围的指令。

2. **后代懒加载** — 子目录的 CLAUDE.md 文件仅在与这些子目录中的文件交互时加载。这防止了不相关的上下文膨胀您的会话。

3. **同级从不加载** — 如果您在 `frontend/` 中工作，`backend/CLAUDE.md` 或 `api/CLAUDE.md` 不会加载到上下文中。

4. **全局 CLAUDE.md** — 您还可以在个人文件夹的 `~/.claude/CLAUDE.md` 中放置一个 CLAUDE.md，它适用于所有 Claude Code 会话，无论项目如何。

### 这种设计为何适用于单体仓库

- **共享指令向下传播** — 根级 CLAUDE.md 包含适用于任何地方的仓库范围约定、编码标准和通用模式。

- **组件特定指令保持隔离** — 前端开发者不需要后端特定的指令占用他们的上下文，反之亦然。

- **上下文得到优化** — 通过懒加载后代的 CLAUDE.md 文件，Claude Code 避免了在启动时加载可能数百 KB 的不相关指令。

### 最佳实践

1. **将共享约定放在根级 CLAUDE.md 中** — 编码标准、提交信息格式、PR 模板以及其他仓库范围的指南。

2. **将组件特定指令放在组件的 CLAUDE.md 中** — 框架特定的模式、组件架构、该组件独有的测试约定。

3. **使用 CLAUDE.local.md 存放个人偏好** — 将其添加到 `.gitignore` 中，用于不应与团队共享的指令。

---

## 来源

- [Claude Code Documentation - How Claude Looks Up Memories](https://code.claude.com/docs/en/memory#how-claude-looks-up-memories)
- [Boris Cherny on X - Clarification on CLAUDE.md Loading](https://x.com/bcherny/status/2016339448863355206)
- [Humanlayer - Writing a good Claude.md](https://www.humanlayer.dev/blog/writing-a-good-claude-md)
