---
layout:     post
title:      "[Tool] Hermes Agent 使用说明"
subtitle:   "把 LLM 拽回终端 — 一份非官方上手指南"
date:       2026-06-14
author:     Mr.X | X师傅
header-img: img/post-bg-hacker.jpg
catalog: true
tags:
    - tool
    - ai
    - hermes
    - agent
    - cli
    - english
---

## 写在前面

Dear Data Scientist,

用过 Claude Code 吗？用过 Codex CLI 吗？用过 OpenCode 吗？
如果你已经习惯了在终端里跟一个会自己读文件、自己跑命令、自己 debug 的 LLM 协作——那么 **Hermes Agent** 是同赛道里更激进的一个选择。

Hermes 是 [Nous Research](https://nousresearch.com/) 出品的开源 agent 框架，定位就是「**自己会进化的 LLM agent**」——靠 **skills**、**memory**、**profiles**、**cron**、**kanban** 这几样东西把"一次性对话"变成"会累积经验的工作流"。

> 一句话：跑 `hermes` 之后，它会记得你是谁、你机器长什么样、你下次想做啥时直接接上。

## 为什么不是 Claude Code

| 维度 | Hermes | Claude Code |
|---|---|---|
| 供应商 | Nous Research（中立，20+ providers） | Anthropic 锁定 |
| 模型 | 任何 OpenAI 兼容端点（OpenRouter / Anthropic / DeepSeek / 本地 GGUF） | 仅 Claude |
| 运行位置 | CLI / Telegram / Discord / Slack / Email / Matrix / API | CLI / IDE 集成 |
| 自进化 | **核心卖点** — skills 累积、memory 跨 session | 无 |
| Profiles | 多个隔离身份（每个独立的 skills/sessions/memory） | 无 |
| Cron | 内置 scheduler | 无 |
| Kanban | 多 agent 工作队列 | 无 |
| 价格 | 取决于底层 provider（可用免费层：Codex OAuth / Gemini） | $20/月起步 |

简单说：**Claude Code 是产品，Hermes 是框架**。如果你只是想用 AI 写代码，Claude Code 省心；如果你想自己搭一套"AI 团队"、跨平台运行、长期积累 workflows——Hermes 是更上游的工具。

## 5 分钟上手

### 安装

```bash
curl -fsSL https://raw.githubusercontent.com/NousResearch/hermes-agent/main/scripts/install.sh | bash
```

### 第一次跑

```bash
hermes                    # 交互式 chat
hermes chat -q "你的问题" # 单次提问
hermes setup              # 引导式配置向导
hermes doctor             # 自检依赖 / 配置
```

### 换模型

```bash
hermes model              # 交互选 model + provider
# 或
hermes config set model.default openrouter/anthropic/claude-sonnet-4
hermes config set model.provider openrouter
```

> 注意：模型换完要在新 session 里生效（`/reset` 或新开 `hermes`），不会影响已缓存的 prompt。

## 五个核心概念（记住这五个就够用）

### 1. Skills — 经验包

`~/.hermes/skills/` 下的每个 `SKILL.md` 都是一份"可复用的工作流"。

- 装一个：`hermes skills install <id>` 或 `hermes skills install https://example.com/SKILL.md`
- 列表：`hermes skills list`
- 用：在对话里 `/skill <name>` 预加载，或让 agent 自己挑
- **关键**：当 agent 解决了一个非平凡问题（5+ 步 / 反复试错 / 用户纠正过），它可以**自己写一份 skill 存下来**——下次再遇到类似问题，session 一开始就会加载

这是我最看重的特性。Claude Code 给你的永远是「一次性」的能力；Hermes 是真的会在你机器上**长出肌肉记忆**。

### 2. Memory — 跨 session 记忆

两份：

- `memory`（agent 自己的笔记）：环境信息、踩过的坑、用户偏好
- `user_profile`（你是谁）：姓名、角色、风格

写法：

```python
memory(action="add", target="memory", content="用户在 macOS 14.5，Python 3.11/3.12 都有，uv 已装")
```

约束：写**会过期的**事实（PR 编号、commit SHA、临时 TODO）会污染记忆库。只写**跨 session 还有用**的稳定事实。

### 3. Profiles — 多个身份

```bash
hermes profile list
hermes profile create work
hermes profile use work
```

每个 profile 独立 `~/.hermes/profiles/<name>/{config, sessions, skills, memory}`。我用 `default` 当树洞、另一个 profile 跑业务——彼此不串。

### 4. Cron — 定时任务

```bash
hermes cron create "0 6 * * *" "汇总昨天的项目动态" --name daily-recap
hermes cron list
hermes cron run <id>   # 立即触发
```

支持 5-field cron / `every 2h` / ISO timestamp。可以挂 skills、override model、改 workdir。是做"AI 助理主动汇报"的基础设施。

### 5. Kanban — 多 agent 协作

一个 SQLite 看板，多个 profile 当 worker 抢任务。配合 dispatcher 可以做「一主机跑 N 个 AI 员工」的效果。一人公司场景的核武器。

```bash
hermes kanban init
hermes kanban create --title "调研 XX" --assign work
```

## 实际工作流：把一篇 blog push 到 GitHub

下面是我 5 分钟前刚跑完的（就是这篇）。

```bash
# 1) 配 GitHub 认证（macOS keychain 比 store 安全）
git config --global credential.helper osxkeychain
# 触发一次 git 操作弹 Keychain 授权，之后免输入

# 2) 写 blog（X师傅风格，零 emoji，中英夹杂）
write_file path="_posts/2026-06-14-[Tool] Hermes Agent 使用说明.md" content="..."

# 3) 提交 + push
git add _posts/2026-06-14-*.md
git commit -m "new post: Hermes Agent 使用说明"
git push origin main
```

## 我用 Hermes 干什么

- **日常 CLI 替代**：找文件、改 config、跑脚本，比手动快 3-5 倍
- **跨平台随手记**：iPhone 发个 Telegram → 树洞 profile → 6am 自动汇总
- **一人公司后台**：cron 跑 daily recap、kanban 跑调研、profile 隔离业务和私人
- **新模型沙盒**：换底层 provider 不用动 workflow

## 坑提醒

1. **Hermes ≠ Claude Code UI**。它没图形界面，CLI 输入依赖 prompt_toolkit。Windows 装 WSL。
2. **Skills 不是越多越好**。一上来装 50 个 skill 只会让 prompt 臃肿。先用 `hermes skills list` 看 bundle 里那批，按需加。
3. **Cron session 拿不到你的当前对话上下文**。prompt 要写得 self-contained。
4. **Token 池轮换**：如果你用 OpenRouter，建议 `hermes auth add` 配多个 key，agent 会自动 rotate。
5. **安全开关**：`approvals.mode` 默认 `manual`（会弹审批），想省事就 `hermes config set approvals.mode smart`，不推荐 `off`。

## 资源

- 官方文档：https://hermes-agent.nousresearch.com/docs/
- GitHub：https://github.com/NousResearch/hermes-agent
- Skills Hub：`hermes skills browse`
- 跟我聊天：本文是 Hermes 协助撰写（然后 X 师傅 review + 加了点人味）

## Table of Content

- [写在前面](#写在前面)
- [为什么不是 Claude Code](#为什么不是-claude-code)
- [5 分钟上手](#5-分钟上手)
- [五个核心概念](#五个核心概念记住这五个就够用)
- [实际工作流](#实际工作流把一篇-blog-push-到-github)
- [我用 Hermes 干什么](#我用-hermes-干什么)
- [坑提醒](#坑提醒)
- [资源](#资源)

Good luck!
