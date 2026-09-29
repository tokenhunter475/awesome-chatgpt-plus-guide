---
title: "Codex 提示词实战：任务描述、上下文给法、分步提交技巧（2026）"
description: "Codex 提示词实战教程：任务拆小、上下文结构（目标/文件/约定/参考/验证五要素）、先测试后实现、AGENTS.md 项目约定、设计稿转代码。附好坏对照示例，把任务成功率拉上去。"
keywords:
  - Codex 提示词
  - Codex prompt
  - Codex 任务描述
  - Codex 使用技巧
  - Codex 上下文
  - Codex 怎么提问
updated: 2026-08-20
---

# Codex 提示词实战：任务描述、上下文给法、分步提交技巧（2026）

> 实战口径来自社区验证用法；通用提问基础见[提示词入门](../02-chatgpt-getting-started/prompt-engineering-basics-2026.md)，这里只针对编程场景。

「开了 Plus，甩一句『帮我做个功能』，效果一般」是 Codex 最常见的翻车姿势。同样的模型，任务描述质量不同，成功率差距可达数倍。

1. **任务拆小**：一次提交一个职责单一的任务，大需求拆 4-5 步。
2. **上下文五要素**：目标、文件、约定、参考、验证，每个任务过一遍清单。
3. **项目约定写进 AGENTS.md**，配置一次全局生效。
4. **先跑测试、先写测试**，减少返工。

## 技巧一：任务拆小，不要一次甩一整个需求

云端或本地任务越大，出错概率越高，排查成本也越高。

> ❌ 「帮我做一个完整的用户管理系统，包含注册、登录、权限管理和数据导出」
> ✅ 「在 src/api/auth/ 目录下实现用户注册接口，使用 bcrypt 哈希密码，Zod 做参数校验，返回 JWT token」

后者一次就能跑对。前者拆成四步更稳妥：注册 → 登录 → 权限 → 导出，每步验证后再做下一步。宁可多提交几次，不要一次赌大的。

## 技巧二：上下文五要素

Codex 能读仓库代码，但不知道你的项目约定与意图。每次提交任务按这五项给信息：

```
目标：[要做什么]
文件：[改哪些文件/目录]
约定：[框架、版本、代码规范]
参考：[现有的类似实现在哪里]
验证：[怎么判断做对了]
```

示例：

> 目标：给 /api/orders 接口加分页
> 文件：src/app/api/orders/route.ts
> 约定：项目用 Next.js 15 App Router + Supabase
> 参考：/api/articles/route.ts 里已实现分页，按那个模式来
> 验证：GET /api/orders?page=2&limit=10 返回正确的分页数据

平时怎么给新同事交代需求，就怎么写给 Codex。

其中**「参考」最关键**：给一个现成的代码样板，比写几段文字描述更管用；**「验证」次之**：给出可执行的验收标准，Codex 会先跑检查再交付结果（配合技巧四）。

## 技巧三：项目约定写进 AGENTS.md，不要每次重复

在仓库根目录放一个 `AGENTS.md`，写清技术栈和版本、目录结构、命名约定、常用命令（测试/构建/部署）以及代码风格。Codex 每次执行任务会自动读取，写一次全局生效。

这是外置项目上下文的标准做法（原理见 [Codex 记忆与配置](codex-memory-and-config-2026.md)）。不要在每次任务描述里重复粘贴规范，既冗长又容易遗漏。

## 技巧四：先测试，再改代码

分两种用法：

**基础用法**：任务描述里要求「先跑现有测试确保通过，改完之后再跑一遍」，避免引入回归 bug。

**TDD 模式**：要求先写测试再实现功能：

> 1. 先在 tests/api/orders.test.ts 写分页功能的测试用例
> 2. 然后修改 src/app/api/orders/route.ts 实现分页
> 3. 确保所有测试通过

测试先行给出了明确的完成信号和验收物，适合 Codex 的异步执行模式（见[云端任务](codex-cloud-tasks-2026.md)）。

## 附加技巧：图片输入

Codex 支持输入图片：直接贴设计稿或 UI 截图让它生成前端代码。实测参考：Figma 截图转 React 组件还原度约 70-80%，手绘草图能生成可用原型。提示词写法：

> 根据这张截图实现一个 React 组件，使用 Tailwind CSS，响应式设计，配色和布局尽量还原。

遇到终端或界面报错也可以直接贴截图，Codex 能识别图中的报错文字。

## 常见翻车对照

| 翻车姿势 | 修正 |
|---|---|
| 一次甩整个大需求 | 拆成单一职责的小任务链 |
| 「帮我优化一下这段代码」 | 写明维度：性能/可读性/安全，和验收标准 |
| 不给参考实现 | 指出仓库里最像的现成代码 |
| 验收靠肉眼 | 给可执行验证（测试、命令、URL） |
| 每次重复贴项目规范 | 移进 AGENTS.md |

## FAQ

Q: 任务描述写中文还是英文？

A: 都支持。中文描述搭配英文代码标识符最常见；核心在于结构和上下文，语言本身不影响效果。

Q: 小任务也要五要素吗？

A: 不用凑满。「改个文案」这类需求写清目标和文件即可。五要素清单主要用于卡壳时排查：生成结果不满意，多数是漏了其中某一项。

Q: 怎么让它别改不该改的文件？

A: 在「文件」项明确修改范围，并加上「不要改动其他文件」；权限层面开启确认模式（`/approvals`，见 [CLI 教程](codex-cli-tutorial-2026.md)）兜底。

Q: 这些技巧适用于其他编程 AI 吗？

A: 适用。任务拆解、上下文和验收标准是通用做法（对照见[AI 与 Agent 怎么选](../00-ai-fundamentals/ai-vs-agent-how-to-choose-2026.md)）。

## 相关阅读

- [Codex 工作流实战：从需求到上线的完整流程（2026）](codex-workflow-guide-2026.md)
- [Codex 记忆与配置：AGENTS.md、config.toml、会话管理（2026）](codex-memory-and-config-2026.md)
- [提示词入门：怎么向 AI 提问才能得到好答案（2026）](../02-chatgpt-getting-started/prompt-engineering-basics-2026.md)

---

<!-- payforchat-cta -->
> **Codex 额度不够，或还没有 Plus / Pro？** Codex 用量随 ChatGPT Plus / Pro 套餐附带。PayForChat 支持微信、支付宝付款，充在你自己的账号上，不需要密码，Plus 一般 1–3 分钟到账，充值失败全额退款。[看套餐](https://www.payforchat.com/plans?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials) · [Codex 代充指南](https://www.payforchat.com/articles/codex-recharge-guide-2026?utm_source=github&utm_medium=docs&utm_campaign=plus-guide&utm_content=03-codex-tutorials)
