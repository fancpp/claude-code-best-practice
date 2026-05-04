# Windows 安装

[返回第 0 天](README.md)

---

**Node.js**
- 访问 [nodejs.org](https://nodejs.org)
- 点击**"Download Node.js (LTS)"**按钮 — 这会下载 `.msi` 安装程序
- 运行 `.msi` 文件，在向导中点击**下一步**
- 接受默认设置，点击**安装**，等待完成

**验证 Node.js**
- 打开一个**新**终端（PowerShell 或 Windows Terminal）并运行：
  ```powershell
  node --version
  npm --version
  ```

**Claude Code**
- ```powershell
  npm install -g @anthropic-ai/claude-code
  ```
- 如果遇到权限错误，请以**管理员**身份运行终端（右键单击 > 以管理员身份运行）

**验证**
- ```powershell
  claude --version
  ```

---

现在返回 [README.md](README.md) 进行身份验证设置。
