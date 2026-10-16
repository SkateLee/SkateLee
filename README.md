
<div align="center">

# Hi, I'm SkateLee 👋

### AI Agent Engineer | Backend Engineer

**Agent Harness · Context Engineering · Long-term Memory · Multi-Agent Systems**

🎓 东北师范大学（211）计算机技术硕士 · 2028 届

🚀 **正在寻找 AI Agent 开发实习机会｜可立即到岗｜可实习 6 个月以上**

[![GitHub](https://img.shields.io/badge/GitHub-SkateLee-181717?style=flat-square&logo=github)](https://github.com/SkateLee)
[![MultiCC](https://img.shields.io/badge/Project-MultiCC-6A5ACD?style=flat-square)](https://github.com/SkateLee/multiCC)
[![Blog](https://img.shields.io/badge/Blog-withsk8lee.top-0A66C2?style=flat-square)](https://www.withsk8lee.top)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:liliubing103@163.com)

</div>

---

## 👨‍💻 About Me

我是一名专注于 **AI Agent 系统研发与工程化落地** 的计算机技术硕士研究生。

相比于简单的 LLM API 调用和工作流编排，我更关注 **Agent 如何从一个能够调用工具的 Demo，演进为可靠、可恢复、可评测、具备长期记忆与持续进化能力的智能体系统**。

目前主要探索三个技术方向：

- **Agent Runtime & Harness**：Agent Loop、Tool Calling、工具权限控制、MCP、子 Agent、会话恢复与运行时治理。
- **Context Engineering & Memory**：上下文分层管理、自主记忆折叠、长期记忆检索、Prompt Cache 与长程任务状态维护。
- **Agent Self-Evolution & Evaluation**：反馈驱动的 Skills 自进化、Replay 评测、LLM-as-Judge、能力版本管理与可审计演化。

同时具备 Python / Java 后端基础，以及 FastAPI、asyncio、MySQL、Redis 等工程实践经验。

> **当前目标：AI Agent 开发实习 / Agent Runtime / LLM 应用工程方向**
>
> 希望参与 Agent 基础设施、智能体应用或 AI Coding Agent 的实际研发，重点关注 Agent 的可靠性、执行效率和工程化能力。

---

## 🌟 Featured Projects

### 01 · [MultiCC — 通用 Agent Harness 与 Skills 自进化平台](https://github.com/SkateLee/multiCC)

**参考 Claude Code 类架构，自主实现的 Python Agent Runtime，探索长期记忆与 Agent 能力自进化。**

`Python` `asyncio` `OpenAI/Anthropic SDK` `MCP` `Tool Calling` `Skills` `Docker`

**项目背景**

传统 Tool-Calling Agent 在执行长程任务时，容易受到上下文窗口限制、工具执行异常和历史经验无法复用等问题的影响。

MultiCC 围绕 **Agent Runtime、Context Management、Memory、Skills Evolution** 构建通用 Agent 执行框架，尝试让 Agent 不仅能够完成任务，还能够保存执行状态、复用历史经验并持续改进任务流程。

**核心设计与实现**

**① Agent Harness & Runtime**

- 自主实现 Agent Loop，统一编排模型推理、Tool Call 解析、权限检查、工具执行、结果回写和会话持久化。
- 支持 OpenAI / Anthropic 双协议、MCP 工具集成、Plan Mode、子 Agent 与会话恢复。
- 将工具执行安全与权限控制纳入运行时，降低文件与 Shell 操作风险。

**② Autonomous Memory Folding**

- 设计自主会话记忆折叠机制，将上下文压缩扩展为长程任务中的状态重组与策略重启能力。
- 通过 `episode_memory`、`working_memory`、`tool_memory` 分层保存任务进度、工作状态与工具经验。
- Agent 可通过 `compact_context` 主动折叠上下文，在上下文受限或工具反复失败时继续推进任务。

**③ Feedback-Driven Skills Evolution**

- 实现从用户反馈到可复用 Skills 的在线演化链路。
- 通过 Pending Window 捕获后续反馈，结合抽取器、维护器进行候选 Skills 提取。
- 支持相似检索、`add / merge / discard` 决策及 `SKILL.md` 持久化。
- 区分 Memory 中的项目事实、用户偏好与 Skills 中的可复用任务流程。

**④ Evaluation & Auditable Evolution**

- 构建基于 Replay、规则评测和 LLM-as-Judge 的 Skills 质量评测机制。
- 支持候选 Skills 试跑、版本对比、优胜版本登记及来源追踪。
- 探索 Agent 能力演化过程的可回放、可比较和可审计。

**📊 项目评测**

以 HiRA 为基线，在 GAIA / HLE 共 665 道任务上进行对比评测：

| Benchmark | Baseline | MultiCC | Improvement |
|:---|---:|---:|---:|
| GAIA Pass@1 | 42.1% | **53.3%** | **+11.2 pp** |
| HLE Pass@1 | 13.6% | **20.2%** | **+6.6 pp** |

**Ablation Study**

关闭自主会话记忆折叠机制后，GAIA Pass@1 从 **53.3% 下降至 44.7%**，说明该机制在当前评测设置下对长程任务推进具有积极作用。

**🔗 [查看源代码与运行文档 →](https://github.com/SkateLee/multiCC)**

---

### 02 · 跨境购物智能体 — Multi-Agent Shopping System

**面向多平台比价、个性化推荐与复杂购物决策的对话式 Agent 系统。**

`Python` `FastAPI` `LangGraph` `Milvus` `MySQL` `Redis` `BM25` `RRF` `LangFuse`

针对跨境购物场景中的复杂任务编排、上下文膨胀、长期记忆与工具执行不稳定等问题，设计并实现多智能体购物决策系统。

**核心工程实践**

**① Multi-Agent Orchestration**

- 采用 Supervisor-Workers 架构组织多个专业子 Agent。
- 基于任务类型和工具读写属性拆分职责，降低单 Agent 上下文负担。
- 复杂任务响应时间降低 **65%**。

**② Context & Runtime Reliability**

- 设计边界压缩策略，平衡 Token 消耗与 Prompt Cache 命中率。
- 10 轮以上对话的 Token 消耗降低 **30%**。
- 构建 LoopDetector、工具熔断和 Agent 主循环自恢复机制。
- 任务完成率由 **71% 提升至 89%**。

**③ Long-term Memory & Retrieval**

- 实现用户偏好、商品黑名单与历史选择的跨会话记忆。
- 设计记忆检索和删除机制，控制长期记忆持续膨胀。
- 基于 Embedding + BM25 + RRF + Reranker 实现混合检索。
- Top-100 商品召回相关率提升 **22%**，跨语言检索场景提升 **35%**。

**④ Observability & Real-time Interaction**

- 集成 LangFuse，对 Agent、Tool Calling、Token 消耗及响应耗时进行全链路追踪。
- Badcase 排查时间由 **30 分钟缩短至 5 分钟**。
- 基于 AG-UI 事件协议和 WebSocket 实现任务进度实时推送与多会话路由。

---

### 03 · [Globex Agent — 跨境电商选购 Agent](https://github.com/SkateLee/globex-agent)

**基于 AgentScope 2.x 的公开电商 Agent 工程实践。**

`AgentScope 2.x` `FastAPI` `AG-UI` `React` `Docker`

- 支持自然语言商品选购、工具调用和商品结果展示。
- 集成实时 Agent 交互、用户偏好与个人 Skills 管理。
- 围绕 Agent 执行、持久化、运行恢复和评测开展工程实践。
- 提供前后端代码、环境配置及本地运行文档。

**🔗 [查看 Globex Agent 项目 →](https://github.com/SkateLee/globex-agent)**

---

## 🛠️ Tech Stack

| Area | Technologies & Topics |
|:---|:---|
| **Languages** | Python · Java · SQL |
| **Backend** | FastAPI · asyncio · MySQL · Redis · WebSocket |
| **Agent Frameworks** | AgentScope 2.x · LangGraph · OpenAI / Anthropic SDK |
| **Agent Runtime** | Agent Loop · Tool Calling · MCP · Multi-Agent · Plan Mode |
| **Context & Memory** | Context Engineering · Prompt Cache · Memory Folding · Long-term Memory |
| **Skills & Evaluation** | Skills Evolution · Replay · LLM-as-Judge · GAIA · HLE |
| **Retrieval** | Milvus · Embedding · BM25 · RRF · Reranking |
| **Infrastructure** | Docker · Linux · Git · LangFuse |

**特别关注：**

`Agent Harness` `Agent Runtime` `Context Engineering` `Skills 自进化` `Agent Evaluation` `Multi-Agent Orchestration`

---

## 💼 Internship Experience

### 重庆美天科技有限公司 · 软件开发实习生

`2026.03 – 2026.07`

- 使用 Python 开发气象业务数据处理脚本，完成数据清洗、处理与批量任务执行。
- 参与业务系统故障排查、Bug 复现、异常定位与功能验证。
- 承担 5 个气象业务系统的日常巡检，积累真实业务场景下的工程实践经验。

---

## 🎓 Education

**东北师范大学（211）** · 计算机技术硕士  
`2025.09 – 2028.06` · 专业排名 **前 10%**

**广东海洋大学** · 软件工程本科  
`2021.09 – 2025.06` · 专业排名 **前 20%**

---

## 🏆 Awards & Certifications

- 🥈 第十七届蓝桥杯全国总决赛 Java 组二等奖
- 🥈 第 22 届百度之星程序设计大赛省赛银奖
- 🥉 2026 年码蹄杯本科组全国总决赛三等奖
- 🏅 第七届大学生算法设计与编程挑战赛金奖
- 📜 软件设计师（软考中级）
- 📚 CET-6 · 本科及研究生奖学金

---

## 📫 Contact

目前正在寻找 **AI Agent 开发工程师实习** 相关机会。

期待参与 Agent Runtime、AI Coding、Context Engineering、多智能体系统及 Agent 应用工程化方向的研发工作。

- **GitHub**: https://github.com/SkateLee
- **Blog**: https://www.withsk8lee.top
- **Email**: liliubing103@163.com

> Building reliable, stateful and continuously improving AI Agents. 🚀

