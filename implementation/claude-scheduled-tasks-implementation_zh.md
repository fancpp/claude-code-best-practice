# Scheduled Tasks 实现

![最后更新](https://img.shields.io/badge/最后更新-2026年3月10日-white?style=flat&labelColor=555)

<table width="100%">
<tr>
<td><a href="../">← 返回 Claude Code Best Practice</a></td>
<td align="right"><img src="../!/claude-jumping.svg" alt="Claude" width="60" /></td>
</tr>
</table>

---

<a href="#loop-demo"><img src="../!/tags/implemented-hd.svg" alt="已实现"></a>

`/loop` 技能用于按 cron 间隔调度重复任务。以下是 `/loop 1m "tell current time"` 的演示——一个简单的重复任务，每分钟触发一次。

---

## Loop 演示

### 1. 调度任务

<p align="center">
  <img src="assets/impl-loop-1.png" alt="/loop 1m tell current time — 调度和 cron 设置" width="100%">
</p>

`/loop 1m "tell current time"` 解析间隔（`1m` → 每分钟一次），创建 cron 作业，并确认调度。关键要点：

- Cron 的最小粒度是 **1 分钟** — `1m` 映射为 `*/1 * * * *`
- 重复任务 **3 天后自动过期**
- 作业是**会话范围的**——它们仅存在于内存中，Claude 退出时即停止
- 随时取消：`cron cancel <job-id>`

---

### 2. Loop 运行中

<p align="center">
  <img src="assets/impl-loop-2.png" alt="每分钟触发一次的重复任务" width="100%">
</p>

任务每分钟触发一次，运行 `date` 并报告当前时间。每次迭代会触发异步的 **UserPromptSubmit** 和 **Stop** 钩子——与本仓库中用于声音通知的钩子系统相同。

---

## ![如何使用](../!/tags/how-to-use.svg)

```bash
$ claude
> /loop 1m "tell current time"
> /loop 5m /simplify
> /loop 10m "check deploy status"
```

---

## ![如何实现](../!/tags/how-to-implement.svg)

`/loop` 是 Claude Code 的内置技能——无需设置。它底层使用 cron 工具（`CronCreate`、`CronList`、`CronDelete`）来管理重复调度。
