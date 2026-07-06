# Java Stack Recommendation

## 必选（Java-first）
- JDK: `Java 21`（至少 Java 17）
- Framework: `Spring Boot 3`
- Build: `Maven`
- HTTP Client: `Spring WebClient`
- JSON: `Jackson`
- Test: `JUnit 5`

## AI 框架选型：Spring AI 2.0 vs LangChain4j

> 两者都覆盖 LLM 调用 / RAG / Agent / Tool Calling / 记忆 / 结构化输出 / MCP。
> 对 Spring Boot 团队，**默认 Spring AI**——它更"原生"；LangChain4j 在非 Spring 生态或需要某些特定抽象时再选。

| 维度 | Spring AI 2.0（GA） | LangChain4j |
|------|--------------------|-------------|
| 定位 | Spring 官方，Spring 生态原生 | 独立框架，跨 Quarkus/Spring Boot/Helidon |
| 调用 API | `ChatClient`（类 `WebClient` 的流式 API） | 统一 `ChatModel` API |
| 复用模式 | `Advisors`（把 RAG/记忆封装成可复用拦截器） | Chain / AiServices |
| RAG | 内置 ETL 文档摄取 + 20+ 向量库 | RAG 模块 + 多向量库 |
| MCP | 一等公民：client/server starter，STDIO/SSE/Streamable-HTTP | 支持 |
| 评测 | 内置评测工具（含 LLM-as-Judge、幻觉检测） | output parsing 为主 |
| 上手 | Spring Boot 自动配置 / starter，DI 风格熟悉 | 轻量，非 Spring 也能用 |

**建议**：本仓库以 Spring AI 2.0 为主线做实战；在选型笔记里对同一个需求各写一版对比，形成自己的判断。

## AI 组件（按需）
- 向量库：`pgvector` / `Milvus`（按公司环境选）
- 可观测：`Micrometer` + `Prometheus` + `Grafana`
- 可靠性：`Resilience4j`（超时/重试/熔断/限流）

## 工程治理
- 日志：`Logback` + traceId
- 安全：密钥管理、脱敏、权限边界

## 选型原则
- 先直接 API，再引入框架抽象
- 先单体可运行，再拆分模块
- 先指标可见，再做性能优化
