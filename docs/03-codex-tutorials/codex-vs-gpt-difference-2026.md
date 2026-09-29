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
updated: 2026-09-29
---

# Codex 和 GPT 的区别是什么？Codex、ChatGPT、GPT 模型关系一次讲清（2026）

> 档位与模型口径以 2026 年 9 月 OpenAI 官方说明为准。

Codex、ChatGPT 与 GPT 分属三个不同层级：工具、账号体系与底层模型。

1. **GPT 是模型**，ChatGPT 与 Codex 调用的底层模型都是它；**Codex 是编程工具**，调用该系列模型完成代码开发任务。
2. **Codex 工具本身免费**，下载、安装与登录均不收费；免费 ChatGPT 账号可以使用，但调用的是轻量档模型，且额度有限。
3. **不存在「Codex 会员」**。可用模型档位与调用额度完全由绑定的 ChatGPT 套餐决定（免费 / Go / Plus / Pro）。

## 三层关系：模型 → 账号 → 工具

**GPT 是模型系列。** GPT-5.6 与 GPT-5.4 均为此系列的代号。OpenAI 提供的对话与编程能力，底层均运行在 GPT 系列模型之上。

**ChatGPT 是账号与订阅体系。** 注册的 ChatGPT 账号决定了可用模型档位与调用量：免费版提供基础模型，Go（官方 $8/月）和 Plus（官方 $20/月）逐级开放更高档位，Pro（官方 $100/$200 月）开放全部档位并提供最高额度。

**Codex 是面向编程的客户端工具。** 它提供五种形态：终端 CLI、VS Code / JetBrains 等 IDE 插件、桌面 App、网页版（chatgpt.com/codex）、GitHub 集成，均可免费获取。登录使用 ChatGPT 账号，对应套餐直接决定 Codex 中可调用的模型档位与额度上限。

## 各档位在 Codex 里的差异（2026 年 9 月口径）

| ChatGPT 档位 | 能用 Codex 吗 | 可用模型 | 额度特点 |
|---|---|---|---|
| 免费版 | 能 | 轻量档 | 额度有限，用完等重置，不能加购 |
| Go（官方 $8/月） | 能 | 轻量档 | 比免费版高，仍有限，不能加购 |
| Plus（官方 $20/月） | 能 | 旗舰档 + 全部轻量档 | 日常开发够用，可加购额度 |
| Pro（官方 $100/$200 月） | 能 | 全部档位 | 分别约为 Plus 的 5 倍 / 20 倍额度 |

> Pro 20X（$200 档）自 2026-09-10 起 OpenAI 暂停新购，只能续费或到期回归；Pro 5X 正常。

- **免费账号可以使用 Codex。** 早期 Codex 仅对付费用户开放，目前已放开限制，免费账号可以正常安装使用，仅在模型和额度上受限。
- **模型支持随官方调整更新。** 2026 年 8 月 31 日，GPT-5.4 系列从 Codex 下线，由新一代档位接替。Codex 能调用的能力上限，取决于账号所处的订阅档位。

## 和其他编程工具的区别

- **GitHub Copilot**：主要用于编辑器内的代码补全；Codex 偏向项目级上下文理解与多步骤任务执行，涵盖代码修改、测试运行与报错修复。
- **Claude Code**：Anthropic 推出的终端编程工具，模型能力突出，但账号风控较严，国内使用门槛较高；Codex 直接使用 ChatGPT 账号登录，使用门槛相对较低。
- 执行风格上，Codex 倾向完整分析与代码审查，响应相对偏慢；Claude Code 生成速度较快，但使用稳定性受账号限制影响较大。

## 额度计算：两项限制机制

Codex 的用量并非单一池子，而是受两项规则同时约束：

| 限额类型 | 机制 | 撞上后的表现 |
|---|---|---|
| 5 小时滚动窗口 | 短时高强度使用触发，随时间滚动恢复 | 报错，通常几小时内自动恢复 |
| 每周上限 | 一周总量封顶 | 5 小时窗口恢复了也照样用不了 |

自 2026 年 4 月起，用量按 token 计算而非消息条数，不同任务规模的消耗差异显著。在 CLI 中运行 `/status` 可查看两项限额的剩余量与重置时间。超额后的处理路径，见 [Codex 用量上限说明](codex-usage-limits-2026.md)。

## 什么情况你不需要更高档位

按实际需求匹配套餐即可：

- 体验 Codex 或编写小型学习项目：免费档足够，额度耗尽后等待重置即可。
- 以常规对话为主、偶尔分析代码：Go 档额度通常能够覆盖。
- 依赖 Codex 进行日常高强度开发、长任务多或频繁达到周上限：建议选择 Plus 起步，更高用量再考虑 Pro。

## FAQ

Q: Codex 和 GPT 是一个东西吗？

A: 不是。GPT 是底层模型系列，Codex 是基于该系列模型构建的编程工具。Codex 执行任务时调用的是 GPT 系列模型。

Q: Codex 免费吗？

A: 工具本身免费，下载、安装及登录均无费用，免费 ChatGPT 账号可以使用。费用产生在模型订阅端：使用旗舰模型与更高额度需要订阅 ChatGPT Plus 及以上套餐。

Q: 需要「Codex 会员」或「Codex 充值」吗？

A: 官方不存在独立的 Codex 会员，相关付费产品本质上都是 ChatGPT 套餐。「Codex 独立账号」「Codex 激活码」多为共享号，缺少售后保障。需要订阅的是 ChatGPT Plus/Pro；国内支付受阻时，代充服务（如 [PayForChat](https://payforchat.com/plans?ref=github)）可以在自有账号上完成订阅，支持微信/支付宝付款，无需提供密码。

Q: Codex 支持哪些形式使用？

A: 支持五种形式：终端 CLI、VS Code / JetBrains 等 IDE 插件、桌面 App、网页版（chatgpt.com/codex）、GitHub 集成。其中 CLI 与 IDE 插件共享登录态和会话。安装步骤见 [Codex CLI 使用教程](codex-cli-tutorial-2026.md)。

Q: GPT-5.4 还能用吗？

A: 2026 年 8 月 31 日起，GPT-5.4 系列已从 Codex 下线，由新一代档位接替。可用模型以 Codex 内运行 `/model` 实际显示的列表为准。

## 参考来源

- [OpenAI Codex 官方定价与额度说明](https://developers.openai.com/codex/pricing)
- [ChatGPT 官方套餐页](https://openai.com/chatgpt/pricing/)
- [OpenAI：Introducing ChatGPT Go](https://openai.com/index/introducing-chatgpt-go/)

## 相关阅读

- [Codex CLI 使用教程：安装、登录、常用命令（2026）](codex-cli-tutorial-2026.md)
- [Codex 用量上限说明：5 小时窗口与周上限（2026）](codex-usage-limits-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials)
