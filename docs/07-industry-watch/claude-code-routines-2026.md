---
title: "Claude Code Routines：AI 编程从「副驾驶」到「值班同事」（2026）"
description: "Anthropic 为 Claude Code 推出 Routines：可按计划、API 调用或 GitHub 事件自动触发，运行在 Anthropic 托管设施上，电脑关了也继续跑。AI 编程工具正在从交互式助手变成云端软件工程代理。"
keywords:
  - Claude Code Routines
  - AI 自动化编程
  - Claude Code 定时任务
  - 云端 AI 编程
  - AI 值班
  - 研发自动化
updated: 2026-08-20
---

# Claude Code Routines：AI 编程从「副驾驶」到「值班同事」（2026）

> 事实口径:2026 年中上线,功能细节以 Anthropic 官方文档为准。

2026 年,AI 编程工具圈出现了一个新物种级的功能:Claude Code 的 **Routines**。它把「人在终端里盯着用」的编程助手,升级成了**可以被预先配置、自动触发、持续执行的任务系统**——你下班关机,它还在云端值班。

先说结论：

1. Routines 三种触发方式:**定时执行、API 调用、GitHub 事件**(比如有 PR 进来就自动跑)。
2. 跑在 **Anthropic 托管的基础设施**上——本地电脑关机,任务照跑。
3. 意义:AI 编程从「你叫它才动」变成「它自己知道什么时候该动」。

## 它解决什么问题

此前的 AI 编程(包括 Codex 的云端任务)本质都是**你发起、它执行**:一次一个任务,跑完就结束。而真实的研发流程里有大量**周期性、事件性**的活:

- 每天早上跑一遍依赖检查,有漏洞就提 issue
- 每次有 PR,自动做一遍代码审查初筛
- 每周自动生成变更日志、同步文档

这些活以前要么靠 CI 脚本(死板),要么靠人肉(烦)。Routines 的答案:**让 AI Agent 挂在事件流上,按需自动醒来干活**。审查怎么做、日志怎么写,它自己会判断——这是脚本做不到的。

## 和已有东西的区别

| | CI/CD 脚本 | AI 云端任务 | Routines |
|---|---|---|---|
| 触发 | 定时/事件 | 手动 | 定时/事件/自动 |
| 执行内容 | 写死的脚本 | 单次任务 | 持续的智能体任务 |
| 运行位置 | 你的服务器 | 云端沙盒 | Anthropic 托管设施 |
| 判断力 | 无 | 有(单次) | 有(持续+事件驱动) |

一句话:CI 是闹钟,Routines 是值班的工程师。**竞争焦点从「谁补全准」变成了「谁能接住整个研发流程」**——Anthropic 想占的不只是 IDE 入口,是研发自动化的调度层。

## 对你意味着什么

- **重复性维护活**(巡检、修复、文档同步)有了新去处:配置一次,持续运行
- **团队视角**:AI 从工具变成流程里的一个「角色」,权限和审计要想清楚(见[数据安全](../00-ai-fundamentals/ai-data-security-2026.md)的企业段)
- **Codex 用户**:OpenAI 侧的对应物是 GitHub 集成 + 云端任务的组合,方向一致,形态不同(见[Codex 入门](../03-codex-tutorials/codex-getting-started-2026.md))

冷静一句:自动化程度越高,**验证环节越重要**。让 AI 值班可以,值完班的产出还是要有验收——[工作流实战](../03-codex-tutorials/codex-workflow-guide-2026.md)里「人工验收不可替代」那条,在值班时代只会更重要。

## FAQ

Q: Routines 和定时跑个脚本有什么本质区别?

A: 脚本只会做写死的事;Routines 是智能体任务,面对「这次 PR 改了什么」能自己判断怎么做。灵活性和适用范围不在一个量级。

Q: 它一直跑,费用怎么算?

A: 托管运行的计费以官方定价为准。配置前设好预算上限——自动化的账单纪律见[血的教训](../06-api-and-relays/ai-pitfalls-lessons-2026.md)的深夜脚本故事。

Q: 电脑关机真的能跑?

A: 能,任务在 Anthropic 的托管设施上执行,和你本地设备无关——这也是它和本地 CLI 的本质差异。

Q: 会不会自动改坏代码?

A: 权限配置决定它能动什么。生产环境建议只给读权限 + 提 issue/PR,合并仍由人决定。

## 相关阅读

- [Claude Code 官方作者亲列的 15 个被低估功能（2026）](claude-code-underrated-features-2026.md)
- [Codex 工作流实战：从需求到上线（2026）](../03-codex-tutorials/codex-workflow-guide-2026.md)
- [AI Agent 是什么？和普通 AI 对话的区别（2026）](../00-ai-fundamentals/what-is-ai-agent-2026.md)
