---
title: "Codex VS Code 集成教程：IDE 插件安装配置全指南（2026）"
description: "Codex IDE 插件安装与使用：VS Code / Cursor / Windsurf / JetBrains 全家桶 / Opencode 的安装步骤、登录方式、使用技巧，以及「Cursor 装完找不到图标」「地区限制报错」等高频坑的解决方法。"
keywords:
  - Codex VS Code
  - Codex 插件
  - Codex Cursor
  - Codex JetBrains
  - Opencode Codex
  - Codex IDE 配置
updated: 2026-08-20
---

# Codex IDE 集成：VS Code、Cursor、JetBrains、Opencode 配置指南（2026）

> 插件市场名称和界面随版本变化，以各市场实际搜索结果为准；本文 2026 年 8 月更新。

IDE 插件支持侧边栏对话、选中代码直接提问，并与 CLI 共享会话。以下覆盖四个主流环境的安装与配置注意事项。

要点：

1. **VS Code / Cursor / Windsurf**：在扩展市场安装官方插件并登录，默认进入 Agent 模式。
2. **JetBrains 全家桶**（IntelliJ / PyCharm / WebStorm 等）：在官方插件市场安装，支持三种登录方式。
3. 插件与 CLI **只需登录一次**，两端共享登录态与会话。

## VS Code / Cursor / Windsurf

**安装**：打开扩展市场 → 搜「Codex – OpenAI's coding agent」（认准 OpenAI 官方）→ 安装 → 侧边栏出现 Codex 图标 → 点击登录（浏览器跳转授权，和 CLI 同一套流程）。

**使用**：

- 侧边栏对话：和 CLI 交互一致，默认 Agent 模式（可读文件、跑命令、改代码）
- **选中代码快速提问**：选中一段代码 → 右键 → Ask Codex → 针对选中内容回答
- 会话互通：终端里 `codex` 开的任务，IDE 里能看到进度；反之亦然

**Cursor 图标显示**：Cursor 的活动栏默认横向排列，装完插件若看不到 Codex 图标，可在折叠项中查找，或手动 pin 到活动栏。

**Cursor 计费差异**：在 Cursor 对话框里直接切换「Codex 模型」走 **OpenAI API 计费**（需在设置中填 API Key），不消耗 ChatGPT 订阅额度；安装 Codex 插件才走订阅。

## JetBrains 全家桶

IntelliJ IDEA、PyCharm、WebStorm、Rider 等通用：在 **JetBrains 插件市场**搜 Codex 安装。鉴权方式有三种可选：ChatGPT 账号登录（推荐个人用户）、API Key、JetBrains AI 订阅。

## Opencode 集成

Opencode 是开源客户端，支持通过 ChatGPT 账号登录以使用 Codex 的订阅和额度。

流程（以桌面版为例）：官网 opencode.ai 下载客户端 → 添加项目 → 对话框输入 `/model` 选模型 → 点「连接供应商」→ 选 OpenAI → 跳转 ChatGPT 登录授权 → 完成后即可管理模型。不同系统版本的界面略有差异（macOS 部分版本没有「添加模型」按钮，走连接供应商路径），以实际界面为准。

## 高频问题排查

| 现象 | 原因 | 解决 |
|---|---|---|
| Cursor 装完找不到 Codex 图标 | 活动栏折叠 | 展开折叠项 / pin 到活动栏 |
| 报 `This model provider doesn't serve your region` | 模型服务对该 IP 地区不开放 | 开全局/系统代理；仍报错在编辑器设置里配 proxy |
| 登录后一直 thinking | 网络问题 | 给终端/编辑器设置代理（方法见 [CLI 教程](codex-cli-tutorial-2026.md)的代理段） |
| 插件里看不到 GPT-5.6 系列 | 客户端版本旧 | 更新插件和 CLI 到最新版 |

关于地区限制：若代理配置持续报错，改用 Codex CLI 或插件（而非在 Cursor 对话框中切换模型）通常更稳，二者走官方登录通道而非 API 通道。

## FAQ

Q: 插件和 CLI 同时装会冲突吗？

A: 不会。两者共享登录态与会话，同时安装是官方推荐用法。

Q: 插件要单独付费吗？

A: 不用。插件直接使用当前 ChatGPT 账号的权限（免费可用轻量档，Plus 解锁完整能力）。

Q: Vim / Neovim 有插件吗？

A: 以官方文档列出的支持范围为准；常用做法是在终端中配合 CLI 使用。

Q: IDE 插件的权限怎么控制？

A: 采用与 CLI 相同的审批机制（`/approvals`），可设置哪些操作自动执行、哪些需要确认。重要项目建议开启确认模式。

## 相关阅读

- [Codex CLI 使用教程：安装、登录、常用命令（2026）](codex-cli-tutorial-2026.md)
- [Codex 入门：五种形态、五大场景（2026）](codex-getting-started-2026.md)
- [AI 编程工具对比：Codex vs Claude Code vs Cursor vs Gemini（2026）](../01-models-and-tools/ai-coding-tools-comparison-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials)
