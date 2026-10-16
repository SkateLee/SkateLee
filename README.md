
<div align="center">

# Hi, I'm SkateLee 👋

### AI Agent Engineer · Backend Engineer

**Agent Harness · Context Engineering · Long-term Memory · Multi-Agent Systems**

🎓 东北师范大学（211）计算机技术硕士在读 · 2028 届

🚀 **Open to AI Agent Internships · 可立即到岗 · 可实习 6 个月以上**

[![GitHub](https://img.shields.io/badge/GitHub-SkateLee-181717?style=for-the-badge&logo=github)](https://github.com/SkateLee)
[![Blog](https://img.shields.io/badge/个人博客-withsk8lee.top-0A66C2?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.withsk8lee.top)
[![Email](https://img.shields.io/badge/Email-联系我-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:liliubing103@163.com)

</div>

---

## 👨‍💻 About Me

我是一名专注于 **AI Agent 系统设计与工程化落地** 的计算机技术硕士研究生。

相比于单纯的 Prompt Engineering 或 LLM API 调用，我更关注如何构建 **可靠、可恢复、可观测、具备长期记忆与持续进化能力的 Agent 系统**。

目前主要围绕以下方向进行探索与实践：

- 🤖 **Agent Runtime & Harness**：自主实现 Agent Loop、Tool Calling、MCP 工具集成、权限控制、子 Agent 调度与会话恢复。
- 🧠 **Context Engineering & Memory**：上下文压缩、自主记忆折叠、长期记忆管理、Prompt Cache 与长程任务状态维护。
- 🔄 **Skills Self-Evolution**：探索从用户反馈到 Skills 抽取、合并、持久化与质量评测的在线能力演化闭环。
- ⚙️ **Multi-Agent Engineering**：实践 Supervisor-Workers / Main-Sub Agent 架构，关注任务拆分、工具调用可靠性和执行效率。
- 📊 **Agent Evaluation & Observability**：实践 GAIA / HLE Benchmark、LLM-as-Judge、Replay、LangFuse 和全链路 Trace 分析。
- 💻 **Backend Engineering**：熟悉 Python、Java、FastAPI、asyncio、MySQL、Redis，具备实际业务系统开发与维护经验。

> **我关注的不只是 Agent 能否完成任务，更关注它如何在复杂、长程和不确定的环境中稳定地完成任务。**

---

## 🚀 Featured Projects

### 01 · MultiCC — 通用 Agent Harness 与 Skills 自进化平台

**Building a stateful, extensible and continuously improving AI Agent Runtime.**

[![Source Code](https://img.shields.io/badge/Source_Code-MultiCC-181717?style=flat-square&logo=github)](https://github.com/SkateLee/multiCC)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-Tool_Integration-444444?style=flat-square)
![Skills](https://img.shields.io/badge/Skills-Self_Evolution-6A5ACD?style=flat-square)

`Python` `asyncio` `OpenAI/Anthropic SDK` `MCP` `Tool Calling` `Skills` `Docker`

#### 📖 Overview

MultiCC 是一个参考 Claude Code 类架构、从零实现的 Python 通用 Agent Harness。

项目关注传统 LLM Agent 在长程任务中面临的 **上下文受限、工具执行安全、任务状态丢失、经验无法复用以及持续学习能力不足** 等问题。

围绕 Agent Runtime、Context Engineering、Memory 和 Skills Evolution 设计统一执行框架，使 Agent 能够在复杂任务中持续推进，并从执行反馈中沉淀可复用能力。

#### 🔧 Key Engineering Highlights

**1. Agent Harness — 统一运行时与工具编排**

- 自主实现 Agent Loop，统一处理模型推理、Tool Call 解析、权限检查、工具执行、结果回写与会话持久化。
- 支持 OpenAI / Anthropic 双协议、MCP 工具接入、Plan Mode、子 Agent 和会话恢复。
- 设计工具执行权限机制，对文件操作和 Shell 执行进行应用层控制。
- 支持上下文压缩与任务状态维护，提高长程任务执行的连续性。

**2. Autonomous Memory Folding — 自主记忆折叠**

- 设计主动式上下文折叠机制，将上下文压缩扩展为任务状态重组与策略重启能力。
- 基于 `episode_memory`、`working_memory`、`tool_memory` 分层保存任务进度、工作状态与工具经验。
- Agent 可通过 `compact_context` 主动重组执行上下文，在上下文压力、工具失败或策略变化时继续推进任务。

**3. Skills Self-Evolution — 反馈驱动的能力进化**

- 设计用户反馈驱动的 Skills 在线演化链路。
- 通过 Pending Window 捕获用户后续反馈，完成候选 Skills 的抽取与维护。
- 支持相似检索、`add / merge / discard` 决策及 `SKILL.md` 持久化。
- 采用 Memory + Skills 分层机制，区分项目事实、用户偏好和可复用任务流程。

**4. Evaluation & Auditing — 能力评测与演化审计**

- 实现基于 Replay、规则评测和 LLM-as-Judge 的 Skills 质量评测机制。
- 支持候选版本试跑、优胜版本登记、能力来源追踪与版本对比。
- 使 Skills 演化过程具备可回放、可比较和可审计能力。

#### 📊 Evaluation Results

项目阶段性评测以 HiRA 为基线，在 GAIA / HLE 共 665 道任务上进行对比：

| Benchmark | Baseline | MultiCC | Improvement |
|:---|---:|---:|---:|
| GAIA Pass@1 | 42.1% | **53.3%** | **+11.2 pp** |
| HLE Pass@1 | 13.6% | **20.2%** | **+6.6 pp** |

**Ablation Study**

关闭自主记忆折叠机制后，GAIA Pass@1 从 **53.3% 降至 44.7%**，体现了该机制在当前实验设置下对长程任务执行的积极作用。

> 以上为项目阶段性实验记录；公开仓库当前提供运行代码与测试，但尚未发布完整的可复现基准跑分数据及实验环境。

**🔗 [Explore MultiCC on GitHub →](https://github.com/SkateLee/multiCC)**

---

### 02 · Globex Agent — 跨境购物 Multi-Agent 系统

**An engineering-oriented shopping Agent with multi-agent orchestration, persistent memory and observable execution.**

[![Source Code](https://img.shields.io/badge/Source_Code-Globex_Agent-181717?style=flat-square&logo=github)](https://github.com/SkateLee/globex-agent)
![AgentScope](https://img.shields.io/badge/AgentScope-2.x-6A5ACD?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![AG-UI](https://img.shields.io/badge/AG--UI-Streaming-008080?style=flat-square)

`Python` `AgentScope 2.x` `FastAPI` `React` `AG-UI` `Qdrant` `Redis` `LangFuse` `Docker`

#### 📖 Overview

Globex Agent 是一个面向跨境购物场景的对话式智能体系统，支持自然语言商品检索、多商品比较、个性化偏好管理、交易确认以及 Agent 执行过程可视化。

项目围绕 **多 Agent 协作、上下文治理、长期记忆、混合检索、执行可靠性与可观测性** 展开工程设计。

当前公开版本基于 AgentScope 2.x 构建 MainAgent / SearchAgent / TradeAgent 架构，使用 FastAPI + AG-UI + React 实现前后端交互。

#### 🖥️ Demo Preview

<img src="https://github.com/user-attachments/assets/7851f1f8-7ea2-47fa-a614-eac015112060" alt="Globex Agent UI" width="700">

#### 🔧 Key Engineering Highlights

**1. Multi-Agent Orchestration — 多智能体任务编排**

- 设计主 Agent 与专业子 Agent 协作机制，对搜索、商品决策和交易能力进行职责划分。
- 当前公开版本通过 MainAgent 直接处理简单任务，并按需调度 SearchAgent / TradeAgent。
- 根据任务复杂度和工具属性进行任务拆分，控制多 Agent 上下文负担及协作开销。

**2. Context Engineering — 上下文分层治理**

- 设计上下文边界压缩策略，减少历史对话和工具返回带来的 Token 膨胀。
- 对工具结果进行分层保存，将完整证据与模型推理所需信息分离。
- 支持上下文整理、摘要和历史证据回查，兼顾任务连续性与信息完整性。
- 结合执行循环检测、重试、熔断等机制，提升复杂任务的执行可靠性。

**3. Long-term Memory & Skills — 长期记忆和用户偏好**

- 实现用户偏好、商品黑名单和历史选择的跨会话持久化。
- 基于语义检索按需召回长期记忆，避免将完整历史信息重复注入上下文。
- 支持记忆更新、删除和变更记录，敏感业务修改引入明确的用户确认。
- 支持用户个人 Skills 的 Markdown 编写、版本管理和按需加载。

**4. Hybrid Retrieval — 商品检索与召回优化**

- 构建商品语义检索、关键词检索和 Reranking 相关能力。
- 当前公开版本以 Embedding + Qdrant + Reranker 为主要检索链路。
- 实现 BM25 / RRF 混合检索能力，并提供可配置开关。
- 通过商品 ID 精确查询与业务约束过滤，提高商品结果的可控性。

**5. Observability & Real-time Interaction — 全链路可观测性**

- 通过 OpenTelemetry / LangFuse 支持模型、Agent、工具调用的 Trace 关联与分析。
- 基于 AG-UI 事件协议实现流式交互，展示任务进度、工具执行记录和结构化商品卡片。
- 设计会话持久化与事件恢复机制，支持刷新页面后恢复已保存的执行记录。
- 通过显式授权、幂等操作与事务约束保护订单和用户偏好变更。

#### 📈 Engineering Results

项目开发阶段记录的部分工程优化结果：

| Optimization | Recorded Result |
|:---|:---|
| 复杂任务响应耗时 | **降低 65%** |
| 10+ 轮对话 Token 消耗 | **降低 30%** |
| 任务完成率 | **71% → 89%** |
| Top-100 商品召回相关率 | **提升 22%** |
| Badcase 排查耗时 | **30 min → 5 min** |

> 上述指标来自项目开发阶段的测试记录，不代表当前公开版本的正式验收结果。当前版本的技术实现、测试状态与限制以仓库文档为准。

**🔗 [Explore Globex Agent on GitHub →](https://github.com/SkateLee/globex-agent)**

---

## 🛠️ Tech Stack

### 💻 Languages & Backend

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

`asyncio` · `SQLAlchemy` · `WebSocket` · `REST API` · `SQL`

### 🤖 AI Agent Engineering

![OpenAI](https://img.shields.io/badge/OpenAI_SDK-412991?style=flat-square&logo=openai&logoColor=white)
![AgentScope](https://img.shields.io/badge/AgentScope_2.x-6A5ACD?style=flat-square)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-444444?style=flat-square)
![AG-UI](https://img.shields.io/badge/AG--UI-008080?style=flat-square)

`Agent Loop` · `Tool Calling` · `Agent Harness` · `Multi-Agent` · `Skills` · `Context Engineering`

### 🔍 Retrieval, Evaluation & Infrastructure

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

`Milvus` · `Qdrant` · `BM25` · `RRF` · `Reranking` · `LangFuse` · `OpenTelemetry` · `LLM-as-Judge`

---

## 💼 Internship Experience

### 重庆美天科技有限公司 · 软件开发实习生

**2026.03 – 2026.07**

- **Python 自动化**：开发气象业务数据处理脚本，完成数据读取、清洗及批量处理。
- **系统调试**：参与故障排查、Bug 复现、异常定位和功能验证。
- **系统维护**：负责 5 个气象业务系统的运行巡检与状态检查，积累真实业务环境下的问题排查经验。

---

## 🎓 Education

**东北师范大学（211） · 计算机技术硕士**

`2025.09 – 2028.06` · 专业排名 **Top 10%**

**广东海洋大学 · 软件工程本科**

`2021.09 – 2025.06` · 专业排名 **Top 20%**

---

## 🏆 Awards & Certifications

- 🥈 **第十七届蓝桥杯全国总决赛 Java 组二等奖**
- 🥈 **第 22 届百度之星程序设计大赛省赛银奖**
- 🥉 **2026 年码蹄杯本科组全国总决赛三等奖**
- 🏅 第七届大学生算法设计与编程挑战赛金奖
- 📜 软件设计师（软考中级）
- 📚 大学英语六级（CET-6）
- 🎓 本科生学业奖学金及研究生奖学金

---

## 📫 Contact & Opportunities

<div align="center">

### 🚀 Open to AI Agent Engineering Internships

**AI Agent Development · Agent Runtime · AI Coding · Backend Engineering**

2028 届硕士在读 · 可立即到岗 · 可长期实习 6 个月以上

欢迎就 AI Agent 技术、开源项目与实习机会进行交流。

📧 **Email:** [liliubing103@163.com](mailto:liliubing103@163.com)

🌐 **Blog:** [www.withsk8lee.top](https://www.withsk8lee.top)

💻 **GitHub:** [github.com/SkateLee](https://github.com/SkateLee)

---

*Building reliable, stateful and continuously improving AI Agents.*

**Keep Building. Keep Learning. 🚀**

</div>
