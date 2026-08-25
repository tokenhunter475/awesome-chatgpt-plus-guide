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

[Skills 用法](../03-codex-tutorials/codex-skills-guide-2026.md)讲了机制,这篇盘点生态:官方技能库现在有什么、哪些值得装、自己造技能的门道。

先说结论：

1. 技能获取三条路:**官方推荐库一键装、Skill Installer 按需装、Skill Creator 自己造**。
2. 目前最出圈的技能是 **Figma Skill**:读设计稿→生成 React+Tailwind→校验 1:1 还原。
3. 生态趋势:从「写代码的技能」扩展到「接工具的技能」——设计、文档、测试都在进来。

## 三个入口

**官方推荐库。** 桌面版的 Skills 界面里,官方维护着一批现成技能,点 Try 即装。入门先逛这里——官方筛选过的东西,踩坑率低。

**Skill Installer。** 从官方技能库按需安装的通道。在对话里问它「有什么可以安装的技能」,它会列出可选项——本质上都是从 OpenAI 官方技能库拉取,和界面推荐同源。

**Skill Creator。** 官方提供的「造技能的技能」——用自然语言描述你想要的流程,它帮你生成技能文件。团队里「每个人都会用但每次都要口头交代」的流程,是 Skill Creator 的最佳素材(写技能的方法论见[Skills 用法](../03-codex-tutorials/codex-skills-guide-2026.md)的判断标准)。

## 值得关注的几个方向

**设计侧:Figma Skill。** 生态里口碑最硬的一个:直接读 Figma 设计稿,生成 React + Tailwind 代码,**还校验是否 1:1 还原**。设计稿转代码的完整链路,还原度问题的兜底方案(场景串联见[多模态工作流](../04-multimodal-creation/multimodal-workflow-2026.md))。

**构建侧:macOS 开发插件。** SwiftUI/AppKit 场景的专门预设,补通用助手在 Apple 原生开发上的短板(见[macOS 插件篇](codex-macos-plugin-2026.md))。

**流程侧:自动化的技能化。** 桌面版 Automations 的定时任务模板(巡检/日报/CI 汇总),本质是「技能+触发器」的组合——技能定义干什么,触发器定义什么时候干(见[定时任务实战](codex-automations-tasks-2026.md))。

## 装技能的三条纪律

1. **按需装,别囤**:每个技能占用上下文,装一堆用不上的,稀释注意力还可能干扰任务匹配
2. **先官方后社区**:官方库的技能经过验证;第三方技能看清它要求什么权限再装
3. **定期清**:三个月没用过的技能,卸载——技能也讲究断舍离

## FAQ

Q: 技能要额外付费吗?

A: 技能本身免费,但技能执行的任务照常消耗用量池额度——重活技能(如全库审查)用起来注意频率。

Q: 自己造的技能能分享吗?

A: 技能本质是文件,可以进版本库团队共享——把团队最佳实践做成技能再入库,是最标准的玩法。

Q: 技能和安全审查会有冲突吗?

A: 技能定义「怎么做」,安全审查(Codex Security、@codex review)是独立环节,两者叠加不冲突——见[安全代理](codex-security-agent-2026.md)。

## 相关阅读

- [Codex Skills 用法：/skills 机制、技能怎么写（2026）](../03-codex-tutorials/codex-skills-guide-2026.md)
- [Codex 桌面版实测（2026）](codex-desktop-app-review-2026.md)
- [Codex 记忆与配置：AGENTS.md（2026）](../03-codex-tutorials/codex-memory-and-config-2026.md)
