---
title: "Codex Skills 生态盘点：官方技能库、Skill Creator 与值得装的几个（2026）"
description: "Codex Skills 生态现状：官方技能库一键安装、Skill Creator 自造技能、Skill Installer 管安装。盘点 Figma Skill（设计稿转代码并校验 1:1 还原）等实用技能，以及技能生态的三个趋势。"
keywords:
  - Codex Skills 生态
  - Codex 技能库
  - Figma Skill
  - Skill Creator
  - Codex 技能推荐
  - Codex 插件推荐
updated: 2026-08-20
---

# Codex Skills 生态盘点：官方技能库、Skill Creator 与值得装的几个（2026）

> 口径:2026 年 8 月;技能库随版本滚动更新,以产品内列表为准。

[Skills 用法](../03-codex-tutorials/codex-skills-guide-2026.md)介绍了运行机制。这里盘点生态现状：官方技能库现有内容、推荐技能以及自建技能的方法。

1. 技能获取三条路：**官方推荐库一键装、Skill Installer 按需装、Skill Creator 自己造**。
2. 应用最广的是 **Figma Skill**：读取设计稿生成 React+Tailwind，并校验 1:1 还原。
3. 生态趋势：从编写代码扩展到对接外部工具，设计、文档、测试等环节均已接入。

## 三个入口

**官方推荐库。** 桌面版 Skills 界面中由官方维护现成技能，点击 Try 即可安装。官方筛选过的技能兼容性更好，适合入门。

**Skill Installer。** 按需安装通道。在对话中询问「有什么可以安装的技能」，会列出可选技能。这些技能均来自 OpenAI 官方技能库，与界面推荐同源。

**Skill Creator。** 官方提供的技能生成工具。用自然语言描述预期流程，即可生成技能文件。团队中需要反复口头交代的流程，适合用 Skill Creator 固化（判断标准见[Skills 用法](../03-codex-tutorials/codex-skills-guide-2026.md)）。

## 值得关注的几个方向

**设计侧：Figma Skill。** 读取 Figma 设计稿生成 React + Tailwind 代码，**并校验是否 1:1 还原**，提供设计稿转代码后的校验兜底（场景串联见[多模态工作流](../04-multimodal-creation/multimodal-workflow-2026.md)）。

**构建侧：macOS 开发插件。** 提供 SwiftUI/AppKit 场景的专用预设，补充通用助手在 Apple 原生开发上的细节支持（见[macOS 插件篇](codex-macos-plugin-2026.md)）。

**流程侧：自动化技能。** 桌面版 Automations 的定时任务模板（巡检、日报、CI 汇总）采用「技能+触发器」结构：技能定义执行逻辑，触发器定义执行时机（见[定时任务实战](codex-automations-tasks-2026.md)）。

## 技能管理原则

1. **按需装，不囤积**：每个技能都会占用上下文窗口，闲置过多会稀释模型注意力，还可能干扰任务匹配。
2. **先官方后社区**：优先使用经过验证的官方技能；安装第三方技能前需检查其要求的权限。
3. **定期清理**：及时卸载三个月未使用的技能。

## FAQ

Q: 技能要额外付费吗?

A: 技能本身免费，执行任务时照常消耗用量池额度。全库审查等高消耗技能需控制调用频率。

Q: 自己造的技能能分享吗?

A: 技能以文件形式存在，可提交到版本库供团队共享，适合沉淀团队内部的最佳实践。

Q: 技能和安全审查会有冲突吗?

A: 技能定义执行流程，Codex Security 与 @codex review 等安全审查属于独立环节，两者叠加使用互不冲突（见[安全代理](codex-security-agent-2026.md)）。

## 相关阅读

- [Codex Skills 用法：/skills 机制、技能怎么写（2026）](../03-codex-tutorials/codex-skills-guide-2026.md)
- [Codex 桌面版实测（2026）](codex-desktop-app-review-2026.md)
- [Codex 记忆与配置：AGENTS.md（2026）](../03-codex-tutorials/codex-memory-and-config-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=09-codex-advanced) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=09-codex-advanced)
