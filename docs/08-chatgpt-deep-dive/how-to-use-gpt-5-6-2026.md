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

「GPT-5.6 都发布一个月了,我的模型列表里怎么没有?」——这是灰度期最常见的问题。这篇把每个入口的开关位置、版本门槛和「看不到」的排查一次列清。

先说结论：

1. **ChatGPT 对话**:模型选择器选 Medium/High(Plus 及以上);免费/Go 档在 Codex 里用 Terra。
2. **Codex**:对版本有硬要求——CLI ≥ 0.144.0,桌面端 Codex 模式 ≥ 26.707.30751。
3. **看不到模型**的两个原因:客户端版本旧(先升级)、灰度没轮到(只能等)。

## 入口一:ChatGPT 对话

打开输入框上方的**模型选择器**:

- Plus:可选 Sol **Medium / High**
- Pro:另有 **Extra High、Sol Pro**
- 模型选择器里的 Configure 可控制「复杂问题是否自动从 Instant 切到 Medium」——**自动切换不占手动推理额度**,开着不亏
- Terra 和 Luna 不在标准对话的选择器里,它们开放在 Codex 和 API(设计如此,不是 bug)

## 入口二:Codex(CLI / 桌面 / IDE)

**先对版本,再谈模型**:

| 客户端 | 最低版本 |
|---|---|
| Codex CLI | 0.144.0 |
| ChatGPT 桌面端(Codex 模式) | 26.707.30751 |

版本达标后,`/model` 里选:Plus 及以上可选 Sol/Terra/Luna 并开 max/ultra;免费和 Go 可用 Terra。客户端怎么装见 [CLI 教程](../03-codex-tutorials/codex-cli-tutorial-2026.md)。

## 入口三:API

直接调模型名即可,Sol/Terra/Luna 全开,按 token 计费($5/$30、$2.5/$15、$1/$6 每百万 token)。API 没有灰度问题,_key 在手说用就用(计费逻辑见[双钱包](../06-api-and-relays/api-credits-vs-subscription-2026.md))。

## 「看不到 GPT-5.6」排查三步

1. **升级客户端到最新**——80% 的「看不到」是版本问题
2. **确认套餐权限**:对话里选 Sol 需要 Plus 及以上;免费用户去 Codex 里找 Terra
3. 都对了还没有 → **灰度未覆盖**,等官方放量(通常按周推进),没有任何加速手段——别信「强制解锁」的偏方

多提一句:网上流传的「改地区强制开 GPT-5.6」教程,基本都是玄学。灰度按账号推进,和你的 IP 没关系;折腾半天不如等两周。

## FAQ

Q: 免费账号能用到 GPT-5.6 吗?

A: 能,路径是 Codex 里的 Terra(2026 年 8 月 6 日后免费/Go 均可);标准对话里免费版默认 Luna。

Q: 手机 App 能选 Sol 吗?

A: 模型选择逻辑与网页版一致,Plus 及以上可选 Medium/High。语音、生图等工具另有各自的档位逻辑。

Q: max 和 ultra 是什么?

A: 更高算力投入的执行模式(多智能体并行),适合最重的长任务,消耗额度也相应更高。日常 Medium/High 够用。

Q: 升级了客户端还是看不到,要等多久?

A: 灰度周期通常按周计,无官方时间表。期间 Terra/Luna 或 GPT-5.5 都能正常干活,不至于阻塞工作。

## 相关阅读

- [GPT-5.6 模型档位解读：Sol、Terra、Luna（2026）](../01-models-and-tools/gpt-5-6-sol-terra-luna-explained-2026.md)
- [GPT-5.6 vs GPT-5.5：实测数据说话（2026）](gpt-5-6-vs-gpt-5-5-2026.md)
- [Codex CLI 使用教程：安装、登录、常用命令（2026）](../03-codex-tutorials/codex-cli-tutorial-2026.md)
