---
title: "ChatGPT Work 是什么：办公智能体、与 Codex 共享额度意味着什么（2026）"
description: "ChatGPT Work 是 OpenAI 面向办公场景的智能体功能，处理文档、表格、流程任务，2026 年 7 月随三合一桌面 App 获得入口，且与 Codex 共享同一个用量池。本文讲清它是什么、和普通对话的区别、额度联动注意。"
keywords:
  - ChatGPT Work
  - ChatGPT 办公智能体
  - ChatGPT 桌面 App
  - AI 办公
  - ChatGPT Work 额度
  - 智能体办公
updated: 2026-08-20
---

# ChatGPT Work 是什么：办公智能体、与 Codex 共享额度意味着什么（2026）

> 口径:2026 年 8 月;功能开放范围以产品内实际显示为准。

2026 年 7 月 9 日，OpenAI 发布了三合一的新版 ChatGPT 桌面 App（Chat / Work / Codex 三个模式合体，独立的旧版更名 ChatGPT Classic），其中包含面向办公场景的智能体模式 **ChatGPT Work**。

1. ChatGPT Work 是**处理文档、表格、流程任务的办公智能体**，不是「办公版聊天框」。
2. 它与 **Codex 共享同一个用量池**，两边同时重度使用会互相挤占额度。
3. 适合批量整理、格式转换、多文档汇总等「重复性办公流程」，不适合当普通对话用。

## 它和普通对话差在哪

普通对话一问一答即结束。ChatGPT Work 则是接收任务目标后，**连续操作多个文档/表格，中途自行检查并交付结果**，机制沿用了 Codex 的智能体执行逻辑（智能体原理见 [AI Agent 是什么](../00-ai-fundamentals/what-is-ai-agent-2026.md)）。

典型任务形态：

- 把这 30 份简历按岗位要求筛成一张汇总表
- 按这个模板，把销售数据整理成周报初稿
- 核对两版合同的差异点，列出改动清单

这类任务都需要「输入材料 + 规则，输出结构化结果」，属于办公中机械耗时的环节。

## 额度联动

2026 年 7 月起，**ChatGPT Work 和 Codex 共享同一个用量池**：

- 白天用 Work 处理文档，晚上 Codex 写代码的可用额度就会减少。
- 重度使用 Codex 前需注意当前用量。
- 限额触发机制与 Codex 一致：5 小时窗口 + 周上限（见[用量说明](../03-codex-tutorials/codex-usage-limits-2026.md)）。

两边任务均从同一额度池扣除，规划用量时需合并计算。

## 适用人群

- **重度处理文档与表格的人**：处理汇总、核对、格式化等重复劳动。
- **小团队**：预算有限无法采购企业系统时，Work 订阅能提供轻量自动化。
- **非开发人员**：不用命令行即可直接使用智能体工作流（进阶参考[智能体平台](../05-ai-toolbox/agent-platforms-guide-2026.md)）。

不适合场景：一次性简短提问（普通对话更直接）、财务关键计算（人工复核公式不可省）、涉密文档处理（参考[数据安全](../00-ai-fundamentals/ai-data-security-2026.md)原则）。

## FAQ

Q: Work 要单独付费吗？

A: 它是 ChatGPT 产品体系内的功能，按账号档位提供权限和额度，不是独立订阅。具体开放范围以产品内显示为准。

Q: 和微软 Copilot 接入 Claude 的 Cowork 是什么关系？

A: 两者是同类产品。OpenAI 的 Work 运行在自家生态中，微软 Copilot Cowork 走本地运行路线（见[微软合作篇](../../archive/07-industry-watch/microsoft-copilot-anthropic-2026.md)）。

Q: 旧版独立 Codex App 还能用吗？

A: 2026 年 7 月 9 日起 Codex 能力已并入新版三合一 App，旧独立版停用，桌面端安装新版 ChatGPT App 即可。

Q: Work 任务失败会消耗额度吗？

A: 会扣除执行中已产生的消耗。减少损耗的方式与 Codex 一致：提供完整材料、明确规则和验收标准（见[提示词实战](../03-codex-tutorials/codex-prompt-guide-2026.md)）。

## 相关阅读

- [AI Agent 是什么？和普通 AI 对话的区别（2026）](../00-ai-fundamentals/what-is-ai-agent-2026.md)
- [Codex 网页版与云端任务（2026）](../03-codex-tutorials/codex-cloud-tasks-2026.md)
- [智能体平台入门：不写代码搭 AI 应用（2026）](../05-ai-toolbox/agent-platforms-guide-2026.md)

---

<!-- payforchat-cta -->
> **想开 ChatGPT Plus / Pro，但没有海外信用卡？** PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=08-chatgpt-deep-dive) · [ChatGPT Plus 购买完整指南](https://www.payforchat.com/articles/chatgpt-plus-buy-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=08-chatgpt-deep-dive)
