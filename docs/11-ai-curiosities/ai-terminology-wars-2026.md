---
title: "AI 界的「 Copy 大战」：同一个功能，四家四种叫法（2026）"
description: "AI 功能命名大混战盘点：OpenAI 的 Skills 对 Anthropic 的 Skills、Routines 对 Automations、MCP 对插件协议——功能趋同、名字各异的现象背后，是行业标准争夺战。消费者视角的「其实都是一个东西」对照表。"
keywords:
  - AI 功能对比
  - Skills MCP
  - AI 插件协议
  - AI 功能命名
  - MCP 协议
  - AI 工具术语
updated: 2026-08-24
---

# AI 界的「 Copy 大战」：同一个功能，四家四种叫法（2026）

> 对照基于各产品公开文档的典型用法;细节差异客观存在,本文抓大放小。

用过三家以上 AI 工具的人都有这个困扰:**学一遍概念,要背三套单词**。OpenAI 叫 Skills 的东西,Anthropic 也叫 Skills;定时任务这边叫 Automations 那边叫 Routines;插件协议有的走 MCP 有的自家造——这篇做张「翻译对照表」,顺便看看名词大战背后在争什么。

先说结论:

1. 核心概念其实就五个:**技能、定时任务、工具协议、记忆文件、权限模式**——名字换来换去,概念没变。
2. 名字趋同处(都叫 Skills)说明行业在自发标准化;名字分裂处(MCP vs 私有协议)是标准争夺战。
3. 背概念别背名字:**理解「它解决什么问题」,换哪家都通**。

## 概念翻译对照表

| 概念 | OpenAI/Codex 阵营 | Anthropic/Claude 阵营 | 它解决什么 |
|---|---|---|---|
| 预置能力包 | Skills(/skills) | Skills | 把重复流程固化,AI 按需调用 |
| 定时/自动任务 | Automations(桌面版) | Routines | 无人值守:按时间或事件触发 |
| 工具接入协议 | MCP(支持) | MCP(支持) | 让 AI 统一插外部工具 |
| 项目记忆 | AGENTS.md | CLAUDE.md | 项目规范每次自动加载 |
| 执行确认 | approvals | 权限模式 | 控制哪些动作要人工点头 |

有意思的观察:**记忆文件是唯一「两边都叫得不一样但格式通用」的**——很多团队一个仓库里两个文件都放,两边的 AI 都能读。事实上的标准,先于名字的统一。

## 名字大战在争什么

**已经统一的:Skills 和 MCP。** MCP(Model Context Protocol)被 OpenAI、Anthropic、Apple(Xcode 26.3 接入,见[这篇](../09-codex-advanced/codex-xcode-agentic-2026.md))共同支持后,已经是工具接入的事实标准;Skills 的写法两边高度相似,互相借鉴的痕迹明显。**行业利益一致的地方,标准长得快。**

**还在分裂的:托管运行。** Routines 跑在 Anthropic 的云端(电脑关机也跑),Automations 依赖本地应用——名字不同是因为**架构真的不同**,不只是命名趣味。这种分裂是有信息量的:看到「Routines」要想到云端,看到「Automations」要确认执行环境。

**纯品牌差异的:档位命名。** Sol/Terra/Luna 对 Opus/Sonnet/Haiku——同一个「能力分层」需求,两套诗意体系(命名八卦详见[命名玄学](ai-naming-philosophy-2026.md))。

## 消费者的生存策略

1. **按概念学,不按品牌背**——「预置技能」「定时任务」「工具协议」五词在手,新工具上手就是「找它在哪」而不是「重新学一遍」
2. **迁移时问三个问题**:它的技能机制是什么、定时任务跑在哪、支持什么协议——三个答案基本刻画出一个工具的形态
3. **别参与标准战争**——MCP 还是私有协议的站队是厂商的事;你只需要知道「支持开放协议的,未来能接更多东西」

## FAQ

Q: 为什么它们总用同一个名字(Skills)却不完全兼容?

A: 功能相似但实现独立——类似早期「小程序」各家都有但互不相通。写法通用化(尤其记忆文件)是社区先趟出来的路。

Q: 学哪家的术语体系最保值?

A: 学概念本身。真要挑一家跟:支持 MCP 的生态未来接口面更宽,这是目前最稳的单一判断标准。

Q: 会有大一统的一天吗?

A: 协议层(MCP)最接近统一;产品功能层会一直分化——差异化是厂商的命,不是 bug。

## 相关阅读

- [Codex Skills 生态盘点（2026）](../09-codex-advanced/codex-skills-ecosystem-2026.md)
- [Claude Code Routines（2026）](../07-industry-watch/claude-code-routines-2026.md)
- [AI 圈的命名玄学（2026）](ai-naming-philosophy-2026.md)
