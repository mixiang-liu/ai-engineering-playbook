# 精选学习资料

> 精选而非罗列——每条都注明「解决什么问题」。学完在对应笔记里留链接。
> 官方文档是一手资料，优先看官方。

## 认知基础（先建立直觉）
- **官方文档优先**：调 API 前先读所用模型 provider 的官方文档（概念+参数最权威）
- 主题清单（按需检索学习，不必全看）：
  - Tokenization 可视化：直观看到文本如何被切成 token
  - Embedding 与向量检索：理解语义相似度
  - Transformer / Attention 科普：工作级理解即可，不必推导公式
  - 幻觉成因：为什么概率生成会「一本正经胡说」

## Prompt 工程
- 各大 provider 官方的 Prompt Engineering 指南（最实用、随模型更新）
- 结构化输出 / Function Calling 的官方规范

## RAG
- RAG 原始论文（了解出发点即可，工程实践看框架文档）
- LangChain4j 官方文档：Java 生态的 RAG/Agent 抽象
- 向量库文档：`pgvector` / `Milvus`（按公司环境选）

## Agent
- ReAct 论文：理解「推理+行动」范式
- 各 provider 的 Tool Use / Agent 文档

## Java + LLM 工程
- Spring Boot 3 官方文档（WebClient 流式、配置、测试）
- Micrometer + Prometheus + Grafana：可观测性
- Resilience4j：超时/重试/熔断/限流

## 使用约定
- 看完一份资料 → 在 `notes/` 对应目录写一篇笔记（用 `_template.md`）
- 笔记里回链到本文件的具体条目
- 发现好资料 → 补进对应分类，注明「解决什么问题」
