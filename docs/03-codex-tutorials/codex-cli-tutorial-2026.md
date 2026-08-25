---
title: "Codex CLI 使用教程 2026：Mac/Windows 安装、登录、常用命令与常见坑"
description: "OpenAI Codex CLI 完整使用教程：npm/官方脚本/winget 各平台安装方法，ChatGPT 账号登录授权流程，/model、/status、/review 等常用命令速查，brew 装成桌面版、npm 包名装错、Windows 沙箱等高频坑的解决办法。"
keywords:
  - Codex CLI 教程
  - Codex 安装
  - Codex 命令
  - Codex CLI 登录
  - Codex Windows 安装
  - Codex 使用方法
updated: 2026-08-20
---

# Codex CLI 使用教程 2026：Mac/Windows 安装、登录、常用命令与常见坑

> CLI 子命令随版本迭代较快，以 `codex --help` 实际输出为准；本文 2026 年 8 月更新。

Codex CLI 是 OpenAI 官方的终端编程工具：进到项目目录里启动，用自然语言描述需求，它直接读代码、改文件、跑命令。这篇把安装、登录、日常用法和已知坑一次讲完。

简单来说：

1. **Mac/Linux**：一行官方脚本装完（`curl -fsSL https://chatgpt.com/codex/install.sh | sh`），最省事。
2. **Windows**：可以装，但原生沙箱还是实验性状态，**官方推荐跑在 WSL2 里**，体验等同 Linux。
3. **登录**用 ChatGPT 账号（免费账号也能登录，模型和额度跟着套餐走）；CLI 和 IDE 插件共享登录态，登录一次两边通用。

## 开始前：两个前置条件

**Node.js 22+。** Codex CLI 基于 Node 运行，版本不够会装失败或运行报错。先跑 `node -v` 确认，低于 22 就去 [nodejs.org](https://nodejs.org/) 升级（Windows 下 .msi 安装包一路下一步；Mac/Linux 可用 nvm）。

**登录方式二选一。** 这决定了额度从哪扣：

| 登录方式 | 适合谁 | 计费 |
|---|---|---|
| ChatGPT 账号登录 | 个人用户（推荐） | 走订阅额度，无独立计费 |
| API Key | 团队 / CI 场景 | 按 token 计费，需 API 账户余额 |

套餐档位和额度的关系（免费账号可用轻量档，Plus 解锁旗舰档）见 [Codex 和 GPT 的区别](codex-vs-gpt-difference-2026.md)。

## 安装

### Mac / Linux

**方式 1：官方脚本（推荐，自动选对架构）**

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

**方式 2：npm**

```bash
npm install -g @openai/codex
```

国内网络慢，加镜像源：

```bash
npm install -g @openai/codex --registry=https://registry.npmmirror.com
```

**方式 3：Homebrew（有坑）**

```bash
brew install --cask codex
```

已知坑：cask 在部分环境装的是**桌面 App 而不是 CLI**——装完终端里没有 `codex` 命令就是中招了，别折腾 brew，换 npm 或官方脚本装即可。

### Windows

**方式 1：官方 PowerShell 脚本**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"
```

**方式 2：winget**

```powershell
winget install OpenAI.Codex
```

**Windows 用户必读**：Codex 在原生 Windows 上用 AppContainer 沙箱，默认限制文件写入和网络访问，官方截至发稿仍标注实验性。稳定跑法是 **WSL2**：

1. 装好 WSL2 + Ubuntu
2. 在 WSL 里按 Mac/Linux 方式安装
3. 仓库放在 Linux 家目录（如 `~/projects/`），不要放 `/mnt/c/...`——跨文件系统性能差一大截

### 两个通用坑

- **npm 包名必须带 scope**：是 `@openai/codex`。npm 上不带 scope 的 `codex` 是 2012 年的无关老包，装错不报错但完全不是这个东西。
- 装完验证：`codex --version` 有版本号输出才算装对。

坑这块多说一句：上面这些翻车点没一个是编的，全是社区里一遍遍被问的问题。装的时候撞上别慌——大家都撞过，撞上反而说明路子是对的。

## 登录授权

进入常用目录，直接运行：

```bash
cd ~/your-project
codex
```

首次运行会引导浏览器登录 ChatGPT 账号（没自动打开就手动复制终端里的链接）。登录成功后，Codex 会询问当前目录的工作权限：

- **选项 1**：允许直接修改目录下文件、执行命令，过程中不再逐条确认
- **选项 2**：任何修改和命令执行前都要求手动确认

日常自己项目选 1 省事；重要项目选 2 稳妥。授权后 token 自动保存到 `~/.codex/` 目录，下次启动不用重复登录。

**API Key 用户**：在 `~/.codex/auth.json` 里填入 `{"OPENAI_API_KEY": "sk-..."}` 即可，不需要浏览器登录。

## 常用命令速查

### 会话内命令（最常用的 7 个）

| 命令 | 作用 | 使用场景 |
|---|---|---|
| `/model` | 切换模型和推理强度 | 简单任务切低配省额度，复杂任务切高配 |
| `/status` | 查看模型、权限、额度剩余和重置时间 | 撞限额时第一步先跑它 |
| `/approvals` | 设置哪些操作要确认 | 信任的项目放开，重要的收紧 |
| `/review` | 审查当前改动 | 写完代码让 AI 过一遍再提交 |
| `/compact` | 压缩上下文 | 对话太长 token 快满时释放空间 |
| `/clear` | 清空对话历史 | 换话题，避免旧上下文干扰 |
| `/new` | 开新对话 | 当前任务完成，开始下一个 |

### 会话管理

| 命令 | 作用 |
|---|---|
| `/resume` | 恢复之前保存的对话（Codex 自动存历史） |
| `/fork` | 从当前对话分叉出新对话，保留原进度 |

### 启动参数

| 参数 | 作用 |
|---|---|
| `codex --full-auto` | 全自动模式，不逐条确认 |
| `codex -a on-request` | 每次执行命令前都要确认 |
| `codex --model <名称>` | 临时指定模型（可用列表以 `/model` 显示为准） |
| `codex --help` | 查看全部参数 |

另有一个 `--dangerously-bypass-approvals-and-sandbox` 参数会跳过所有确认并禁用沙箱——只建议在一次性测试环境用，生产项目慎用。

## 实用技巧

**进项目目录再启动。** Codex 自动读取当前目录的代码上下文，`cd` 到项目根目录再跑 `codex`，提问不用重复交代背景。

**报错直接截图贴进去。** Codex 是多模态模型，能读截图里的报错文字和界面，直接分析原因给修复方案。

**长任务交给云端。** 终端会话适合快速迭代；跨多文件的大重构可以在网页版（chatgpt.com/codex）提交云任务异步跑，本地和云端共享同一份额度。

**代理设置（网络超时看这里）。** 登录后一直 thinking 或连接超时，多半是网络问题：

```bash
export HTTPS_PROXY=http://127.0.0.1:7890
export HTTP_PROXY=http://127.0.0.1:7890
codex
```

把 `7890` 换成你自己的代理端口。

## 高频问题排查表

| 现象 | 原因 | 解决 |
|---|---|---|
| `npm ERR` 装不上 | Node 版本低于 22 | 升级 Node 后重装 |
| 装完没有 `codex` 命令 | brew cask 装成了桌面 App | 换 `npm install -g @openai/codex` |
| 装成了别的东西 | 用了不带 scope 的 `codex` 包 | 卸载后装 `@openai/codex` |
| 登录后一直 thinking | 网络不通 | 设置代理环境变量（见上） |
| 突然报 usage limit | 撞了 5 小时窗口或周上限 | 跑 `/status` 判断，处理方法见[用量上限说明](codex-usage-limits-2026.md) |
| 明明有额度却报限额 | 已知的 phantom limit bug | 升级 CLI 到最新版，重新登录 |

## FAQ

Q: Codex CLI 免费吗？

A: 工具免费。ChatGPT 账号登录即可使用，免费账号也能跑（轻量模型、额度有限）；更高模型档位和额度随 Plus/Pro 套餐解锁。也可以改用 API Key 按 token 计费。

Q: CLI 和 VS Code 插件要分别登录吗？

A: 不用。两者共享登录态和会话，终端里开的任务可以在 IDE 里接着看。

Q: 为什么官方推荐 Windows 用户用 WSL2？

A: 原生 Windows 的 AppContainer 沙箱仍是实验性，限制文件写入和网络。WSL2 下体验等同 Linux，注意仓库放 Linux 家目录，别放 `/mnt/c/` 路径。

Q: Codex 和 Claude Code 选哪个？

A: 侧重代码审查、要低门槛（ChatGPT 账号直接用）选 Codex；追求响应速度、能接受较高账号门槛的可以试 Claude Code。两者定位对比见 [Codex 和 GPT 的区别](codex-vs-gpt-difference-2026.md)。

Q: 用量突然变得特别快是为什么？

A: 2026 年 4 月起用量按 token 计算，大仓库长任务消耗天然高；另外本地和云端共享额度。完整机制和排查见 [Codex 用量上限说明](codex-usage-limits-2026.md)。

## 参考来源

- [OpenAI Codex 官方文档](https://developers.openai.com/codex/)
- [openai/codex GitHub 仓库](https://github.com/openai/codex)

## 相关阅读

- [Codex 和 GPT 的区别是什么？（2026）](codex-vs-gpt-difference-2026.md)
- [Codex 用量上限说明：5 小时窗口与周上限（2026）](codex-usage-limits-2026.md)
