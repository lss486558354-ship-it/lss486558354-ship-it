# Hi, I'm Liu Shuisheng (刘水生) 👋

> "目标系统不给你接口，但事情必须做成。"

**🎯 求职意向**：2027届全日制本科应届生（电气工程及自动化），正在寻找 **AI Agent 开发 / 后端开发 / 嵌入式 FAE** 岗位。**随时可申请离校全职实习**。

**🔗 极客简历与项目演示**：[78456.tech/cv](https://78456.tech/cv)

---

## 🛠️ 技术栈与核心能力

- **AI Native & Agent**: Python, LangChain, MCP (Model Context Protocol), RAG 检索与评估, 多 Agent 协同开发 (Cursor/Claude Code)
- **系统与后端**: SQLite, 状态机设计 (State Machine), 自动化测试 (Pytest), Git, Linux / Ubuntu
- **底层与硬件**: C, STM32 / HAL, RS485, PLC 逻辑, PCB 焊接与硬件排障
- **工程伦理**: 坚持“白盒可审计”，拒绝盲目调参，注重系统的边界防御与断点恢复机制。

---

## 🚀 核心开源项目矩阵

为了在受限环境下解决长任务落地问题，我构建了从“执行边界”到“持久化记忆”的完整闭环框架。

| 项目 | 定位与解决的核心痛点 | 技术亮点 |
| :--- | :--- | :--- |
| **[Agent-LongRun-Framework-v2](https://github.com/lss486558354-ship-it/Agent-LongRun-Framework-v2)** | **状态机与记忆路由深度耦合**。解决长任务跑偏、会话截断失忆的问题。 | 一键脚手架(`agent-projects init`)、项目级数据沙盒隔离、热状态与冷记忆双重恢复、42个行为测试保障。 |
| **[Agent-Memory-Router](https://github.com/lss486558354-ship-it/agent-memory-router)** | **白盒 Agent 记忆路由系统**。解决 LLM 长上下文截断带来的幻觉与 Token 浪费。 | 基于 MCP 协议暴露 4 个读写工具，SQLite 保存元数据与冷数据分离，按需加载避免上下文爆表。 |
| **[engineering-workflow](https://github.com/lss486558354-ship-it/engineering-workflow)** | **AI 编程 Agent 的授权与执行边界协议**。解决 AI 越权乱改代码、任务中断后无法继续的问题。 | 设计双层状态机（读写门禁 × 执行策略），强制约束 AI 动作，实现断点续传。 |
| **[diagnosis-agent](https://github.com/lss486558354-ship-it/diagnosis-agent)** | **基于 MCP Server 的 RAG 检索与评估系统**。 | 接入多工具查故障，设计了防幻觉拒答机制（测出 RRF 失败场景），坚持真实的检索评估而不调参拟合。 |
| **[printer-controller](https://github.com/lss486558354-ship-it/printer-controller)** | **8.5k 行企业级商业交付**。解决无 API 硬件设备的无人值守闭环难题。 | 纯底层硬核实现：HDMI 诱骗 + GUI 自动化 + 像素级识别 + PLC 状态机，已完成真实的商业交付。 |

---

## 🏆 荣誉与经历

- **国家级一等奖**（2026 智能装备创新设计赛 / 2024 机械创新设计大赛）、**省级一等奖**
- **TI 杯** 全国大学生电子设计竞赛 省级二等奖（本科）/ 三等奖（专科）
- 电子创新工作室 软件部部长（带领 20+ 人团队）
- 拥有真实商业项目交付经验（从签约前可行性验证到最终验收）

*“AI 可以代劳敲键盘，但不能代替我思考。”*
