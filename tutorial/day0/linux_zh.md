# Linux 安装

[返回第 0 天](README.md)

## 前置条件

你需要 **Node.js v18 或更高版本**和 **npm**。

## 步骤 1：安装 Node.js

### 选项 A：通过 nodejs.org 下载页面配合 fnm（推荐）

**fnm**（Fast Node Manager）是 Node.js 官方推荐的版本管理器。它快速、轻量，并且如果以后需要，可以轻松切换 Node 版本。

1. 打开浏览器，访问 [nodejs.org/en/download](https://nodejs.org/en/download)。

2. 你会看到一行下拉菜单，显示：**"Get Node.js® vXX.XX.X (LTS) for __ using __ with __"**。按如下方式设置下拉菜单：

   | 下拉菜单 | 选择 |
   |----------|--------|
   | 版本 | **vXX.XX.X (LTS)** — 保持默认的 LTS 版本，不要更改 |
   | 操作系统 | **Linux** |
   | 包管理器 | **fnm**（在"Recommended (Official)"下） |
   | 包格式 | **npm** — 保持默认 |

3. 页面会显示你需要运行的确切命令。打开终端并复制粘贴它们。看起来大概像这样：

   ```bash
   # 步骤 1 — 安装 fnm
   curl -fsSL https://fnm.vercel.app/install | bash

   # 步骤 2 — 重启终端或重新加载 shell 配置文件
   source ~/.bashrc   # 或者：source ~/.zshrc（如果你使用 zsh）

   # 步骤 3 — 安装 Node.js
   fnm install 24   # 页面会显示确切的版本号
   ```

   > 版本号可能与上述不同——始终使用网站上显示的内容。

4. **关闭并重新打开终端**（或运行上面的 `source` 命令），以便 `fnm`、`node` 和 `npm` 可用。

> **为什么用 fnm？** 它在 Node.js 下载页面上属于"Recommended (Official)"类别。与 nvm 一样，它将 Node 安装到你的主目录，因此 npm 全局安装永远不需要 `sudo`——但 fnm 快得多（用 Rust 编写），并且在 Windows、macOS 和 Linux 上的工作方式相同。

### 选项 B：使用发行版的包管理器

这样更快，但可能会安装较旧版本的 Node.js。**安装后检查版本**——如果低于 v18，请改用选项 A。

**Ubuntu / Debian：**

```bash
sudo apt update
sudo apt install -y nodejs npm

# 检查版本
node --version   # 必须是 v18 或更高版本
```

**Fedora：**

```bash
sudo dnf install -y nodejs npm
```

**Arch Linux：**

```bash
sudo pacman -S nodejs npm
```

### 选项 C：NodeSource（通过 apt 获取最新 LTS，无需 nvm）

对于希望在不使用 nvm 的情况下获取最新 LTS 的 Ubuntu/Debian 用户：

```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs
```

## 步骤 2：验证 Node.js

```bash
node --version
npm --version
```

两者都应打印版本号。`node --version` 必须显示 v18.x 或更高版本。

## 步骤 3：安装 Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

> **权限错误？**
> - 如果你使用了 **fnm** 或 **nvm**：不应该发生此错误。检查它是否处于活动状态（`which node` 应指向你主目录中的路径，而不是 `/usr/...`）。
> - 如果你使用了系统安装：使用 `sudo npm install -g @anthropic-ai/claude-code` 或修复 npm 的全局目录权限：
>   ```bash
>   mkdir -p ~/.npm-global
>   npm config set prefix '~/.npm-global'
>   echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
>   source ~/.bashrc
>   ```

## 步骤 4：验证 Claude Code

```bash
claude --version
```

你应该看到 Claude Code 版本号被打印出来。现在返回 [README.md](README.md) 进行身份验证设置。

---

## 注意事项

- **WSL（Windows Subsystem for Linux）：** 本指南在 WSL 内部同样适用。只需在 WSL 终端中执行这些步骤即可。
- **PATH 问题：** 如果安装后找不到 `claude`，请确保 npm 的全局 bin 目录在你的 PATH 中。运行 `npm config get prefix`——该路径的 `bin/` 子目录需要位于你的 PATH 中。
