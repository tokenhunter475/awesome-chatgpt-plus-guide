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

Codex CLI 是 OpenAI 官方的终端编程工具：进入项目目录启动后，用自然语言描述需求，工具会直接读取代码、修改文件并执行命令。

核心概括：

1. **Mac/Linux**：运行官方脚本安装（`curl -fsSL https://chatgpt.com/codex/install.sh | sh`）。
2. **Windows**：原生沙箱处于实验状态，**官方推荐在 WSL2 中运行**，体验与 Linux 一致。
3. **登录**：使用 ChatGPT 账号（免费账号也支持，模型和额度取决于套餐）；CLI 与 IDE 插件共享登录态。

## 开始前：两个前置条件

**Node.js 22+。** Codex CLI 基于 Node 运行，版本不足会导致安装失败或运行报错。先运行 `node -v` 检查，低于 22 需要到 [nodejs.org](https://nodejs.org/) 升级（Windows 可用 .msi 安装包，Mac/Linux 可用 nvm）。

**登录方式二选一。** 决定了额度扣除方式：

| 登录方式 | 适合谁 | 计费 |
|---|---|---|
| ChatGPT 账号登录 | 个人用户（推荐） | 走订阅额度，无独立计费 |
| API Key | 团队 / CI 场景 | 按 token 计费，需 API 账户余额 |

套餐档位和额度的对应关系（免费账号支持轻量档，Plus 支持旗舰档）见 [Codex 和 GPT 的区别](codex-vs-gpt-difference-2026.md)。

## 安装

### Mac / Linux

**方式 1：官方脚本（推荐，自动匹配架构）**

```bash
curl -fsSL https://chatgpt.com/codex/install.sh | sh
```

**方式 2：npm**

```bash
npm install -g @openai/codex
```

国内网络较慢可指定镜像源：

```bash
npm install -g @openai/codex --registry=https://registry.npmmirror.com
```

**方式 3：Homebrew（注意）**

```bash
brew install --cask codex
```

注意：Homebrew cask 在部分环境下安装的是**桌面 App 而非 CLI**。如果安装后终端找不到 `codex` 命令，改用 npm 或官方脚本安装。

### Windows

**方式 1：官方 PowerShell 脚本**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 | iex"
```

**方式 2：winget**

```powershell
winget install OpenAI.Codex
```

**Windows 环境说明**：Codex 在原生 Windows 上运行依赖 AppContainer 沙箱，默认限制文件写入与网络访问，官方仍标记为实验特性。生产使用建议选择 **WSL2**：

1. 安装 WSL2 + Ubuntu
2. 在 WSL 中按 Mac/Linux 流程安装
3. 将项目仓库放在 Linux 家目录（如 `~/projects/`），避免放在 `/mnt/c/...` 跨文件系统挂载路径以防性能下降

### 两个通用注意事项

- **npm 包名必须带 scope**：包名为 `@openai/codex`。不带 scope 的 `codex` 是 2012 年发布的无关包。
- **安装验证**：运行 `codex --version`，正常输出版本号即安装成功。

## 登录授权

进入项目目录运行：

```bash
cd ~/your-project
codex
```

首次运行会引导打开浏览器登录 ChatGPT 账号（若未自动打开可复制终端输出的 URL）。登录成功后，Codex 会请求当前目录的操作权限：

- **选项 1**：允许直接修改目录下文件、执行命令，过程不逐条确认
- **选项 2**：修改文件或执行命令前均需手动确认

个人项目选 1 更快捷；重要项目选 2 确认安全。授权凭证保存在 `~/.codex/` 目录，后续启动无需重复登录。

**API Key 用户**：在 `~/.codex/auth.json` 中配置 `{"OPENAI_API_KEY": "sk-..."}` 即可跳过浏览器登录。

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

参数 `--dangerously-bypass-approvals-and-sandbox` 会跳过所有确认并禁用沙箱，仅适用于一次性隔离测试环境。

## 实用技巧

**进入项目根目录启动。** Codex 会读取当前目录上下文，先 `cd` 到根目录再执行 `codex`，无需手动提供项目背景。

**直接粘贴报错截图。** 模型具备多模态能力，可识别截图中的报错文本和界面并提供修复方案。

**长耗时任务使用云端。** 终端适合交互迭代；跨多文件的大型重构可在网页版（chatgpt.com/codex）提交异步任务，本地与云端共用额度。

**代理环境变量配置。** 若登录后停留在 thinking 或出现连接超时：

```bash
export HTTPS_PROXY=http://127.0.0.1:7890
export HTTP_PROXY=http://127.0.0.1:7890
codex
```

将 `7890` 替换为实际代理端口。

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

A: 工具本身免费。使用 ChatGPT 账号登录即可使用，免费账号包含轻量模型额度；更高级的模型档位和额度需要 Plus/Pro 订阅。也可以使用 API Key 按 token 计费。

Q: CLI 和 VS Code 插件需要分别登录吗？

A: 不需要。两者共享登录态与会话，终端发起的任务可在 IDE 插件中继续查看。

Q: 为什么官方推荐 Windows 用户使用 WSL2？

A: 原生 Windows 依赖的 AppContainer 沙箱属于实验状态，会限制文件与网络访问。WSL2 环境与 Linux 表现一致；需注意将代码放置在 Linux 原生文件系统，不要使用 `/mnt/c/` 路径。

Q: Codex 和 Claude Code 选哪个？

A: 需要低门槛接入（直接使用 ChatGPT 账号）或重度依赖代码审查可选 Codex；更注重响应速度可考虑 Claude Code。对比细节参考 [Codex 和 GPT 的区别](codex-vs-gpt-difference-2026.md)。

Q: 为什么用量消耗比预期快？

A: 2026 年 4 月起用量按 token 消耗统计，大型仓库或长对话消耗更快；本地与云端任务共享统一额度。规则见 [Codex 用量上限说明](codex-usage-limits-2026.md)。

## 参考来源

- [OpenAI Codex 官方文档](https://developers.openai.com/codex/)
- [openai/codex GitHub 仓库](https://github.com/openai/codex)

## 相关阅读

- [Codex 和 GPT 的区别是什么？（2026）](codex-vs-gpt-difference-2026.md)
- [Codex 用量上限说明：5 小时窗口与周上限（2026）](codex-usage-limits-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials)
