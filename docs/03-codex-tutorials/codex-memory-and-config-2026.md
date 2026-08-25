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

> 配置文件字段随版本迭代，以官方文档和 `codex --help` 为准；本文讲三层结构和通用字段。

「每次都要跟 Codex 重新交代一遍项目规范」——这是没配置记忆时的日常。Codex 的记忆分三层，各管一件事：**项目级（AGENTS.md）管约定，客户端级（~/.codex/）管配置，会话级（/resume 等）管进行中的工作**。这篇把三层一次配明白。

废话不多说，结论先放这儿：

1. **先写 AGENTS.md**——一次投入，所有任务受益，是三层里性价比最高的。
2. `~/.codex/config.toml` 管客户端行为（模型偏好、鉴权方式），一般装完就不用动。
3. 会话三板斧：`/resume` 续会话、`/fork` 分叉尝试、`/compact` 压缩上下文。

## 第一层：项目记忆——AGENTS.md

在**仓库根目录**放一个 `AGENTS.md`（Markdown 文件），Codex 每次执行任务前自动读取。它解决的是「Codex 能读你的代码，但不知道你的规矩」：

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

写法三原则：**写指令不写散文**（「用 pnpm」优于「我们倾向于使用 pnpm」）；**写例外和禁区**（哪里不能动比哪里能动更重要）；**保持短**（一屏内，太长遵循度下降）。

团队场景下这个文件进版本库，所有人的 Codex 行为一致；同类文件机制（CLAUDE.md 等）在多个 AI 编程工具间通用，写一份多处受益。

## 第二层：客户端配置——~/.codex/

家目录下的 `.codex/` 目录存放 Codex CLI 的本地状态：

- **auth.json**：登录凭证。账号登录后自动生成；API Key 用户手动填 `{"OPENAI_API_KEY": "sk-..."}`——两种鉴权方式对应订阅额度 vs 按 token 计费（对照见 [CLI 教程](codex-cli-tutorial-2026.md)）
- **config.toml**：客户端配置。可设置默认模型、推理强度、鉴权偏好等；第三方 API 用户在这里配自定义 endpoint

多数人装完即用、终身不改。需要动的典型场景：固定默认模型（省得每次 `/model` 切）、接自定义模型服务。

## 第三层：会话管理——进行中的记忆

会话内的对话历史就是 Codex 的短期记忆（受上下文窗口约束，原理见[大模型是什么](../00-ai-fundamentals/what-is-llm-2026.md)）。三个命令管好它：

| 命令 | 作用 | 场景 |
|---|---|---|
| `/resume` | 恢复历史会话 | 第二天继续昨天的重构（历史自动保存） |
| `/fork` | 从当前点分叉新对话 | 想试另一种方案，保留当前进度 |
| `/compact` | 压缩上下文 | 长会话变慢/变笨时释放空间（也会自动触发） |

配套习惯：**按主题分会话**——一个会话一个任务链，别让订单重构和文档翻译共享上下文（互相污染）。换任务 `/new`，隔天 `/resume`。

## 三层记忆的分工总结

| 层 | 载体 | 生命周期 | 记什么 |
|---|---|---|---|
| 项目 | AGENTS.md | 跟随仓库 | 团队约定、规范、禁区 |
| 客户端 | ~/.codex/ | 跟随机器 | 鉴权、默认模型 |
| 会话 | 对话历史 | 单次任务链 | 当前任务的来龙去脉 |

记忆外置到文件的本质：**上下文窗口会满、会话会结束，文件不会**。重要信息沉到 AGENTS.md，临时信息留在会话里。

## FAQ

Q: AGENTS.md 会拖慢任务、多耗额度吗？

A: 每次任务会读取它（占用少量上下文），换来的省掉重复交代和跑偏返工，净收益为正。但别把它写成百科全书——只放高频需要的约定。

Q: 已有 CLAUDE.md / 其他工具的说明文件，要重写吗？

A: 内容可直接复用，文件名按你主力工具的约定来；多工具并存的仓库常见做法是放一份内容或互相引用。

Q: 换电脑要迁移什么？

A: 重新登录账号即可（auth.json 不建议拷贝，等于分享登录凭证）；config.toml 有自定义配置的话拷它；AGENTS.md 在仓库里，clone 即得。

Q: /compact 之后它还记得之前的细节吗？

A: 压缩是摘要化的——大意保留，细节有损。所以重要决定和规范要及时沉到 AGENTS.md，别只活在会话里。

## 相关阅读

- [Codex 提示词实战：任务描述、上下文、分步提交（2026）](codex-prompt-guide-2026.md)
- [Codex Skills 用法：/skills 机制、技能怎么写（2026）](codex-skills-guide-2026.md)
- [Codex CLI 使用教程：安装、登录、常用命令（2026）](codex-cli-tutorial-2026.md)
