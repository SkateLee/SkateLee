 
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

### 01 · MultiCC — 通用 Agent 运行框架与 Skills 自进化平台

**构建具备状态管理、灵活扩展与持续进化能力的通用 AI Agent 运行框架。**

[![源代码](https://img.shields.io/badge/源代码-MultiCC-181717?style=flat-square&logo=github)](https://github.com/SkateLee/multiCC)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-工具集成-444444?style=flat-square)
![Skills](https://img.shields.io/badge/Skills-自进化-6A5ACD?style=flat-square)

`Python` `asyncio` `OpenAI/Anthropic SDK` `MCP` `Tool Calling` `Skills` `Docker`

#### 📖 项目概述

MultiCC 是一个参考 Claude Code 类架构、从零实现的 Python 通用 Agent 运行框架（Agent Harness）。

项目关注传统大模型 Agent 在长程任务中面临的 **上下文受限、工具执行安全、任务状态丢失、经验无法复用以及持续学习能力不足** 等问题。

围绕 Agent 运行时、上下文工程、记忆管理和 Skills 进化设计统一执行框架，使 Agent 能够在复杂任务中持续推进，并从执行反馈中沉淀可复用能力。

#### 🔧 核心工程亮点

**1. Agent 运行框架 — 统一运行时与工具编排**

- 自主实现 Agent 执行循环，统一处理模型推理、工具调用解析、权限检查、工具执行、结果回写与会话持久化。
- 支持 OpenAI / Anthropic 双协议、MCP 工具接入、规划模式（Plan Mode）、子 Agent 和会话恢复。
- 设计工具执行权限机制，对文件操作和 Shell 命令执行进行应用层控制。
- 支持上下文压缩与任务状态维护，提高长程任务执行的连续性。

**2. 自主记忆折叠（Autonomous Memory Folding）**

- 设计主动式上下文折叠机制，将上下文压缩扩展为任务状态重组与策略重启能力。
- 基于 `episode_memory`、`working_memory`、`tool_memory` 分层保存任务进度、工作状态与工具经验。
- Agent 可通过 `compact_context` 主动重组执行上下文，在上下文压力、工具失败或策略变化时继续推进任务。

**3. Skills 自进化 — 反馈驱动的能力演化**

- 设计用户反馈驱动的 Skills 在线演化链路。
- 通过待处理反馈窗口（Pending Window）捕获用户后续反馈，完成候选 Skills 的抽取与维护。
- 支持相似检索、`add / merge / discard` 决策及 `SKILL.md` 持久化。
- 采用 Memory + Skills 分层机制，区分项目事实、用户偏好和可复用任务流程。

**4. 能力评测与演化审计**

- 实现基于执行回放（Replay）、规则评测和 LLM-as-Judge 的 Skills 质量评测机制。
- 支持候选版本试运行、优胜版本登记、能力来源追踪与版本对比。
- 使 Skills 演化过程具备可回放、可比较和可审计能力。

#### 📊 阶段性评测结果

项目阶段性评测以 HiRA 为基线，在 GAIA / HLE 共 665 道任务上进行对比：

| 评测基准 | 基线（HiRA） | MultiCC | 提升幅度 |
|:---|---:|---:|---:|
| GAIA Pass@1 | 42.1% | **53.3%** | **+11.2 个百分点** |
| HLE Pass@1 | 13.6% | **20.2%** | **+6.6 个百分点** |

**消融实验**

关闭自主记忆折叠机制后，GAIA Pass@1 从 **53.3% 降至 44.7%**，体现了该机制在当前实验设置下对长程任务执行的积极作用。

> 以上为项目阶段性实验记录；公开仓库当前提供运行代码与测试，但尚未发布完整的可复现基准跑分数据及实验环境。

**🔗 [在 GitHub 查看 MultiCC 项目 →](https://github.com/SkateLee/multiCC)**

---

### 02 · Globex Agent — 跨境购物多智能体系统

**面向跨境购物场景，构建集多智能体协作、持久化记忆与执行过程可观测性于一体的智能体应用系统。**

[![源代码](https://img.shields.io/badge/源代码-Globex_Agent-181717?style=flat-square&logo=github)](https://github.com/SkateLee/globex-agent)
![AgentScope](https://img.shields.io/badge/AgentScope-2.x-6A5ACD?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![AG-UI](https://img.shields.io/badge/AG--UI-流式交互-008080?style=flat-square)

`Python` `AgentScope 2.x` `FastAPI` `React` `AG-UI` `Qdrant` `Redis` `LangFuse` `Docker`

#### 📖 项目概述

Globex Agent 是一个面向跨境购物场景的对话式智能体系统，支持自然语言商品检索、多商品比较、个性化偏好管理、交易确认以及 Agent 执行过程可视化。

项目围绕 **多 Agent 协作、上下文治理、长期记忆、混合检索、执行可靠性与可观测性** 展开工程设计。

当前公开版本基于 AgentScope 2.x 构建主 Agent（MainAgent）、搜索 Agent（SearchAgent）与交易 Agent（TradeAgent）架构，使用 FastAPI + AG-UI + React 实现前后端交互。

#### 🖥️ 系统演示

<img src="https://github.com/user-attachments/assets/7851f1f8-7ea2-47fa-a614-eac015112060" alt="Globex Agent 系统界面" width="700">

#### 🔧 核心工程亮点

**1. 多智能体任务编排（Multi-Agent Orchestration）**

- 设计主 Agent 与专业子 Agent 协作机制，对搜索、商品决策和交易能力进行职责划分。
- 当前公开版本通过 MainAgent 直接处理简单任务，并按需调度 SearchAgent / TradeAgent。
- 根据任务复杂度和工具属性进行任务拆分，控制多 Agent 上下文负担及协作开销。

**2. 上下文工程 — 分层治理与执行恢复**

- 设计上下文边界压缩策略，减少历史对话和工具返回带来的 Token 膨胀。
- 对工具结果进行分层保存，将完整证据与模型推理所需信息分离。
- 支持上下文整理、摘要和历史证据回查，兼顾任务连续性与信息完整性。
- 结合执行循环检测、重试、熔断等机制，提升复杂任务的执行可靠性。

**3. 长期记忆与 Skills 管理**

- 实现用户偏好、商品黑名单和历史选择的跨会话持久化。
- 基于语义检索按需召回长期记忆，避免将完整历史信息重复注入上下文。
- 支持记忆更新、删除和变更记录，敏感业务修改引入明确的用户确认。
- 支持用户个人 Skills 的 Markdown 编写、版本管理和按需加载。

**4. 混合检索 — 商品召回与排序优化**

- 构建商品语义检索、关键词检索和重排序（Reranking）相关能力。
- 当前公开版本以 Embedding + Qdrant + Reranker 为主要检索链路。
- 实现 BM25 / RRF 混合检索能力，并提供可配置开关。
- 通过商品 ID 精确查询与业务约束过滤，提高商品结果的可控性。

**5. 可观测性与实时交互**

- 通过 OpenTelemetry / LangFuse 支持模型、Agent、工具调用的全链路追踪关联与分析。
- 基于 AG-UI 事件协议实现流式交互，展示任务进度、工具执行记录和结构化商品卡片。
- 设计会话持久化与事件恢复机制，支持刷新页面后恢复已保存的执行记录。
- 通过显式授权、幂等操作与事务约束保护订单和用户偏好变更。

#### 📈 阶段性工程优化效果

项目开发阶段记录的部分工程优化结果：

| 优化项目 | 阶段性测试结果 |
|:---|:---|
| 复杂任务响应耗时 | **降低 65%** |
| 10+ 轮对话 Token 消耗 | **降低 30%** |
| 任务完成率 | **71% → 89%** |
| Top-100 商品召回相关率 | **提升 22%** |
| 不良案例（Badcase）排查耗时 | **30 分钟 → 5 分钟** |

> 上述指标来自项目开发阶段的测试记录，不代表当前公开版本的正式验收结果。当前版本的技术实现、测试状态与限制以仓库文档为准。

**🔗 [在 GitHub 查看 Globex Agent 项目 →](https://github.com/SkateLee/globex-agent)**

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
