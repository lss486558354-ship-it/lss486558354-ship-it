# 刘水生 · Liu Shuisheng

> 给 AI Agent 装上状态机与记忆。

**2027 届应届生** · 湖南交通工程学院 · 电气工程及其自动化

**求职方向**：Agent 基建 / AI 应用工程 / AI Native 全栈 · 可随时离校全职实习

**简历与项目演示**：[78456.tech/cv](https://78456.tech/cv)

---

## 定位

重度 AI Native 开发者，专注 AI Agent 的底层约束：**执行状态机、读写门禁、MCP 白盒记忆路由、项目级工作区隔离**。

电气工程背景，能从 STM32 固件下到 Linux 自动化，也能用测试和可复现实验，把 AI 生成的代码约束成可交付系统。

**可验证的数据**：42 + 47 个 pytest · 7 态状态机 · 4 个 MCP 工具 · 8.5k 行商业交付。

---

## 核心项目

### 1. [Agent-LongRun-Framework-v2](https://github.com/lss486558354-ship-it/Agent-LongRun-Framework-v2)
**长任务 Agent 的执行状态机 × 记忆路由** · 开源 / 独立架构

- 7 态状态机 + 读写门禁：默认 `read_only`，调研完成必须显式 `enable_writes(原因)` 才能写文件。
- `checkpoint()` 先 `save_memory` 成功、再输出断点；写入失败只落 `pending_checkpoint.json`，不输出假回执。
- 热状态 `<项目根>/.longrun/state.json` + 冷记忆 `memory.db` / `raw_data/`，`resume()` 不会读到别的项目。
- 42 个 pytest 行为测试；本地后端与真实 MCP stdio 双链路示例。

### 2. [agent-memory-router-v2](https://github.com/lss486558354-ship-it/agent-memory-router-v2)
**项目级白盒记忆路由** · 开源 / 独立开发

- 每个项目独立 `memory.db`（SQLite 索引）+ `raw_data/<id>/raw.txt`（原文）；全局索引只登记路径，不存内容。
- 4 个 MCP 工具：`search_memory` / `read_raw_data` / `save_memory` / `link_memory`，返回统一 JSON。
- `agent-projects init` 一键生成 `.mcp.json`、skill、`.gitignore`，已有文件先备份、只改受管标记块。
- 47 个 pytest：路径解析、v0.1 迁移、原子写索引、`--project_path` 均有覆盖。

### 3. [多平台制造报价 Agent](https://78456.tech) — 线上运行 / 企业委托
**自动跨平台取价，构建可核验、可比较的证据链**

- `BaseAdapter + @register`，平台即插即用；公共防线收在基类。
- 置信度 = 时间衰减 × 佐证强度；多币种拒绝直接比价；偶发抖动 vs 整段不可用，后者熔断而非重试。
- SQLite 跨线程锁 + Fernet 凭证加密 + 全链路工单号溯源；FastAPI + Playwright。
- 线上入口：[78456.tech](https://78456.tech)

### 4. [diagnosis-agent](https://github.com/lss486558354-ship-it/diagnosis-agent)
**设备故障诊断 RAG × MCP 评估** · 开源

- 17 份技术文档 / 288 块，表格与代码块原子保护，命令帧不被截断。
- 交付 6 个 MCP 工具；门控拒答 10/10 拦截。
- 测出混合检索默认权重下跑输纯 BM25（Recall@5 打平 80.0%，MRR@5 0.583 → 0.543）；不改默认值，因为评估集不能同时用来调参。

### 5. [printer-controller](https://github.com/lss486558354-ship-it/printer-controller)
**自助 3D 打印终端 · 自动化核心模块** · 商业交付 / 开源 8.5k 行

- 目标软件无 CLI / HTTP API / 插件：先用 RS485 抓包确认可控，再签合同。
- 签约后方案被推翻，换路线：桌面 Linux + 键鼠回放 + 像素识别 + PLC 风格状态机。
- 打印 → 云端验证码 → 二维码取件，全程无人值守；X11 + systemd + HDMI 诱骗器。

### 6. [scallion-washer-packer](https://github.com/lss486558354-ship-it/scallion-washer-packer)
**叶菜切割-清洗-打包一体机 · 电控系统** · 国一 + 省一

- 电控与上位机开发负责人；20 天、无正式 PCB，手焊洞洞板原型直接上比赛现场。
- STM32F103：9 状态工艺流程状态机 + 6 路步进 + 4 路飞特总线舵机 + 超声波 / 称重 / 限位。
- 绝对时间基准消除阶段切换竞态；对照实验定位 2/10 复现率的共地干扰；同一台设备零改动，省一 + 国一。

> 前代项目：[engineering-workflow](https://github.com/lss486558354-ship-it/engineering-workflow) — AI 编程 Agent 的授权与推进协议，v2 的状态机与门禁设计从这里演化而来。

---

## 技术栈

| 方向 | 具体 |
| --- | --- |
| **Agent 基建** | 状态机设计、读写门禁、checkpoint / resume、项目级沙盒、MCP Server、结构化输出、规则 / skill 设计 |
| **AI 应用** | RAG（分块 / BM25 / 向量 / RRF / 引用溯源）、检索评估、Ollama bge-m3、jieba、置信度建模 |
| **工程化** | Python、pytest、SQLite、FastAPI、Playwright、多线程 / 锁、Fernet、Git、Linux systemd、Cloudflare Tunnel |
| **底层 / 硬件** | C、STM32F103、FreeRTOS、Keil MDK、UART 协议、步进电机加减速、飞特总线舵机、硬件调试与干扰定位 |
| **AI 协同** | Claude Code / Cursor / Codex 日常开发、规则驱动、AI 代码审查与重构 |

---

## 获奖

- **国家级一等奖** — 2026 中国大学生机械工程创新创意大赛 · 智能装备创新设计赛（证书编号 `MEICC02IEIDC2026-JB1-038`）
- **省级一等奖** — 2026 年第十二届湖南省大学生机械创新设计大赛
  *同一台设备、两场比赛之间未作任何改动。*

---

## 联系

📧 **lss486558.54@gmail.com** · GitHub [@lss486558354-ship-it](https://github.com/lss486558354-ship-it)
