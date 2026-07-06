# Learning Map (Java 后端视角)

> 这是一张**地图**，不是课程表。它给你全貌和位置，但**不规定顺序**——结合具体工作，跳着点亮节点即可。
> 进度记在 [`progress-log.md`](./progress-log.md)：哪个工作任务 → 点亮了哪个节点 → 沉淀到哪篇 notes。

## 状态标记

- `[ ]` 未学
- `[~]` 在学 / 部分了解
- `[x]` 已落地到工作或项目（不只是"看过"）

## 结构

三分：**主干**（两支共享地基）→ **AI Coding**（用 AI 提效）→ **AI 应用开发**（把 AI 建进产品）。
同一概念（MCP、Skills、Agent）常在 Coding 里先"用"、在应用开发里再"建"——Coding 天然是应用开发的动手预热。

---

## 主干 · 基础认知（两支都依赖）

### LLM 运行机制
- `[ ]` Token / 上下文窗口 / 采样参数（temperature、top_p）
- `[ ]` 幻觉成因（概率生成的本质、知识边界）
- `[ ]` 推理模型 vs Chat 模型（何时开推理 / 成本延迟权衡）
- `[ ]` 多模态作为默认能力（文本 + 图像 + 音频输入）

### X-Engineering 同心圆（全图图例 · 统一心智模型）
> 这些 `X-Engineering` 不是并列关系，而是**同心圆**：作用范围逐层放大，外层把内层包住。
> 记圈别记词——以后再冒出新的 `-Engineering`，套进这个圈定位即可。

```
Prompt  ⊂  Context  ⊂  Loop  ⊂  Harness
一条指令   单次输入    多步循环   整个运行时
```

- `[ ]` **Prompt Eng**：一条指令的措辞（角色 / few-shot / CoT）→ 见下方 Context 子集
- `[ ]` **Context Eng**：单次调用喂进窗口的**全部**信息 → 本主干重点（下一节）
- `[ ]` **Loop Eng**：一次调用如何变成多步循环（观察→行动→反馈、终止、重试）→ 落在 [应用开发 · Agent](#agent)
- `[ ]` **Harness Eng**：包裹模型的整个运行时（loop + 工具 + 记忆 + 护栏 + 监控 + 评测）→ 落在 [应用开发 · 系统设计](#系统设计) 和 [AI Coding](#分支一--ai-coding用-ai-提效)
- 心法：中心随应用形态外移——聊天时代重 Prompt，RAG 时代重 Context，Agent 时代重 Loop / Harness

### Context Engineering（横切核心，贯穿全程）
- `[ ]` 上下文预算 / 压缩 / 检索注入
- `[ ]` 多轮记忆的取舍
- `[ ]` Prompt 工程作为其子集：模板、few-shot、CoT

### 决策框架
- `[ ]` 何时用 Prompt、何时用 RAG、何时才需要微调

---

## 分支一 · AI Coding（用 AI 提效 · 我是"使用者"）

> ROI 最高、见效最快的一支——直接服务当前 Java 后端工作。

### 工具
- `[ ]` Claude Code / Cursor / Codex / IDE 插件

### 工作流
- `[ ]` Spec-Driven Coding（规范驱动，团队级主流工作流）
- `[ ]` CLAUDE.md / AGENTS.md 最佳实践
- `[ ]` Subagents / 多会话并行
- `[ ]` Skills（作为使用者体验——到应用开发再作为构建者实现）

### 技巧与治理
- `[ ]` Vibe Coding 技巧、CLI vs IDE 选择
- `[ ]` AI 生成代码的评审 / 测试 / 安全门禁（进主干前）

---

## 分支二 · AI 应用开发（把 AI 建进产品 · 我是"构建者"）

### 技术栈选型
- `[ ]` Spring AI 2.0（Spring 团队默认——ChatClient / Advisors / ETL / 评测 / MCP starter）
- `[ ]` LangChain4j
- `[ ]` 二者选型对比（见 [`java-stack.md`](./java-stack.md)）

### LLM 调用工程
- `[ ]` 流式（SSE） / 超时 / 重试 / 幂等
- `[ ]` 结构化输出（JSON Schema + Jackson）
- `[ ]` Function / Tool Calling（通往 Agent 的枢纽）

### 评测体系（持续工程，非一次性阶段）
- `[ ]` Golden Set 构建 → 自动打分 / LLM-as-Judge
- `[ ]` 线上灰度闭环

### RAG
- `[ ]` 文档解析 / 清洗 / Chunking
- `[ ]` 向量库选型 / 向量索引算法
- `[ ]` 检索 / 重排 / 引用 / 拒答
- `[ ]` 知识库更新流水线（增量 / 版本 / 去重 / 全量重建）← 后端真实活
- `[ ]` GraphRAG
- `[ ]` Agentic RAG（Agent 自主决定检索策略）

### Agent
- `[ ]` Agent Loop / Plan-and-Execute / Tool 注册
- `[ ]` 记忆系统（短期 / 长期 / 记忆演化）
- `[ ]` Workflow / Graph / Loop 编排范式
- `[ ]` 多 Agent（A2A）

### MCP（独立地基 · 连接 AI 与外部系统的事实标准）
- `[ ]` 核心原语：Tools / Resources / Prompts
- `[ ]` 传输：STDIO / SSE / Streamable-HTTP
- `[ ]` 写 MCP Server 暴露公司 Java 服务 ← 后端主场

### 系统设计
- `[ ]` LLM 网关（多模型路由 / fallback / 限流 / 成本）← 重点作品项目
- `[ ]` 可观测性（日志 / trace / metrics）
- `[ ]` 稳定性（限流 / 熔断 / 降级）
- `[ ]` 安全（脱敏 / 注入防护 / 权限边界）

---

## 怎么用这张图

1. 结合手头工作，挑一个能立刻用上的节点（不必从主干开始）
2. 学完在 `notes/` 对应目录（`foundations/` `ai-coding/` `app-dev/`）写一篇笔记
3. 把节点状态从 `[ ]` 更新为 `[~]` 或 `[x]`
4. 在 `progress-log.md` 记一行：工作任务 → 节点 → 笔记路径
