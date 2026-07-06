# AI 术语表（中英对照）

> 系统学习强依赖术语的精确理解。遇到新词先查这里，缺的补进来。
> 排序对齐 `learning-roadmap.md`：认知基础 → 同心圆 → Prompt/评测 → RAG → Agent → MCP → AI Coding → 工程治理 → 框架。

## 认知基础
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| Token | 词元 | 模型处理文本的最小计量单位，不等于字/词 |
| Tokenization | 分词 | 把文本切成 token 的过程；中文、代码通常更耗 token |
| Context Window | 上下文窗口 | 单次请求「输入+输出」的总 token 上限 |
| Embedding | 向量嵌入 | 把文本映射为向量，用于语义相似度比较 |
| Cosine Similarity | 余弦相似度 | 衡量两个向量方向接近程度，RAG 检索的核心度量 |
| Transformer | — | 现代 LLM 的底层架构 |
| Attention | 注意力机制 | 让模型在生成时「关注」输入中相关部分 |
| Pre-training | 预训练 | 在海量语料上学习通用能力 |
| Fine-tuning (SFT) | 监督微调 | 用特定数据调整模型行为 |
| RLHF / DPO | 人类反馈对齐 | 让模型输出更符合人类偏好 |
| Hallucination | 幻觉 | 模型生成看似合理但事实错误的内容 |
| Temperature | 温度 | 控制输出随机性；越高越发散 |
| Top-p (Nucleus) | 核采样 | 从累积概率 p 的候选集中采样 |
| Max Output Tokens | 最大输出 token | 限制单次回答长度，防截断/控成本 |
| Reasoning Model | 推理模型 | 生成前先"思考"的模型（如 o 系列、DeepSeek-R1），复杂任务更准但更慢更贵 |
| Multimodal | 多模态 | 模型可接收/输出多种模态（文本+图像+音频），现已是默认能力而非特例 |

## X-Engineering 同心圆
> 这些 `X-Engineering` 是同心圆关系（作用范围逐层放大），不是并列。
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| Prompt Engineering | 提示词工程 | 打磨**一条指令**的措辞，同心圆最内层 |
| Context Engineering | 上下文工程 | 管理**单次调用**喂进窗口的全部信息（含预算/压缩/检索注入） |
| Loop Engineering | 循环工程 | 设计一次调用如何变成**多步循环**（观察→行动→反馈、终止、重试） |
| Harness Engineering | — | 工程**包裹模型的整个运行时**（loop+工具+记忆+护栏+监控+评测） |
| Agent Harness | 智能体运行时 | Harness 的具体形态；Claude Code 本身就是一个 harness |

## Prompt 与评测
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| System Prompt | 系统提示词 | 设定模型角色与全局约束 |
| Few-shot | 少样本示例 | 在提示词里给几个示例引导输出格式 |
| Chain-of-Thought (CoT) | 思维链 | 引导模型分步推理，提升复杂任务准确率 |
| Structured Output | 结构化输出 | 强制输出 JSON 等可解析格式 |
| Grounding | 事实锚定 | 让回答基于给定材料，减少幻觉 |
| Eval / Evaluation | 评测 | 用样本+标准量化输出质量 |
| Golden Set | 黄金样本集 | 人工确认过的标准答案集，作为评测基准 |
| LLM-as-Judge | 模型当裁判 | 用一个 LLM 给另一个 LLM 的输出打分 |
| Canary / Online Eval | 灰度 / 线上评测 | 新版本先放小流量+持续打分，把评测做成上线闭环而非一次性 |

## RAG
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| RAG | 检索增强生成 | 先检索相关材料再让模型基于材料回答 |
| Chunking | 分块 | 把长文档切成适合检索的片段 |
| Vector Store | 向量库 | 存储 embedding 并支持相似度检索 |
| Top-k Retrieval | Top-k 检索 | 取相似度最高的 k 个片段 |
| Rerank | 重排 | 对初检结果二次排序，提升相关性 |
| Citation | 引用 | 回答中标注信息来源片段 |
| Abstention | 拒答 | 材料不足时明确说「不知道」而非编造 |
| ANN Index | 近似最近邻索引 | 向量库高效检索的底层算法（如 HNSW/IVF），决定召回速度与精度 |
| Ingestion Pipeline | 知识库更新流水线 | 文档增量更新/版本/去重/全量重建的工程链路——后端真实活 |
| GraphRAG | 图谱增强检索 | 用知识图谱组织材料，支持多跳、全局性问题的检索 |
| Agentic RAG | 智能体式 RAG | 由 Agent 自主决定要不要检索、检索几轮、如何改写 query |

## Agent
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| Agent | 智能体 | 能自主调用工具、多步完成任务的 LLM 系统 |
| Tool / Function Calling | 工具调用 | 模型决定调用外部函数并使用其结果 |
| Orchestration | 任务编排 | 协调多步/多工具的执行流程 |
| ReAct | 推理-行动 | 交替「思考」与「调用工具」的经典 Agent 范式 |
| State Management | 状态管理 | 跨多步维护任务上下文与中间结果 |
| Agent Loop | 智能体循环 | 感知→决策→行动→观察的反复循环，Agent 的运行核心 |
| Plan-and-Execute | 先规划后执行 | 先拆出计划再逐步执行的 Agent 范式，对复杂任务更稳 |
| Memory (Short/Long-term) | 记忆系统 | 短期（本轮上下文）+ 长期（跨会话）+ 记忆演化，让 Agent 有状态 |
| Workflow / Graph / Loop | 编排范式 | 三种 Agent 编排结构：固定流程 / 有向图 / 自主循环 |
| Multi-Agent (A2A) | 多智能体 | 多个 Agent 分工协作（Agent-to-Agent 通信） |
| Skills | 技能 | 可复用的能力封装，Agent 按需加载调用 |

## MCP
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| MCP (Model Context Protocol) | 模型上下文协议 | 连接 AI 与外部系统的开放标准，"AI 界的 USB-C" |
| MCP Server | MCP 服务端 | 把数据/工具暴露给 AI 的一端——把公司 Java 服务包成 Server 是后端主场 |
| MCP Client | MCP 客户端 | 消费 MCP Server 能力的一端（如 Claude、IDE） |
| Resources / Tools / Prompts | 资源 / 工具 / 提示词 | MCP 三大核心原语：可读数据 / 可调函数 / 可复用提示 |
| Transport (STDIO/SSE/HTTP) | 传输层 | MCP 通信方式：本地进程 / 服务端推送 / 流式 HTTP |

## AI Coding
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| AI Coding | AI 编程 | 用 AI 工具辅助/生成代码，见效最快的提效方向 |
| Spec-Driven Coding | 规范驱动编程 | 先写规格再让 AI 生成，团队级主流工作流 |
| Vibe Coding | — | 凭感觉与 AI 快速迭代的轻量编程方式 |
| Subagents | 子智能体 | 把大任务拆给多个 AI 会话并行推进 |
| CLAUDE.md / AGENTS.md | — | 给编码 Agent 的项目级上下文/约定文件 |

## 工程治理
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| Streaming (SSE) | 流式输出 | 边生成边返回，降低首字延迟 |
| Idempotency | 幂等 | 同一请求重复执行结果一致 |
| Backoff | 退避重试 | 失败后按指数间隔重试 |
| Rate Limiting | 限流 | 控制请求速率，防止过载/超配额 |
| Circuit Breaker | 熔断 | 依赖故障时快速失败并降级 |
| Observability | 可观测性 | 日志 + trace + metrics 三支柱 |
| Token Budget | Token 预算 | 为请求设定 token 上限以控成本 |
| Model Routing | 模型路由 | 按任务难度分流到不同大小的模型 |
| LLM Gateway | 大模型网关 | 统一入口做多模型路由/fallback/限流/成本——很适合后端做成作品项目 |
| Prompt Injection | 提示词注入 | 恶意输入劫持模型指令的攻击，需在边界防护 |

## 框架（Java）
| 英文 | 中文 | 一句话理解 |
|------|------|-----------|
| Spring AI | — | Spring 官方 AI 框架（2.0 GA），Spring 团队默认选型 |
| LangChain4j | — | 独立的 Java LLM 框架，跨 Quarkus/Spring/Helidon |
| ChatClient | — | Spring AI 类 `WebClient` 的流式调用 API |
| Advisors | 顾问 | Spring AI 把 RAG/记忆封装成可复用拦截器的机制 |
| ETL Pipeline | 文档摄取管道 | Spring AI 内置的"加载→转换→写入向量库"流程 |
