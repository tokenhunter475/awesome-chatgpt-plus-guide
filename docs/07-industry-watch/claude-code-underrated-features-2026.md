---
title: "Claude Code 官方作者亲列的 15 个被低估功能（2026）"
description: "2026 年 3 月 30 日 Claude Code 创建者 Boris Cherny 分享了 15 个他认为被严重低估的功能，包括移动端编程、云端会话无缝切换等。本文按「普通人能用上的」优先级整理这份清单。"
keywords:
  - Claude Code 功能
  - Claude Code 技巧
  - Boris Cherny
  - Claude Code 移动端
  - Claude Code 云端会话
  - Claude Code 被低估功能
updated: 2026-08-20
---

# Claude Code 官方作者亲列的 15 个被低估功能（2026）

> 事实口径:2026 年 3 月 30 日 Boris Cherny(Claude Code 创建者)公开分享;功能可用性随版本变化,以官方文档为准。

工具的作者亲自下场说「这 15 个功能你们都低估了」——这种机会不多。2026 年 3 月 30 日,Claude Code 的创建者 Boris Cherny 盘点了 15 个他认为被严重低估的能力,中文圈随后做了广泛解读。这篇按**普通人能用上的优先级**重新整理,顺带标注对应到 Codex 生态的等价能力。

捡要紧的说:

1. 最值得先试的三个:**移动端编程**、**云端会话无缝切换**、**从任何地方恢复会话**。
2. 这份清单的共同主题:Claude Code 不只是终端工具,**是一套跨设备的会话系统**。
3. 用 Codex 的用户别眼红——大部分能力在 Codex 生态有对应(见各条标注)。

## 高频实用组:先试这三个

**移动端编程。** 手机上直接让 Claude Code 干活——不是看代码的玩具,是真的能跑任务。配合云端执行,通勤时也能推进工作。Codex 对应:手机 App 里的 Codex 入口(见[云端任务](../03-codex-tutorials/codex-cloud-tasks-2026.md))。

**云端会话无缝切换。** 电脑上开一个任务,路上用手机接着看进度,回办公室再切回终端——同一个会话,三种设备。Codex 对应:CLI/IDE/网页共享会话(见[IDE 集成](../03-codex-tutorials/codex-ide-integration-2026.md))。

**会话恢复。** 所有会话自动保存,任何时候捡回来继续——包括跨设备。Codex 对应:`/resume` 命令(见[记忆与配置](../03-codex-tutorials/codex-memory-and-config-2026.md))。

## 效率组:用了回不去的那种

- **后台并行任务**:多个任务同时跑,到点收结果(Codex 对应:云端并行任务)
- **上下文管理的自动化**:长会话自动压缩,不用手动操心窗口(见[大模型原理](../00-ai-fundamentals/what-is-llm-2026.md))
- **自定义权限粒度**:哪些操作免确认、哪些必须问,按项目配置(Codex 对应:`/approvals`)
- **检查点回滚**:改坏了回到之前的检查点,不用手动 undo

## 深水组:进阶玩家再看

- hooks 自动化(事件触发自定义脚本)、团队共享配置、与 CI 集成、长任务的自主执行模式等——这些是[智能体平台](../05-ai-toolbox/agent-platforms-guide-2026.md)方向的雏形,适合把 Claude Code 当基础设施用的团队。

## 这份清单的弦外之音

作者亲自强调「被低估」,说明用户用得浅。这不是用户懒,是**工具的进步速度超过了使用习惯的更新速度**——多数人还停留在「对话框里问问题」,而工具已经长成了「跨设备任务系统」。

这条判断对 Codex 用户同样成立:翻一遍 [CLI 教程](../03-codex-tutorials/codex-cli-tutorial-2026.md)的命令表,大概率也有你从没碰过的能力。工具的「隐藏功能」多数不是藏,是我们没空看说明书。

## FAQ

Q: 我是 Codex 用户,值得为此转 Claude Code 吗?

A: 不必为此转。两个生态在快速互相学习,这份清单里的高频功能在 Codex 大多有对应。选型还是看账号门槛和任务口味(见[工具对比](../01-models-and-tools/ai-coding-tools-comparison-2026.md))。

Q: 移动端编程靠谱吗,屏幕那么小?

A: 靠谱的原因恰恰是「你不用写代码」——下达任务、看进度、验收结果,这些操作手机完全够用。真正的代码生产仍在云端/电脑上。

Q: 哪里看完整 15 个功能?

A: 搜「Boris Cherny Claude Code 15」能找到原帖和多方中文解读;细节以 claude.com/docs 官方文档为准。

## 相关阅读

- [Claude Code 快速模式：为速度多付钱（2026）](claude-code-fast-mode-2026.md)
- [Claude Code Routines:AI 编程进入值班时代（2026）](claude-code-routines-2026.md)
- [AI 编程工具对比：Codex vs Claude Code vs Cursor vs Gemini（2026）](../01-models-and-tools/ai-coding-tools-comparison-2026.md)
