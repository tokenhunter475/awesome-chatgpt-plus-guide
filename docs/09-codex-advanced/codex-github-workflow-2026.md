---
title: "在 GitHub 里 @codex：从审 PR 到接 issue，AI 原生协作现场（2026）"
description: "Codex 的 GitHub 集成全解：PR 评论区 @codex review 直接出标准审查（默认聚焦 P0/P1 高优先级问题），新能力扩展到从 issue 接任务、回应反馈、提交代码、开 PR。GitHub 正在变成 AI 可直接参与协作的工作现场。"
keywords:
  - Codex GitHub
  - @codex review
  - AI 代码审查 GitHub
  - Codex PR 审查
  - GitHub AI 集成
  - Codex issue
updated: 2026-08-20
---

# 在 GitHub 里 @codex：从审 PR 到接 issue，AI 原生协作现场（2026）

> 口径:OpenAI 开发者文档与官方动态,2026 年。

过去用 AI 辅助编程的路径是「打开 ChatGPT 贴代码」;后来变成「IDE 里让 AI 改文件」;现在,Codex 直接住进了 GitHub——在 PR 评论区敲一句 `@codex review`,它像一个真实 reviewer 一样,原地交一份标准 GitHub review。

先说结论：

1. **@codex review**:PR 评论区触发,直接回标准审查,不跳外部页面。
2. 聪明的默认设计:**只聚焦 P0/P1 级问题**(正确性/安全/稳定性),不挑格式毛病。
3. 能力正扩展到全流程:**从 issue 接任务 → 改代码 → 提交 → 开 PR**。

## 审 PR:为什么 P0/P1 聚焦很聪明

团队 code review 的真实痛点:PR 太多看不完、reviewer 只顾大问题小问题没人理、来回改三轮节奏拖死。Codex 进场做**第一轮筛查**,把「高优先级风险」先标出来。

它默认聚焦 P0/P1——真正影响正确性、安全性和稳定性的问题,而不是到处挑格式和拼写。这个设计直接避开了 AI review 最大的翻车道:**把 review 区变成噪音现场**。工程团队不怕 AI 不会挑错,怕它太爱挑无关紧要的错。

配合姿势:AI 做第一轮(广度),人做第二轮(深度+业务判断)——和[代码审查实战](../03-codex-tutorials/codex-code-review-2026.md)里的双闸结构完全一致,只是第一闸从本地 `/review` 换成了仓库内 `@codex`。

## 更大的图:从审 PR 到接 issue

官方动态给出的新能力四件套:**Review issues、Address feedback、Commit changes、Open pull requests**。翻译过来:

1. 从 issue 描述理解任务
2. 读完 review 意见继续改
3. 提交代码
4. 自己开 PR

这意味着 Codex 的 GitHub 角色从「审查助手」变成「执行代理」——issue 是任务入口,PR 是交付出口,中间的循环它自己走。GitHub 从「代码托管平台」变成「AI 原生协作现场」,这就是 2026 年 AI 编程的主战场转移。

## 用起来的三条建议

- **从 review 起步**:先让 @codex 做 PR 第一轮筛查,团队适应后再放开 issue 接任务
- **权限渐进**:初期只给读+评论;接任务功能给到独立分支,合并权留在人手里
- **和 CI 分工**:@codex 管语义层审查(逻辑/安全),CI 管机械检查(构建/测试)——两者不重复

## FAQ

Q: @codex review 消耗我的 ChatGPT 额度吗?

A: GitHub 集成的计量方式以官方文档为准;企业/团队场景通常走组织级配置。

Q: 私有仓库能用吗?

A: 取决于仓库的集成配置与权限,安装 Codex GitHub App 时按提示授权。

Q: 它会把 review 发成「需要修改」吗?

A: 它输出标准 GitHub review 结构,按问题的严重度给结论;P0/P1 聚焦意味着大多数时候它只标真问题。

Q: 和 Routines/定时任务什么关系?

A: 互补:GitHub 集成响应仓库事件(事件驱动),桌面版 Automations 按时间跑(时间驱动)——两套触发器覆盖不同场景。

## 相关阅读

- [Codex 代码审查实战：/review 与清单（2026）](../03-codex-tutorials/codex-code-review-2026.md)
- [Codex 定时任务实战（2026）](codex-automations-tasks-2026.md)
- [Codex Security：安全代理（2026）](codex-security-agent-2026.md)
