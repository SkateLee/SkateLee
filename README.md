
<div align="center">

# Hi，我是 SkateLee 👋

### AI Agent 开发工程师 | 后端开发工程师

**Agentic AI · Agent Harness · 上下文工程 · 多智能体系统**

🎓 东北师范大学（211）计算机技术硕士在读

[![GitHub](https://img.shields.io/badge/GitHub-SkateLee-181717?style=for-the-badge&logo=github)](https://github.com/SkateLee)
[![个人博客](https://img.shields.io/badge/个人博客-访问网站-0A66C2?style=for-the-badge&logo=googlechrome&logoColor=white)](https://www.withsk8lee.top)
[![邮箱](https://img.shields.io/badge/Email-联系我-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:liliubing103@163.com)

![GitHub followers](https://img.shields.io/github/followers/SkateLee?style=flat-square&logo=github)
![Profile Views](https://komarev.com/ghpvc/?username=SkateLee&style=flat-square&color=blueviolet)

</div>

---

## 🚀 关于我

- 🎓 东北师范大学（211）计算机技术硕士在读，专业排名 **前 10%**；本科毕业于广东海洋大学软件工程专业
- 🤖 专注于 **AI Agent 系统设计与工程化落地**，关注从 Agent 原型到可靠智能体系统的完整技术链路
- 🧠 深入探索 **Agent Harness、Context Engineering、Long-term Memory、Skills 自进化** 等核心技术
- ⚙️ 具备从零构建 Agent Runtime、Tool Calling、MCP 工具集成、多 Agent 协作及工具安全执行机制的实践经验
- 📊 关注 Agent 的可靠性、可观测性与评测体系，具备 GAIA / HLE Benchmark、LLM-as-Judge 等评测实践经验
- 💻 熟悉 Python / Java 后端开发，以及 FastAPI、asyncio、MySQL、Redis 等技术
- 🌱 正在寻找 **AI Agent 开发 / 后端开发相关实习机会**，可长期实习 6 个月以上

> 💡 致力于构建可靠、具备长期记忆与持续进化能力的 AI Agent 系统。

---

## 🧰 技术栈

### 💻 编程语言与后端开发

![Python](https://img.shields.io/badge/-Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/-Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![FastAPI](https://img.shields.io/badge/-FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![MySQL](https://img.shields.io/badge/-MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/-Redis-DC382D?style=flat-square&logo=redis&logoColor=white)

### 🤖 AI Agent 与大模型应用

![OpenAI](https://img.shields.io/badge/-OpenAI_SDK-412991?style=flat-square&logo=openai&logoColor=white)
![LangGraph](https://img.shields.io/badge/-LangGraph-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![AgentScope](https://img.shields.io/badge/-AgentScope_2.0-6A5ACD?style=flat-square)
![MCP](https://img.shields.io/badge/-MCP-444444?style=flat-square)
![Multi-Agent](https://img.shields.io/badge/-Multi--Agent-8A2BE2?style=flat-square)
![Tool Calling](https://img.shields.io/badge/-Tool_Calling-008080?style=flat-square)

**核心技术方向：**

`Agent Harness` · `AgentLoop` · `Context Engineering` · `长期记忆` · `Skills 自进化` · `多智能体协作` · `Agent 评测`

### 🔍 检索增强与工程基础设施

![Milvus](https://img.shields.io/badge/-Milvus-00A1EA?style=flat-square)
![Docker](https://img.shields.io/badge/-Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Linux](https://img.shields.io/badge/-Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/-Git-F05032?style=flat-square&logo=git&logoColor=white)

`BM25` · `混合检索` · `RRF` · `Reranking` · `LangFuse` · `WebSocket` · `asyncio`

---

## 📌 精选项目

### 🤖 MultiCC — 具备 Skills 自进化能力的通用 Agent 平台

**参考 Claude Code 架构设计，从零实现的通用 Agent Harness**

`Python` `asyncio` `OpenAI/Anthropic SDK` `MCP` `Tool Calling` `Skills` `Docker`

#### 📖 项目介绍

MultiCC 是一个面向本地任务执行的通用 Agent 平台，旨在解决传统大模型 Agent 在长程任务执行过程中面临的 **上下文受限、工具执行安全、任务经验无法复用及持续学习能力不足** 等问题。

不同于简单组合 LLM 与工具调用的 Agent 应用，MultiCC 更关注 Agent Runtime 的统一编排、长程任务状态管理、长期记忆和能力自进化。

#### 🔧 核心技术实现

**1. Agent Harness 核心框架与统一编排**

- 从零实现 Agentic Harness，统一编排模型推理、Tool Calling、权限检查、工具执行及结果回写
- 支持 OpenAI / Anthropic 双协议、MCP、Plan Mode、子 Agent 及会话恢复
- 实现上下文压缩与长程任务执行状态管理

**2. 自主记忆折叠与长程任务状态管理**

- 设计自主会话记忆折叠机制，将其作为长程任务中的状态重组和策略重启能力，而非简单的上下文压缩
- 通过 `episode_memory`、`working_memory`、`tool_memory` 保存任务进度、当前工作状态及历史工具经验
- 支持 Agent 在上下文受限、工具调用失败或策略变化时，通过 `compact_context` 主动折叠上下文并继续执行任务

**3. 基于反馈驱动的 Skills 在线自进化**

- 实现从用户反馈到可复用 Skills 的在线自进化链路
- 基于 Pending Window 捕获用户后续反馈，通过抽取器与维护器完成候选 Skills 提取
- 支持候选 Skills 相似检索、`add / merge / discard` 决策及 `SKILL.md` 持久化
- 实现 Memory + Skills 分层长期上下文管理，区分项目事实、用户偏好与可复用任务流程

**4. Skills 质量评测与可审计演化**

- 构建基于 Replay、规则评测、LLM-as-Judge 的 Skills 自进化质量评测机制
- 支持候选版本试跑、优胜版本登记及来源追踪
- 实现 Skills 能力演化过程的可回放、可比较与可审计

#### 📊 核心评测结果

以 HiRA 为基线，在 GAIA / HLE 共 **665 道任务**上完成评测：

| 评测基准 | 基线 | MultiCC | 绝对提升 |
|:---:|:---:|:---:|:---:|
| GAIA Pass@1 | 42.1% | **53.3%** | +11.2 个百分点 |
| HLE Pass@1 | 13.6% | **20.2%** | +6.6 个百分点 |

**消融实验：**

关闭自主会话记忆折叠机制后，GAIA Pass@1 从 **53.3% 下降至 44.7%**，验证了该机制对长程任务持续推进的重要作用。

---

### 🛒 跨境购物智能体 — 基于 Multi-Agent 的智能购物系统

**面向多平台比价、个性化推荐及复杂购物决策的对话式 Agent 系统**

`Python` `FastAPI` `LangGraph` `Milvus` `MySQL` `Redis` `BM25` `RRF` `LangFuse`

#### 📖 项目介绍

面向跨境购物场景，设计并实现支持 **多平台商品比价、个性化偏好管理、智能商品检索及长链路购物决策** 的对话式 Agent 系统。

重点解决 Agent 在实际业务中面临的多 Agent 编排、上下文膨胀、工具执行不稳定、长期记忆管理和全链路可观测性等工程问题。

#### 🔧 核心技术实现

**1. Supervisor-Workers 多 Agent 架构**

- 采用 Supervisor-Workers 架构实现多智能体协同工作
- 根据工具及任务读写属性划分子 Agent，减少单 Agent 上下文负担
- 优化复杂任务执行流程，任务响应时间降低 **65%**

**2. 上下文压缩与 Agent Harness 工程**

- 设计边界压缩策略，平衡 Token 消耗和 Prompt Cache 命中率
- 在 10 轮以上的长对话场景中，Token 消耗降低 **30%**
- 实现 LoopDetector 滑动窗口循环检测、工具熔断及主循环自恢复机制
- 解决 Agent 决策不稳定、工具调用失控和上下文过载问题
- 任务完成率由 **71% 提升至 89%**

**3. 长期记忆与用户偏好管理**

- 构建长期记忆检索及删除机制
- 支持用户偏好、商品黑名单和历史选择信息跨会话复用
- 控制历史记忆持续膨胀，提高检索效率
- 长期记忆命中率达到 **72%**

**4. 混合检索与商品召回优化**

- 基于 Embedding 语义检索与 BM25 全文检索实现混合召回
- 使用 RRF 进行结果融合，并结合 Reranker 进行相关性优化
- Top-100 商品召回相关率较基线提升 **22%**
- 在跨语言检索场景下，召回相关率提升 **35%**

**5. Agent 可观测性与实时交互**

- 接入 LangFuse，实现多 Agent、多工具执行链路的 Trace 追踪
- 支持 Token 消耗、工具响应时间及异常执行链路分析
- Badcase 排查时间由 **30 分钟缩短至 5 分钟**
- 基于 AG-UI 事件协议与 WebSocket 实现 Agent 执行进度的实时推送
- 通过 `shopping_session_id` 实现多会话消息路由

---

## 💼 实习经历

### 重庆美天科技有限公司 — 软件开发实习生

**2026.03 – 2026.07**

- 🐍 **Python 自动化：** 基于 Python 开发气象业务数据处理脚本，实现数据读取、清洗处理与批量任务执行
- 🔧 **系统调试：** 参与气象业务系统的故障排查、Bug 调试、问题复现、异常定位及功能验证
- 🖥️ **系统运维：** 负责 5 个气象业务系统的日常运行巡检，检查服务状态与业务运行情况
- ⚙️ **工程实践：** 积累真实业务环境下的系统运行维护、问题排查和团队协作经验

---

## 🎓 教育背景

### 东北师范大学（211）

**计算机技术 · 硕士研究生**

2025.09 – 2028.06（预计毕业）

- 专业排名：**前 10%**

### 广东海洋大学

**软件工程 · 本科**

2021.09 – 2025.06

- 专业排名：**前 20%**

---

## 🏆 竞赛获奖与荣誉

- 🥈 **第十七届蓝桥杯全国总决赛 Java 组二等奖**
- 🥈 **第 22 届百度之星程序设计大赛省赛银奖**
- 🥉 **2026 年码蹄杯本科组全国总决赛三等奖**
- 🥈 第十五届蓝桥杯省赛 Java 组二等奖
- 🏅 第七届大学生算法设计与编程挑战赛金奖
- 📜 软件设计师（软考中级）
- 📚 大学英语六级（CET-6）
- 🎓 本科生学业奖学金及研究生奖学金

---

## 📊 GitHub 数据统计

<div align="center">

![SkateLee's GitHub Stats](https://github-readme-stats.vercel.app/api?username=SkateLee&show_icons=true&theme=radical&hide_border=true)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=SkateLee&layout=compact&theme=radical&hide_border=true)

</div>

---

## 📫 联系我

<div align="center">

🌐 **个人网站：** [withsk8lee.top](https://www.withsk8lee.top)

📧 **电子邮箱：** [liliubing103@163.com](mailto:liliubing103@163.com)

💻 **GitHub：** [github.com/SkateLee](https://github.com/SkateLee)

**专注 AI Agent 工程化，探索具备长期记忆与持续进化能力的智能体系统。🚀**

</div>

<!-- AI Agent Engineer | Agent Harness | Context Engineering -->
<!-- Building in public. -->
