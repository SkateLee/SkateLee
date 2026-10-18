 
<div align="center">

# 你好，我是 SkateLee 👋

### AI Agent 工程师 · 后端开发工程师

**Agent 运行框架 · 上下文工程 · 长期记忆 · 多智能体系统**

🎓 东北师范大学（211）计算机技术硕士在读 · 2028 届

🚀 **正在寻找 AI Agent 开发实习机会 · 可立即到岗 · 可实习 6 个月以上**

[![GitHub](https://img.shields.io/badge/GitHub-SkateLee-181717?style=for-the-badge&logo=github)](https://github.com/SkateLee)
[![个人博客](https://img.shields.io/badge/个人博客-withsk8lee.top-0A66C2?style=for-the-badge&logo=googlechrome&logoColor=white)](http://117.72.221.82/)
[![邮箱](https://img.shields.io/badge/邮箱-联系我-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:liliubing103@163.com)

</div>

---

## 👨‍💻 关于我

我是一名专注于 **AI Agent 系统设计与工程化落地** 的计算机技术硕士研究生。

相比于单纯的提示词工程或大模型 API 调用，我更关注如何构建 **可靠、可恢复、可观测、具备长期记忆与持续进化能力的 Agent 系统**。

目前主要围绕以下方向进行探索与实践：

- 🤖 **Agent 运行时与执行框架（Agent Runtime & Harness）**：自主实现 Agent 执行循环、工具调用、MCP 工具集成、权限控制、子 Agent 调度与会话恢复。
- 🧠 **上下文工程与记忆管理（Context Engineering & Memory）**：上下文压缩、自主记忆折叠、长期记忆管理、提示词缓存与长程任务状态维护。
- 🔄 **Skills 自进化**：探索从用户反馈到 Skills 抽取、合并、持久化与质量评测的在线能力演化闭环。
- ⚙️ **多智能体工程（Multi-Agent Engineering）**：实践监督者—工作者（Supervisor-Workers）与主从 Agent 架构，关注任务拆分、工具调用可靠性和执行效率。
- 📊 **Agent 评测与可观测性**：实践 GAIA / HLE 基准测试、LLM-as-Judge 自动评估、执行回放、LangFuse 和全链路追踪分析。
- 💻 **后端工程开发**：熟悉 Python、Java、FastAPI、asyncio、MySQL、Redis，具备实际业务系统开发与维护经验。

> **我关注的不只是 Agent 能否完成任务，更关注它如何在复杂、长程和不确定的环境中稳定地完成任务。**

---

## 🚀 精选项目

### 01 · MultiCC — 参考 Claude Code 架构的本地通用 Agent Harness

**从零构建可扩展、可持续运行、安全可控的本地 Agent Harness，支持复杂长程任务执行。**

[![源代码](https://img.shields.io/badge/源代码-MultiCC-181717?style=flat-square&logo=github)](https://github.com/SkateLee/multiCC)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-工具集成-444444?style=flat-square)
![Multi-Agent](https://img.shields.io/badge/Multi--Agent-并行编排-6A5ACD?style=flat-square)

`Python` `ReAct` `OpenAI/Anthropic SDK` `MCP` `Skills` `Multi-Agent` `Sandbox`

#### 📖 项目概述

MultiCC 参考 Claude Code 的架构设计与运行机制，从零设计并实现本地通用 Agent Harness。基于 **ReAct** 构建 Agent 执行循环，采用**五层分层架构**，集成多模型适配、MCP 工具扩展、Skills 动态加载、上下文管理、权限控制与多 Agent 协作能力，为 LLM 提供可扩展、可持续运行、安全可控的本地任务执行环境。

#### 👨‍💻 个人职责

- 独立负责 Agent Harness 的整体架构设计、核心机制选型与模块拆分，借助 Codex 辅助完成代码实现与调试，构建模型调用、工具执行、上下文管理与任务编排的完整运行链路。
- 设计跨会话记忆与上下文管理系统，实现 **JSONL 会话持久化、LLM 自动记忆提取及项目级指令文件分级加载**，支持长周期任务执行。
- 搭建 Agent 自动化评测体系，基于 **SWE-bench-Live** 验证代码任务执行能力，自主设计上下文信息保留测试，通过评测反馈持续优化执行策略。

#### 🔧 核心工程亮点

**1. MCP 工具延迟加载 — 提升工具生态扩展能力**

- 设计工具发现与按需加载机制，避免将全量工具 Schema 注入上下文。
- 百级工具场景下，**工具描述 Token 占用降低 85%**，提升上下文利用率。

**2. 两层渐进式上下文压缩 — 支撑长程任务**

- 设计两层渐进式上下文压缩策略，兼顾上下文窗口压力与任务关键信息保留。
- 支持 **8 小时以上连续 Agent 会话**，不丢失关键上下文。

**3. 五层安全执行机制 — 降低重复审批开销**

- 构建分层权限控制与工具执行确认机制，将单次会话权限弹窗由**平均 30 次降至 5 次以内**。
- 可选启用 OS 级沙箱作为额外安全保障，以内核级隔离支持 Agent 全自动模式下的安全执行。

**4. 多 Agent 并行编排 — 提升复杂任务效率**

- 设计多 Agent 任务拆分、并行执行与文件级隔离机制，缓解单 Agent 上下文和串行执行瓶颈。
- 跨文件重构任务耗时相比单 Agent **降低约 60%**。

**5. 评测驱动优化 — 通过测试发现上下文缺陷**

- 基于 **SWE-bench-Live** 搭建评测流水线，验证 Agent 的 Bug 定位与修复能力。
- 自主设计上下文信息保留测试，定位并修复压缩摘要模板缺陷，**信息保留率从 17% 提升至 100%**。

**🔗 [在 GitHub 查看 MultiCC 项目 →](https://github.com/SkateLee/multiCC)**

---

### 02 · FlowFusion — Workflow-Agent 混合架构的电商售后智能体系统

**以确定性 Workflow 保障业务流程，以 Agent 实现动态应答，兼顾售后自动化、检索质量与幻觉治理。**

[![项目仓库](https://img.shields.io/badge/GitHub-FlowFusion-181717?style=flat-square&logo=github)](https://github.com/SkateLee/FlowFusion)
![LangGraph](https://img.shields.io/badge/LangGraph-工作流编排-1C3C3C?style=flat-square)
![RAG](https://img.shields.io/badge/RAG-混合检索-4479A1?style=flat-square)
![Langfuse](https://img.shields.io/badge/Langfuse-评测与追踪-6A5ACD?style=flat-square)

`Python` `LangChain` `LangGraph` `RAG` `Milvus` `MCP` `Langfuse` `MySQL`

#### 📖 项目概述

FlowFusion 面向电商售后场景设计并实现智能客服系统，以 **确定性 Workflow 与 Agent 混合架构**为核心，通过 LangGraph 编排意图分流、RAG 混合检索、证据校验及智能应答，构建覆盖**九类业务意图**的客服处理链路，并结合可观测评测、数据飞轮及主题分类微调，实现知识库持续更新与售后问题自动化处理。

#### 👨‍💻 个人职责

- 独立负责智能客服系统整体架构设计、技术选型与核心模块拆分，借助 Codex 辅助完成代码实现与调试，构建确定性 Workflow 与 Agent 协同执行的售后客服链路。
- 设计基于 LangGraph 的对话主链路，编排意图分流、混合检索、生成前证据校验与 Agent 应答，实现流程控制与动态决策的职责分离。
- 搭建 RAG 检索、意图识别与置信度阈值评估体系，通过离线评测与错误案例分析，持续优化检索策略、Prompt 及 Agent 应答质量。

#### 🔧 核心工程亮点

**1. 混合检索与精排优化 — 提升证据召回质量**

- 基于 **BGE-M3** 语义向量与 **BM25** 关键词双路召回，结合 **RRF** 名次融合及 **BGE-Reranker** 精排。
- 在自建 300 题五桶评估集的 **240 道可作答题**上，**Recall@5 达 98%、MRR 达 89.4%、答案覆盖度 97%**；人工逐条核验的**幻觉率为 0.7%**。

**2. 四信号置信度与幻觉治理 — 防止错误售后承诺**

- 设计四信号加权置信度评分机制，在 Agent 应答前校验证据充分性。
- 对低置信度问题执行人工转接，避免证据不足时作出错误业务承诺；测试中**误放率 0%、误拦率 17%**。

**3. Workflow-Agent 混合编排 — 确保关键流程不被跳过**

- 基于 LangGraph 构建**九类意图到五个出口**的确定性分流状态机。
- 检索、订单查询和政策校验等必经步骤由 Workflow 统一调度，Agent 仅在证据齐备后负责动态判断与应答。

**4. 分层上下文治理 — 改善长对话信息保留**

- 设计三层上下文管理机制，结合异步分段摘要与工具结果裁剪，减少长对话上下文冗余。
- **长对话关键信息保留率提升 50%**。

**5. 数据飞轮与知识自迭代 — 持续补齐知识缺口**

- 设计三入口数据飞轮，将线上未解决问题、低置信度应答及人工反馈沉淀为待处理样本。
- 经人工审核后增量更新知识库，持续提升售后知识的完备性。

**🔗 [在 GitHub 查看 FlowFusion 项目 →](https://github.com/SkateLee/FlowFusion)**

---

## 🛠️ 技术栈

### 💻 编程语言与后端开发

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

`asyncio` · `SQLAlchemy` · `WebSocket` · `REST API` · `SQL`

### 🤖 AI Agent 工程开发

![OpenAI](https://img.shields.io/badge/OpenAI_SDK-412991?style=flat-square&logo=openai&logoColor=white)
![AgentScope](https://img.shields.io/badge/AgentScope_2.x-6A5ACD?style=flat-square)
![LangGraph](https://img.shields.io/badge/LangGraph-1C3C3C?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-444444?style=flat-square)
![AG-UI](https://img.shields.io/badge/AG--UI-008080?style=flat-square)

`Agent Loop` · `Tool Calling` · `Agent Harness` · `Multi-Agent` · `Skills` · `Context Engineering`

### 🔍 检索、评测与基础设施

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

`Milvus` · `Qdrant` · `BM25` · `RRF` · `Reranking` · `LangFuse` · `OpenTelemetry` · `LLM-as-Judge`

---

## 💼 实习经历

### 重庆美天科技有限公司 · 软件开发实习生

**2026.03 – 2026.07**

- **Python 自动化开发**：开发气象业务数据处理脚本，完成数据读取、清洗及批量处理。
- **系统调试与故障排查**：参与故障排查、Bug 复现、异常定位和功能验证。
- **业务系统维护**：负责 5 个气象业务系统的运行巡检与状态检查，积累真实业务环境下的问题排查经验。

---

## 🎓 教育背景

**东北师范大学（211） · 计算机技术硕士**

`2025.09 – 2028.06` · 专业排名 **前 10%**

**广东海洋大学 · 软件工程本科**

`2021.09 – 2025.06` · 专业排名 **前 20%**

---

## 🏆 竞赛获奖与资格证书

- 🥈 **第十七届蓝桥杯全国总决赛 Java 组二等奖**
- 🥈 **第 22 届百度之星程序设计大赛省赛银奖**
- 🥉 **2026 年码蹄杯本科组全国总决赛三等奖**
- 🏅 第七届大学生算法设计与编程挑战赛金奖
- 📜 软件设计师（软考中级）
- 📚 大学英语六级（CET-6）
- 🎓 本科生学业奖学金及研究生奖学金

---

## 📫 联系方式与实习机会

<div align="center">

### 🚀 正在寻找 AI Agent 工程开发实习机会

**AI Agent 开发 · Agent 运行时 · AI 编程智能体 · 后端工程开发**

2028 届硕士在读 · 可立即到岗 · 可长期实习 6 个月以上

欢迎就 AI Agent 技术、开源项目与实习机会进行交流。

📧 **邮箱：** [liliubing103@163.com](mailto:liliubing103@163.com)

🌐 **个人博客：** [www.withsk8lee.top](https://www.withsk8lee.top)

💻 **GitHub：** [github.com/SkateLee](https://github.com/SkateLee)

---

*致力于构建可靠、有状态、可持续进化的 AI Agent 系统。*

**持续构建，持续学习。🚀**

</div>
