---
title: "GPT-5.6 模型档位解读：Sol、Terra、Luna 各是什么、免费用哪个（2026）"
description: "GPT-5.6 于 2026 年 7 月 9 日正式上线，分 Sol（旗舰）、Terra（均衡）、Luna（轻量）三个型号。本文讲清三者区别、各套餐开放范围、API 价格和编程基准成绩，帮你判断自己该用哪档。"
keywords:
  - GPT-5.6
  - GPT-5.6 Sol
  - GPT-5.6 Terra
  - GPT-5.6 Luna
  - GPT 模型档位
  - GPT-5.6 免费
updated: 2026-08-20
---

# GPT-5.6 模型档位解读：Sol、Terra、Luna 各是什么、免费用哪个（2026）

> 口径日期：2026 年 7 月 9 日 GPT-5.6 正式上线，本文按 8 月开放范围整理；灰度推送以自己账号实际显示为准。

GPT-5.6 包含旗舰 Sol、均衡 Terra、轻量 Luna 三个型号，以及 Sol 的多智能体高性能模式 Sol Ultra。各型号对应不同的定位与取舍：

1. **日常问答**不需要 GPT-5.6——GPT-5.5 Instant 更快，仍负责快速回答。
2. **长任务编程、复杂研究**使用 Sol，Plus 用户可用 Medium/High 档。
3. **免费和 Go 用户**在 Codex 里可用 Terra（能力已超过上一代旗舰 GPT-5.5）。

## 三个型号怎么分工

| 型号 | 定位 | 适合任务 | API 价格（每百万 token） |
|---|---|---|---|
| GPT-5.6 Sol | 旗舰能力 | 长任务编程、复杂研究、计算机操作 | 输入 $5 / 输出 $30 |
| GPT-5.6 Terra | 能力/速度/成本平衡 | 日常工作、Codex 常规任务、批量处理 | 输入 $2.5 / 输出 $15 |
| GPT-5.6 Luna | 最快、最便宜 | 轻量任务、高频调用、低延迟 | 输入 $1 / 输出 $6 |

**Sol Ultra 不是第四个型号**，而是 Sol 的多智能体模式，通过投入更多算力并行处理复杂任务，对应 Pro 用户的最高档。

官方 Terminal-Bench 2.1 编程基准测试中，Sol 为 88.8%、Sol Ultra 为 91.9%、Terra 为 87.4%、Luna 为 84.7%，上一代旗舰 GPT-5.5 为 85.6%。Terra 表现已超过上代旗舰，Sol 的优势主要集中在复杂终端工作流与持续执行能力。

## 各套餐在哪能用什么

按产品入口区分（2026 年 8 月口径）：

| 套餐 | 标准 ChatGPT 对话 | Codex |
|---|---|---|
| Free / Go | 不能选 Sol | 可用 Terra |
| Plus | Sol Medium、High | Sol/Terra/Luna 可选，支持 max/ultra |
| Pro | 另有 Extra High、Sol Pro | 三型号全开，支持 max/ultra |

细节说明：

- **Terra 和 Luna 不在标准对话的模型选择器里**，仅开放在 Codex 和 API。需要轻量档跑批量任务，走 Codex 或 API。
- 标准对话中，GPT-5.5 Instant 仍负责快速回答；遇到复杂问题可自动切到 Medium（自动切换不消耗手动推理额度）。手动选 Medium/High 才会消耗 Sol 的推理额度。

## 在 Codex 里用 GPT-5.6 的版本要求

Codex 客户端最低版本要求：CLI 需达到 `0.144.0`，ChatGPT 桌面端 Codex 模式需达到 `26.707.30751`。账号符合条件却看不到 GPT-5.6 时，先更新客户端；若更新后仍未出现，需等待后续灰度放量。CLI 的安装与 `/model` 切换见 [Codex CLI 使用教程](../03-codex-tutorials/codex-cli-tutorial-2026.md)。

## 该为 GPT-5.6 升级套餐吗

根据使用需求评估：

- 免费用户：Codex 中可直接调用 Terra（能力超上代旗舰）；若没有长任务需求，无需专门为 Sol 付费。
- Plus 用户：Medium/High 已覆盖绝大多数场景；Extra High 和 Sol Pro 为 Pro 专属，主要应对极端复杂任务。
- API 用户：高频轻量任务选 Luna，常规任务选 Terra，复杂任务选 Sol，不同型号间成本相差 3-5 倍。

## FAQ

Q: GPT-5.6 免费用户能用吗？

A: 能。免费和 Go 用户在 Codex 中可用 Terra；标准对话里免费用户继续用基础模型，不能手动选 Sol。

Q: 为什么模型选择器里没有 Terra 和 Luna？

A: 这两个型号开放在 ChatGPT Work、Codex 和 API，未放入标准对话的选择器。

Q: Sol Medium 和 High 差在哪？

A: 推理投入不同：High 思考更深、更慢、消耗更多额度，适合难题；Medium 是日常主力档。

Q: GPT-5.6 有限额吗？

A: 沿用 ChatGPT 现有限额体系，未公布统一固定次数；手动推理消耗 Sol 额度，达上限可能暂时回退到 GPT-5.4 Thinking mini，界面会显示重置时间。

## 相关阅读

- [ChatGPT 是什么？产品、模型、套餐三层一次分清（2026）](what-is-chatgpt-2026.md)
- [Codex 和 GPT 的区别是什么？（2026）](../03-codex-tutorials/codex-vs-gpt-difference-2026.md)
- [三大模型家族对比：GPT vs DeepSeek vs Claude（2026）](gpt-vs-deepseek-vs-claude-2026.md)

---

<!-- payforchat-cta -->
> **想用 ChatGPT Plus / Pro，但没有海外信用卡？** PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=01-models-and-tools) · [国内充值全指南](https://www.payforchat.com/articles/2026-gpt-chatgpt-recharge-guide-plus-pro?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=01-models-and-tools)
