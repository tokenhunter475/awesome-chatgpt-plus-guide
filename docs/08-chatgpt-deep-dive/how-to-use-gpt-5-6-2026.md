---
title: "怎么用上 GPT-5.6：各入口的开放范围、版本要求与灰度问题（2026）"
description: "GPT-5.6 已全量上线，但不同入口开放不同：ChatGPT 对话选 Sol Medium/High，Codex 里 Plus 可用三型号全档，免费用户在 Codex 用 Terra。本文讲清每个入口怎么开、版本要求、以及「看不到模型」的灰度排查。"
keywords:
  - 怎么用 GPT-5.6
  - GPT-5.6 入口
  - GPT-5.6 模型选择
  - Codex 用 GPT-5.6
  - GPT-5.6 看不到
  - GPT-5.6 灰度
updated: 2026-08-20
---

# 怎么用上 GPT-5.6：各入口的开放范围、版本要求与灰度问题（2026）

> 口径:2026 年 7 月 9 日正式上线后的开放范围;灰度推送以自己账号实际显示为准。

灰度推送期间，模型列表未更新通常与客户端版本或放量批次有关。以下整理各入口的开启位置、版本要求与排查方法。

1. **ChatGPT 对话**:模型选择器可选 Medium/High(Plus 及以上);免费/Go 档可在 Codex 中使用 Terra。
2. **Codex**:客户端有版本要求——CLI ≥ 0.144.0,桌面端 Codex 模式 ≥ 26.707.30751。
3. **看不到模型**的两个原因:客户端版本过旧(先升级)、灰度未覆盖(等待放量)。

## 入口一:ChatGPT 对话

打开输入框上方的**模型选择器**:

- Plus:可选 Sol **Medium / High**
- Pro:另有 **Extra High、Sol Pro**
- 模型选择器里的 Configure 可设置「复杂问题是否自动从 Instant 切到 Medium」——**自动切换不占手动推理额度**,建议开启
- Terra 和 Luna 不在标准对话选择器中,仅开放在 Codex 和 API

## 入口二:Codex(CLI / 桌面 / IDE)

最低版本要求：

| 客户端 | 最低版本 |
|---|---|
| Codex CLI | 0.144.0 |
| ChatGPT 桌面端(Codex 模式) | 26.707.30751 |

版本达标后,在 `/model` 中选择:Plus 及以上可选 Sol/Terra/Luna 并开启 max/ultra;免费和 Go 可用 Terra。安装步骤见 [CLI 教程](../03-codex-tutorials/codex-cli-tutorial-2026.md)。

## 入口三:API

直接调用模型名即可,Sol/Terra/Luna 均已上线,按 token 计费($5/$30、$2.5/$15、$1/$6 每百万 token)。API 无灰度限制,持有 API Key 即可调用(计费逻辑见[双钱包](../06-api-and-relays/api-credits-vs-subscription-2026.md))。

## 「看不到 GPT-5.6」排查三步

1. **升级客户端到最新**:大部分未显示情况由版本过旧导致。
2. **确认套餐权限**:标准对话选用 Sol 需 Plus 及以上套餐;免费用户需在 Codex 中查找 Terra。
3. **确认灰度覆盖**:若版本与权限均满足仍未出现,属于灰度未覆盖,需等待官方按周放量,目前无手动加速方法。

网上修改地区或更换 IP 的方式无法生效。灰度基于账号判定,与网络节点无关。

## FAQ

Q: 免费账号能用到 GPT-5.6 吗?

A: 能,路径是 Codex 里的 Terra(2026 年 8 月 6 日后免费/Go 均可);标准对话中免费版默认使用 Luna。

Q: 手机 App 能选 Sol 吗?

A: 模型选择逻辑与网页版一致,Plus 及以上可选 Medium/High。语音、生图等工具沿用各自档位。

Q: max 和 ultra 是什么?

A: 多智能体并行的更高算力执行模式,适合长任务,消耗额度也更高。日常使用 Medium/High 即可。

Q: 升级了客户端还是看不到,要等多久?

A: 灰度周期通常按周推进,官方未公布时间表。等待期间使用 Terra/Luna 或 GPT-5.5 均可正常处理任务。

## 相关阅读

- [GPT-5.6 模型档位解读：Sol、Terra、Luna（2026）](../01-models-and-tools/gpt-5-6-sol-terra-luna-explained-2026.md)
- [GPT-5.6 vs GPT-5.5：实测数据说话（2026）](gpt-5-6-vs-gpt-5-5-2026.md)
- [Codex CLI 使用教程：安装、登录、常用命令（2026）](../03-codex-tutorials/codex-cli-tutorial-2026.md)

---

<!-- payforchat-cta -->
> **想开 ChatGPT Plus / Pro，但没有海外信用卡？** PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=08-chatgpt-deep-dive) · [ChatGPT Plus 购买完整指南](https://www.payforchat.com/articles/chatgpt-plus-buy-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=08-chatgpt-deep-dive)
