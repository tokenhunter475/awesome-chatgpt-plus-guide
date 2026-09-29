---
title: "Codex 记忆与配置：AGENTS.md、config.toml、会话管理（2026）"
description: "Codex 的三层记忆机制讲解：项目级 AGENTS.md（全局约定）、~/.codex/config.toml（客户端配置）、会话管理（/resume、/fork、/compact）。让 Codex 记住你的项目规范，不用每次重复交代。"
keywords:
  - Codex AGENTS.md
  - Codex config.toml
  - Codex 记忆
  - Codex 配置
  - Codex resume
  - Codex 会话管理
updated: 2026-08-20
---

# Codex 记忆与配置：AGENTS.md、config.toml、会话管理（2026）

> 配置文件字段随版本迭代，以官方文档和 `codex --help` 为准；这里介绍三层结构和通用字段。

不配置记忆时，每次都要跟 Codex 重新交代项目规范。Codex 的记忆分三层：**项目级（AGENTS.md）管约定，客户端级（~/.codex/）管配置，会话级（/resume 等）管进行中的工作**。

核心原则：

1. **先写 AGENTS.md**——一次投入，所有任务受益，性价比最高。
2. `~/.codex/config.toml` 管客户端行为（模型偏好、鉴权方式），通常装完不用改动。
3. 会话常用三个命令：`/resume` 续会话、`/fork` 分叉尝试、`/compact` 压缩上下文。

## 第一层：项目记忆——AGENTS.md

在**仓库根目录**放一个 `AGENTS.md`（Markdown 文件），Codex 每次执行任务前自动读取，用于补充代码之外的规则。

建议写的内容（按优先级）：

```markdown
# 项目说明
- 技术栈：Next.js 15 App Router + TypeScript + Supabase
- 包管理：pnpm（不要用 npm）

# 常用命令
- 测试：pnpm test
- 构建：pnpm build

# 代码规范
- 组件用函数式 + hooks，不用 class
- API 返回统一 { code, data, message } 结构
- 提交信息用中文，格式：模块：做了什么

# 注意事项
- src/legacy/ 目录不要动，正在迁移
- 数据库 schema 改动必须走 migrations/
```

编写原则：**写指令不写散文**（「用 pnpm」优于「我们倾向于使用 pnpm」）；**写例外和禁区**（哪里不能动比哪里能动更重要）；**保持短**（控制在一屏内，太长遵循度下降）。

该文件提交到版本库后，团队成员的 Codex 行为可保持一致；同类机制（CLAUDE.md 等）在多个 AI 编程工具间通用，写一份多处可用。

## 第二层：客户端配置——~/.codex/

家目录下的 `.codex/` 目录存放 Codex CLI 的本地状态：

- **auth.json**：登录凭证。账号登录后自动生成；API Key 用户手动填 `{"OPENAI_API_KEY": "sk-..."}`——两种鉴权方式对应订阅额度 vs 按 token 计费（对照见 [CLI 教程](codex-cli-tutorial-2026.md)）
- **config.toml**：客户端配置。可设置默认模型、推理强度、鉴权偏好等；第三方 API 用户在这里配自定义 endpoint

多数情况装完即用。需要修改的场景主要是固定默认模型（省去每次用 `/model` 切换）或接入自定义模型服务。

## 第三层：会话管理——进行中的记忆

会话内的对话历史是 Codex 的短期记忆，受上下文窗口约束（原理见[大模型是什么](../00-ai-fundamentals/what-is-llm-2026.md)）。常用三个命令管理：

| 命令 | 作用 | 场景 |
|---|---|---|
| `/resume` | 恢复历史会话 | 第二天继续昨天的重构（历史自动保存） |
| `/fork` | 从当前点分叉新对话 | 想试另一种方案，保留当前进度 |
| `/compact` | 压缩上下文 | 长会话变慢/变笨时释放空间（也会自动触发） |

建议按主题分会话，单会话对应单个任务链，避免不同任务共享上下文产生干扰。开启新任务用 `/new`，隔天继续用 `/resume`。

## 三层记忆的分工总结

| 层 | 载体 | 生命周期 | 记什么 |
|---|---|---|---|
| 项目 | AGENTS.md | 跟随仓库 | 团队约定、规范、禁区 |
| 客户端 | ~/.codex/ | 跟随机器 | 鉴权、默认模型 |
| 会话 | 对话历史 | 单次任务链 | 当前任务的来龙去脉 |

上下文窗口会满、会话会结束，但文件会留存。重要信息写入 AGENTS.md，临时信息留在会话里。

## FAQ

Q: AGENTS.md 会拖慢任务、多耗额度吗？

A: 每次任务会读取该文件并占用少量上下文，但能省去重复交代和返工成本。不用写成百科全书，只放高频约定的内容。

Q: 已有 CLAUDE.md / 其他工具的说明文件，要重写吗？

A: 内容可直接复用，文件名按主力工具约定设置；多工具并存的仓库可以直接保留一份内容或互相引用。

Q: 换电脑要迁移什么？

A: 重新登录账号即可（auth.json 不建议拷贝，以免泄露登录凭证）；config.toml 有自定义配置的话单独复制；AGENTS.md 随代码仓库 clone 即可获取。

Q: /compact 之后它还记得之前的细节吗？

A: 压缩属于摘要提取，会保留大意但丢失部分细节。重要的决定和规范应及时写入 AGENTS.md，不要仅留在会话中。

## 相关阅读

- [Codex 提示词实战：任务描述、上下文、分步提交（2026）](codex-prompt-guide-2026.md)
- [Codex Skills 用法：/skills 机制、技能怎么写（2026）](codex-skills-guide-2026.md)
- [Codex CLI 使用教程：安装、登录、常用命令（2026）](codex-cli-tutorial-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials)
