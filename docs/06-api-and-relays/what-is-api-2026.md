---
title: "API 是什么？给非程序员的 10 分钟入门（2026）"
description: "API 通俗入门：什么是 API、为什么 AI 工具总让你填 API Key、按量计费怎么算、和网页版用 AI 的区别。看懂这篇，AI 圈一半的收费套路你就明白了。"
keywords:
  - API 是什么
  - API 入门
  - API Key
  - 按量计费
  - AI API
  - API 和网页版区别
updated: 2026-08-20
---

# API 是什么？给非程序员的 10 分钟入门（2026）

> 「历劫卷」第一篇。不写代码也需要了解 API，多付费、被多扣钱、买错订阅这类问题，多数和它有关。

很多 AI 工具会提示「请填入你的 API Key」。填还是不填、填了会发生什么、钱从哪里扣，核心都在 API 的计费与调用逻辑。

要点如下：

1. API 是**程序调用程序的接口**：网页版是人直接用 AI，API 是让程序调用 AI。
2. API **按量计费**（用多少 token 付多少钱），网页版订阅**按月付费**，两套账目互不相通。
3. 遇到「填 API Key」，先确认三件事：这工具做什么用、调用花谁的钱、是否有账号直接登录等替代方式（比如 ChatGPT 账号登录就不用 API）。

## API 是什么：点菜的比喻

餐厅有两种使用方式：进店堂食（有菜单、有界面），或者后厨外包（按做菜量结算）。

- **网页版/App** = 进店点菜：界面就是菜单，按月付订阅费，交互与使用由服务方包办。
- **API** = 后厨外包：你或第三方工具直接调用模型能力，按实际 token 用量结账。

API（应用程序编程接口）相当于后厨对外接单的窗口。不需要了解模型内部如何运行，只要按约定格式发送请求即可，这个格式就是接口规范。

## API Key：你的后厨账卡

API Key 是一串字符（通常以 `sk-` 开头），用于**记账身份**：哪个 Key 发起的调用，费用就记在哪个账户上。

安全原则：

1. **Key = 钱包**。谁拿到你的 Key，谁就能消耗你的账户余额。不要截图、不要发群聊、不要贴进 AI 对话框（对话内容可能被保存）。
2. **Key 泄露的处理**：立刻去平台后台吊销（revoke）并重新生成。
3. **不同工具用不同的 Key**（如果平台支持创建多个），便于定位用量来源。

## 按量计费怎么算

API 按 token 计费（token 概念见[大模型原理](../00-ai-fundamentals/what-is-llm-2026.md)）。量级参考（2026 年 8 月官方价）：GPT-5.6 Luna 输入 $1/百万 token——一百万 token 大概是七十几万英文单词，或几十万汉字。日常轻度使用，几美元能跑很久；但接入自动化脚本或 Agent 时，每轮循环都会产生消耗，计算方法参考 [DeepSeek 涨价解读](../01-models-and-tools/deepseek-api-price-hike-2026.md)的示例。

与订阅模式的场景对照见下一篇：[API 额度 vs 订阅](api-credits-vs-subscription-2026.md)。

## 什么人在用 API

- **开发者**：把 AI 能力接入自己的产品或脚本。
- **第三方工具用户**：许多 AI 客户端本身不提供模型，需要用户填 Key「自带酒水」。
- **自动化用户**：处理批量文档、定时任务、机器人等网页版无法直接支持的操作。

如果只有日常对话需求，免费网页版或按月订阅已经足够，不需要特意使用 API。

## 常见疑问快答

**「工具让我填 Key，我该填吗？」** 先确认三点：工具的具体用途、调用费用是否由你的账户承担（是）、是否有其他登录方式。正规工具通常支持随时在平台端撤销授权。

**「API 能共用一个账号的订阅吗？」** 不能。API 额度与网页版订阅属于两套独立的计费体系，互不相通。

**「按量计费会不会失控？」** 有可能。主流平台均提供预算上限设置（monthly budget），充值后应优先配置预算上限。具体案例见[血的教训合集](ai-pitfalls-lessons-2026.md)。

## 相关阅读

- [API 额度 vs 订阅：两套钱包别充错（2026）](api-credits-vs-subscription-2026.md)
- [API 中转站是什么、怎么判断靠不靠谱（2026）](what-is-api-relay-2026.md)
- [大模型是什么？AI 为什么会说话、写代码（2026）](../00-ai-fundamentals/what-is-llm-2026.md)

---

<!-- payforchat-cta -->
> **订阅和 API 是两套钱包。** 要用 ChatGPT 和 Codex 的套餐额度，开的是 Plus / Pro 订阅。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=06-api-and-relays) · [API 额度 vs 订阅：别充错](https://www.payforchat.com/articles/chatgpt-api-credit-recharge-vs-subscription-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=06-api-and-relays)
