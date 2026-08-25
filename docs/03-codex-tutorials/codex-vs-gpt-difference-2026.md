---
title: "Codex 和 GPT 的区别是什么？Codex、ChatGPT、GPT 模型关系一次讲清（2026）"
description: "Codex 是 OpenAI 的 AI 编程工具，GPT 是模型，ChatGPT 是账号和订阅体系——三者关系一句话讲清：Codex 免费用，模型和额度跟着 ChatGPT 套餐走。附各档位差异对比表和额度机制说明。"
keywords:
  - Codex 和 GPT 区别
  - Codex 是什么
  - Codex 和 ChatGPT 关系
  - Codex 免费吗
  - Codex 额度
  - GPT 模型
updated: 2026-08-20
---

# Codex 和 GPT 的区别是什么？Codex、ChatGPT、GPT 模型关系一次讲清（2026）

> 档位与模型口径以 2026 年 8 月 OpenAI 官方说明为准，本文持续更新。

搜「Codex 和 GPT 的区别」的人，多数是被三个名字绕晕了：Codex、ChatGPT、GPT。它们不是并列的三个产品，而是三层东西——工具、账号体系、模型。搞清这三层，所有关于 Codex 的疑问都能对上号。

总而言之，就下面几条：

1. **GPT 是模型**，ChatGPT 里回答你问题的就是它；**Codex 是写代码的工具**，用同一批模型干编程的活。
2. **Codex 工具本身免费**——下载、安装、登录都不花钱；免费 ChatGPT 账号也能用，只是模型为轻量档、额度有限。
3. **不存在「Codex 会员」**。你能用多强的模型、多少额度，完全由你的 ChatGPT 套餐决定（免费 / Go / Plus / Pro）。

## 三层关系：模型 → 账号 → 工具

**GPT 是模型系列的名字。** GPT-5.6 是模型，GPT-5.4 也是模型——就像发动机型号。OpenAI 的对话和编程能力，底层都跑在 GPT 系列模型上。

**ChatGPT 是账号和订阅体系。** 你注册的 ChatGPT 账号决定你能用到哪些档位的模型、多少用量：免费版用基础模型，Go（官方 $8/月）和 Plus（官方 $20/月）逐级解锁更多，Pro（官方 $100/$200 月）给到全部档位和最高额度。

**Codex 是跑在这套体系上的编程工具。** 它有五种形态：终端 CLI、VS Code / JetBrains 等 IDE 插件、桌面 App、网页版（chatgpt.com/codex）、GitHub 集成——全部免费获取。登录用你的 ChatGPT 账号，你是什么套餐，Codex 就用什么档位的模型、给多少额度。

说白了：**ChatGPT 是账号和模型体系，Codex 是跑在这套体系上的编程工具，GPT 是两者共用的发动机。**

## 各档位在 Codex 里的差异（2026 年 8 月口径）

| ChatGPT 档位 | 能用 Codex 吗 | 可用模型 | 额度特点 |
|---|---|---|---|
| 免费版 | 能 | 轻量档 | 额度有限，用完等重置，不能加购 |
| Go（官方 $8/月） | 能 | 轻量档 | 比免费版高，仍有限，不能加购 |
| Plus（官方 $20/月） | 能 | 旗舰档 + 全部轻量档 | 日常开发够用，可加购额度 |
| Pro（官方 $100/$200 月） | 能 | 全部档位 | 分别约为 Plus 的 5 倍 / 20 倍额度 |

两个容易踩的认知坑：

- **「免费账号用不了 Codex」是旧口径。** 早期 Codex 只对付费用户开放，现在已经放开——免费账号能装能用，只是模型和额度受限。
- **模型和 Codex 绑得越来越紧。** OpenAI 持续把最新旗舰模型优先给 Codex：2026 年 8 月 31 日，旧的 GPT-5.4 系列从 Codex 下线，由新一代档位接替。Codex 的体验天花板，始终由你账号能用的模型决定。

## 和其他编程工具的区别（30 秒版）

- **GitHub Copilot**：主打编辑器里的行级补全，像打字很快的助手；Codex 是能理解整个项目、独立执行多步任务的工程师——改代码、跑测试、修报错一条龙。
- **Claude Code**：Anthropic 的同类终端工具，能力强但账号风控严，国内使用门槛高；Codex 用 ChatGPT 账号直接登录，门槛低。
- 执行风格上，Codex 分析严谨、代码审查是公认强项，代价是响应偏慢； Claude Code 快但稳不稳看账号。

## 额度怎么算：两把锁机制

Codex 的用量不是单一池子，每个套餐同时挂着**两把锁**：

| 限额类型 | 机制 | 撞上后的表现 |
|---|---|---|
| 5 小时滚动窗口 | 短时高强度使用触发，随时间滚动恢复 | 报错，通常几小时内自动恢复 |
| 每周上限 | 一周总量封顶 | 5 小时窗口恢复了也照样用不了 |

用量按 token 计算（2026 年 4 月起），不是消息条数——改一个小脚本和重构一个大仓库，消耗可能差几十倍。CLI 里用 `/status` 可以看两个限额各自的剩余量和重置时间。撞限额后的完整处理路径，见 [Codex 用量上限说明](codex-usage-limits-2026.md)。

## 什么情况你不需要更高档位

冷静点，不是人人都要上 Plus/Pro：

- 只是想体验 Codex、写写学习项目——免费档够用，撞额度了等重置就行。
- 轻度对话为主、偶尔让 AI 看段代码——Go 档的额度已经覆盖。
- 重度使用（每天靠 Codex 干活、长任务多、频繁撞周上限）——才需要 Plus 起步，Pro 看量。

## FAQ

Q: Codex 和 GPT 是一个东西吗？

A: 不是。GPT 是模型系列（发动机），Codex 是基于这些模型的编程工具（车）。Codex 干活时调用的就是 GPT 系列模型。

Q: Codex 免费吗？

A: 工具本身免费，下载安装登录都不花钱，免费 ChatGPT 账号也能用。付费的是背后的模型订阅——想用旗舰模型和更多额度，需要 ChatGPT Plus 及以上套餐。

Q: 需要「Codex 会员」或「Codex 充值」吗？

A: 不存在独立的 Codex 会员。网上标着「Codex 会员」的付费产品，实质都是 ChatGPT 套餐。警惕「Codex 独立账号」「Codex 激活码」类商品，多为共享号，无售后。要充的是 ChatGPT Plus/Pro；国内支付受阻时，代充服务（如 [PayForChat](https://payforchat.com/plans?ref=github)）可以在你自己的账号上完成订阅，微信/支付宝付款，不需要提供密码。

Q: Codex 支持哪些形式使用？

A: 五种：终端 CLI、VS Code / JetBrains 等 IDE 插件、桌面 App、网页版（chatgpt.com/codex）、GitHub 集成。CLI 和 IDE 插件共享登录态和会话。安装步骤见 [Codex CLI 使用教程](codex-cli-tutorial-2026.md)。

Q: GPT-5.4 还能用吗？

A: 2026 年 8 月 31 日起，GPT-5.4 系列从 Codex 下线，由新一代档位接替。模型列表以 Codex 内 `/model` 命令实际显示为准。

## 参考来源

- [OpenAI Codex 官方定价与额度说明](https://developers.openai.com/codex/pricing)
- [ChatGPT 官方套餐页](https://openai.com/chatgpt/pricing/)
- [OpenAI：Introducing ChatGPT Go](https://openai.com/index/introducing-chatgpt-go/)

## 相关阅读

- [Codex CLI 使用教程：安装、登录、常用命令（2026）](codex-cli-tutorial-2026.md)
- [Codex 用量上限说明：5 小时窗口与周上限（2026）](codex-usage-limits-2026.md)
