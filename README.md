# 刘水生 · Liu Shuisheng

> 给 AI Agent 装上状态机与记忆。

**🎯 求职意向**：2027 届应届生，方向：**Agent 基建 / AI 应用工程 / AI Native 全栈**。随时可离校全职实习。

**🔗 在线简历**：[78456.tech/cv](https://78456.tech/cv)　**📮 联系**：[lss486558.54@gmail.com](mailto:lss486558.54@gmail.com)

---

## 定位

我关心的是 Agent 在真实工程里的可控性：按状态推进、写之前确认、跨会话恢复、记忆留在项目里。

- **执行状态机**：7 态、显式白名单流转，非法跳转直接失败
- **读写门禁**：调研阶段只读，方案确认后才允许写
- **MCP 白盒记忆路由**：SQLite 索引 + 原文按需加载，项目级隔离
- **可验证**：42 + 47 个 pytest、4 个 MCP 工具、8.5k 行生产级 Python

---

## 核心项目

| 项目 | 解决的问题 | 关键实现 |
| :--- | :--- | :--- |
| **[Agent-LongRun-Framework-v2](https://github.com/lss486558354-ship-it/Agent-LongRun-Framework-v2)** | 长任务跑偏、会话截断失忆 | 7 态状态机、读写门禁、热状态 + 冷记忆双重恢复、42 个行为测试 |
| **[agent-memory-router-v2](https://github.com/lss486558354-ship-it/agent-memory-router-v2)** | LLM 长上下文截断、Token 浪费 | MCP 暴露 4 个读写工具、每项目独立 `memory.db` + `raw_data/`、47 个离线测试 |
| **多平台制造报价 Agent**（[线上运行](https://78456.tech) · 私有项目） | 多平台报价链路无法无人值守 | 自动登录 / STEP 上传 / 参数配置 / 真实报价抓取 / 价格监测 |
| **[diagnosis-agent](https://github.com/lss486558354-ship-it/diagnosis-agent)** | 工业文档不可检索、不可溯源 | BM25 + 向量 + RRF、零命中门控、30 题 × 4 配置检索评估 |
| **[printer-controller](https://github.com/lss486558354-ship-it/printer-controller)** | 无 API 设备的无人值守闭环 | 像素级识别、PLC 状态机、OTA 三重防护、8.5k 行商业交付 |
| **[scallion-washer-packer](https://github.com/lss486558354-ship-it/scallion-washer-packer)** | 叶菜切割—清洗—打包电控闭环 | STM32F103VE + FreeRTOS、四路串口、1ms 工艺状态机 |

**前代项目**：[engineering-workflow](https://github.com/lss486558354-ship-it/engineering-workflow) —— 给 AI 编程 Agent 的授权与推进协议，定义读写门禁 × 执行策略的双层状态机，是 LongRun-v2 状态机设计的前身。

---

## 技术栈

- **Agent 基建**：Python、MCP、SQLite、状态机设计、断点恢复、项目级隔离
- **AI 应用**：RAG 检索与评估、BM25、向量检索、RRF 融合、防幻觉门控
- **工程化**：Pytest、Git、Linux / Ubuntu、systemd、OTA、SHA256 校验
- **底层硬件**：C、STM32 / HAL、FreeRTOS、RS485、PLC 逻辑、PCB 焊接与硬件排障
- **AI 协同**：Cursor、Claude Code、Codex、rules / skills 设计、多 Agent 协作

---

## 获奖

- **2026.09** 中国大学生机械工程创新创意大赛 · 智能装备创新设计赛 · 本科生组 **全国一等奖**（中国机械工程学会｜证书编号 `MEICC02IEIDC2026-JB1-038`）
- **2026** 湖南省大学生机械工程创新创意大赛 · 主赛道叶菜组 **一等奖**（湖南省教育厅）

---

## 联系

- 📮 邮箱：[lss486558.54@gmail.com](mailto:lss486558.54@gmail.com)
- 🔗 简历：[78456.tech/cv](https://78456.tech/cv)
- 💻 GitHub：[@lss486558354-ship-it](https://github.com/lss486558354-ship-it)

---

> **Built with AI, Reviewed by Human.** 只写可复现的事实。
