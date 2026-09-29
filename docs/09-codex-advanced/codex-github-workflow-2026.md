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

> 口径：OpenAI 开发者文档与官方动态，2026 年。

过去用 AI 辅助编程，流程多是「在网页端粘贴代码」或「在 IDE 内修改文件」。现在 Codex 直接接入 GitHub：在 PR 评论区输入 `@codex review`，它即可在当前页面提交一份标准 GitHub review。

核心特性如下：

1. **@codex review**：在 PR 评论区直接触发，原地返回审查结果，无需跳转外部页面。
2. **聚焦 P0/P1 问题**：默认只检查正确性、安全性与稳定性缺陷，不纠缠代码格式。
3. **全流程覆盖**：支持从 issue 接任务、改代码、提交到创建 PR。

## 审 PR：为什么聚焦 P0/P1

团队做 code review 的典型痛点在于 PR 积压过多、关键风险容易被漏看、反复修改拉长周期。Codex 的定位是承担第一轮筛查，优先识别高优先级问题。

它默认聚焦影响正确性、安全性和稳定性的 P0/P1 问题，不抓格式和拼写，避免在 review 评论区制造琐碎噪音。对工程团队而言，无效反馈往往比漏检更影响协作效率。

协作方式上，通常由 AI 负责第一轮广度筛查，人工负责第二轮业务逻辑与深度把关。这与[代码审查实战](../03-codex-tutorials/codex-code-review-2026.md)中的双闸机制一致，区别仅在于第一道检查从本地 `/review` 移到了仓库内的 `@codex`。

## 全流程扩展：从审 PR 到接 issue

官方动态展示的核心能力包括：**Review issues、Address feedback、Commit changes、Open pull requests**。对应完整执行链路：

1. 从 issue 描述理解任务需求
2. 根据 review 反馈继续修改代码
3. 提交代码变更
4. 主动创建 PR

这使 Codex 在 GitHub 里的角色从单点审查延伸到任务执行：以 issue 为输入，以 PR 为交付出口，在仓库内独立完成修改循环。

## 三条落地建议

- **从 review 起步**：先用 @codex 做 PR 的第一轮筛查，团队磨合顺畅后再放开 issue 任务处理。
- **权限渐进**：初期仅开放只读与评论权限；允许接任务时限定在独立分支提交，合并权限始终由人工把控。
- **与 CI 明确分工**：@codex 负责代码逻辑与安全性等语义层审查，CI 负责构建、单测与 lint 等自动化检查，二者各司其职。

## FAQ

Q: @codex review 消耗我的 ChatGPT 额度吗？

A: GitHub 集成的计量方式以官方文档为准；企业与团队场景通常走组织级配置。

Q: 私有仓库能用吗？

A: 取决于仓库的集成配置与权限，安装 Codex GitHub App 时按提示授权即可。

Q: 它会把 review 发成「需要修改」吗？

A: 它输出标准 GitHub review 结构，按严重度给出结论；因聚焦 P0/P1，通常只在发现实质问题时标记要求修改。

Q: 和 Routines / 定时任务是什么关系？

A: 二者互补：GitHub 集成响应仓库事件（事件驱动），桌面版 Automations 按计划时间执行（时间驱动），覆盖不同自动化场景。

## 相关阅读

- [Codex 代码审查实战：/review 与清单（2026）](../03-codex-tutorials/codex-code-review-2026.md)
- [Codex 定时任务实战（2026）](codex-automations-tasks-2026.md)
- [Codex Security：安全代理（2026）](codex-security-agent-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=09-codex-advanced) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=09-codex-advanced)
