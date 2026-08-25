---
title: "OpenAI 把 Codex 插进 Claude Code：跨阵营协作开始了（2026）"
description: "OpenAI 官方发布 codex-plugin-cc：在 Claude Code 里直接调用 Codex 做代码审查、对抗性审查甚至整段任务移交。AI 编码工具从各自闭环走向互操作，竞争焦点变成谁更容易被调用。"
keywords:
  - Codex Claude Code 插件
  - codex-plugin-cc
  - 跨 AI 协作
  - 对抗性审查
  - AI 编程互操作
  - 多代理编程
updated: 2026-08-20
---

# OpenAI 把 Codex 插进 Claude Code：跨阵营协作开始了（2026）

> 口径:OpenAI 官方发布 codex-plugin-cc,2026 年。

2026 年 AI 编程圈最反直觉的一幕:OpenAI 官方做了个插件,让你**在竞争对手 Claude Code 的地盘里调用 Codex**。不是社区 hack,是官方行为。

先说结论：

1. **codex-plugin-cc**:Claude Code 里直接调 Codex——代码审查、对抗性审查、整段任务移交。
2. 最有意思的不是功能,是**姿态**:OpenAI 主动把自己的能力嵌进 Anthropic 的工作流。
3. 行业逻辑变了:竞争从「谁做闭环」变成「**谁更容易被调用**」。

## 插件能干什么

三个用法,按侵入程度排:

- **代码审查**:Claude Code 写的代码,让 Codex 审——两家模型互查,盲区互补
- **对抗性审查**:让一个 AI 专门挑另一个 AI 的茬——同样的代码,不同模型的训练偏差不同,交叉验证能暴露单模型发现不了的问题
- **任务移交**:整段任务直接丢给 Codex 处理——在同一个工作流里按任务类型分工

## 为什么「官方互插」是个大信号

过去行业的默认剧本:各家做封闭生态,抢入口、抢粘性、竖墙。这个插件给出了另一个剧本:**用户不会只用一个模型**——你写代码用 Claude Code 顺手,审查信 Codex 的严谨,为什么要强迫选边?

竞争的胜负手因此改变:**谁更愿意开放接口、嵌入别人的工作流,谁就更容易成为「被调用的那一层」**。微软接 Claude、Apple 同时接两家、OpenAI 插进 Claude Code——2026 年的大厂动作高度一致:开放比封闭值钱。

## 你可以立刻用的思路

装不装这个插件其次,**「双模型交叉审查」的思路现在就能用**:

- 一边生成、另一边审——写完让另一个模型复述需求、挑毛病,是性价比最高的质量手段(见[Claude vs ChatGPT](../08-chatgpt-deep-dive/claude-vs-chatgpt-2026.md)的按任务分法)
- 关键代码过双闸:Codex `/review` + 另一家模型的安全视角(见[代码审查实战](../03-codex-tutorials/codex-code-review-2026.md))
- 别为「阵营」吵架——**大厂自己都不站队,用户站什么队**

## FAQ

Q: 在 Claude Code 里用 Codex,额度算谁的?

A: Codex 侧消耗走 ChatGPT 账号体系,Claude Code 侧走 Anthropic 订阅——各算各的,两边账号都要有。

Q: 对抗性审查是什么意思?

A: 让模型 A 生成的代码交给模型 B 专门找茬。不同模型的弱点分布不同,交叉验证的覆盖面大于单一模型自审。

Q: 以后会不会所有工具都互通?

A: 方向如此——MCP 等开放协议 + 官方插件,墙在变矮。评估工具时把「能不能和别人协作」当成一个正式维度。

## 相关阅读

- [AI 编程工具对比：Codex vs Claude Code vs Cursor（2026）](../01-models-and-tools/ai-coding-tools-comparison-2026.md)
- [Xcode 26.3 与 MCP 的胜利（2026）](codex-xcode-agentic-2026.md)
- [Codex 代码审查实战（2026）](../03-codex-tutorials/codex-code-review-2026.md)
