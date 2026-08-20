---
title: "Codex CLI 国内使用全攻略 2026：终端、VS Code、Cursor、Opencode 四种用法"
description: "Codex CLI 国内安装使用完整教程：Node 环境配置、npm 安装与镜像加速、登录授权、常用命令，以及 VS Code 插件、Cursor 集成、Opencode 三种替代方案。附代理配置和常见坑解决。"
keywords:
  - Codex CLI
  - Codex 使用教程
  - Codex 国内使用
  - Codex 安装
  - Codex VS Code
  - Codex Cursor
  - OpenAI Codex 教程
updated: 2026-08-20
---

# Codex CLI 国内使用全攻略 2026：终端、VS Code、Cursor、Opencode 四种用法

> 改编自 [PayForChat 官网教程](https://payforchat.com/articles/2026-codex-cli-cursor-vscode-opencode?ref=github)。

官方说 Codex 是「云端编程 Agent」，实际体验是：一个跑在终端里的 ChatGPT，能读你的项目、改代码、跑命令。代码审查能力很强，速度比 Claude Code 慢一些，但胜在稳定、门槛低——任何付费 ChatGPT 套餐都能解锁。

## 前提条件

- ChatGPT Plus / Pro / Team 任一付费订阅（免费账号用不了 Codex CLI；国内付款问题见[充值教程](../01-chongzhi-jiaocheng/chatgpt-plus-chongzhi-jiaocheng-2026.md)）
- 可用的代理环境

## 方式一：Codex CLI 终端使用（推荐）

### 安装 Codex CLI

要求 Node.js 22+（`node -v` 检查）：

```bash
npm install -g @openai/codex@latest
# 国内网络慢可加镜像：
npm install -g @openai/codex@latest --registry=https://registry.npmmirror.com
# Mac 也可以：brew install codex
```

`codex --version` 验证安装。

### 登录授权

项目目录下运行 `codex`，选浏览器登录，用付费 ChatGPT 账号授权。首次会选执行模式：自动执行 或 每步确认（建议先选每步确认）。凭证存在 `~/.codex/`。

### Codex 常用命令

| 命令 | 作用 |
|---|---|
| `/model` | 切换模型 |
| `/approvals` | 切换权限模式 |
| `/status` | 查看当前状态 |
| `/compact` | 压缩上下文 |
| `/review` | 代码审查 |
| `/resume` / `/fork` | 恢复 / 分叉会话 |

实用技巧：Codex 支持多模态，报错截图可以直接粘贴；在项目根目录启动能拿到完整上下文；`codex --full-auto` 全自动模式适合测试环境，生产环境慎用。

### 第三方 API 接入（可选）

编辑 `~/.codex/config.toml` 配置自定义 `model_provider`、`base_url` 和模型（如 `gpt-5-codex`），并在 `~/.codex/auth.json` 里填 `{"OPENAI_API_KEY": "sk-..."}`。

## 方式二：Codex VS Code 插件

扩展市场装官方 OpenAI Codex 插件，浏览器跳转登录 Plus 账号，侧边栏直接对话。选中代码右键「Ask Codex」最常用。

## 方式三：Cursor 集成 Codex

两条路：

1. **装 Codex 插件**（推荐）：走你的 ChatGPT 订阅额度。
2. **Cursor 模型切换里选 OpenAI**：走的是 OpenAI API 按量计费，需要在 Settings → Models 填 API key，和订阅是两回事。

遇到 "This model provider doesn't serve your region" 报错：开全局代理，或在 Cursor 设置里配代理。解决不了就回插件/CLI 方案，更稳。

## 方式四：Opencode 接入 ChatGPT 订阅

opencode.ai 下载客户端 → 添加项目 → `/model` 或「connect provider」选 OpenAI → 登录 Plus/Pro 账号，直接用订阅额度。

## Codex 常见坑与解决

| 问题 | 解决 |
|---|---|
| `npm ERR` 装不上 | 升 Node 22+ |
| 一直转圈 "thinking" | 开全局代理，或设 `export HTTPS_PROXY=http://127.0.0.1:7890`（端口按自己代理改） |
| 付款被 declined | 见[常见报错](../02-changjian-baocuo/chatgpt-fukuan-beiju-baocuo-jiejue.md) |
| Cursor 里没有 Codex 模型 | 更新 Cursor 到最新版 |

## 多工具搭配建议

重度用户的常见组合：Gemini 写前端、Claude Code 主力开发、Codex 做代码审查。各取所长，比一个工具打全场效率高。

## 相关阅读

- [Codex 需要充值吗？Codex 和 ChatGPT 的关系](../01-chongzhi-jiaocheng/codex-xuyao-chongzhi-ma-2026.md)
- [ChatGPT Plus 充值教程](../01-chongzhi-jiaocheng/chatgpt-plus-chongzhi-jiaocheng-2026.md)
- [ChatGPT 常见报错与解决](../02-changjian-baocuo/chatgpt-fukuan-beiju-baocuo-jiejue.md)
