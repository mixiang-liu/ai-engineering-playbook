# AI Engineering Playbook

面向 Java 开发者的 AI 工程化学习与项目仓库：**结合工作、按需跳学**，边学边做，持续沉淀可复用资产。

## 目标
- 建立可落地的 AI 能力，服务当前 Java 后端工作（两条主线：用 AI 提效 + 把 AI 建进产品）
- 每个学到的知识点都有 1 篇笔记 + 尽量 1 个可运行产出
- 形成可展示的项目作品集（代码 + 指标 + 文档）

## 怎么用这个仓库

不按周推进——用**地图 + 台账**：

1. 看 [`docs/learning-roadmap.md`](docs/learning-roadmap.md) —— 全貌地图，带状态标记（`[ ]`/`[~]`/`[x]`），不规定顺序
2. 结合手头工作挑一个能立刻用上的节点开始学
3. 学完在 `notes/` 对应目录写笔记（用 `notes/_template.md`），并把地图节点状态更新
4. 在 [`docs/progress-log.md`](docs/progress-log.md) 记一行：工作任务 → 点亮节点 → 笔记路径

## Java-First 技术栈
- `Java 21` · `Spring Boot 3` · `Maven`
- `Spring WebClient`（流式/SSE） · `Jackson`（结构化输出）
- AI 框架：`Spring AI 2.0`（主线） / `LangChain4j`（选型对比见 [`docs/java-stack.md`](docs/java-stack.md)）

## 仓库结构
- `docs/` 学习地图与台账
  - `learning-roadmap.md` 三分骨架地图（主干 / AI Coding / AI 应用开发）
  - `progress-log.md` 学习台账（工作 ↔ 学习 双向锚定）
  - `java-stack.md` 技术栈与框架选型
  - `glossary.md` 中英术语表
  - `resources.md` 精选学习资料
- `notes/` 分层学习笔记（`foundations/` `ai-coding/` `app-dev/`）
- `prompts/` 提示词模板与评测样本
- `projects/` 实战项目（`llm-playground/` 为 LLM 调用基座）
- `shared/` 共享 schema 与工具

## 快速开始
1. `cp .env.example .env` 并填入密钥
2. 打开 `docs/learning-roadmap.md`，挑一个节点
3. 学完写 `notes/`、更新地图状态、记 `progress-log.md`

## 工作原则
- 先可用，再优化
- 先指标，再感觉
- 先复用，再重写
