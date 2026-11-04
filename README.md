<div align="center">

# 刘水生 · Liu Shuisheng

**给 AI Agent 装上状态机与记忆。**

Agent 基建 · 长任务运行时契约 · 重度 AI Native 开发者

**求职方向**：Agent 基建 / AI 应用工程 / AI Native 全栈 · 2027 届应届生

[**简历与项目演示 →**](https://78456.tech/cv) · [邮箱](mailto:lss486558354@gmail.com) · [GitHub](https://github.com/lss486558354-ship-it)

![Python](https://img.shields.io/badge/Python-3.10--3.12-3776AB?logo=python&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-52%20%2B%2047-0A9EDC?logo=pytest&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-4%20tools-10b981)
![License](https://img.shields.io/badge/license-MIT-10b981)

</div>

---

> **Agent 的运作，就像跟产品经理对接。**
>
> **对话态（只读）**：与 Agent 对齐颗粒度——澄清需求、探讨方案；
> **执行态（可写）**：审核通过方案后的任务下发——闭门写代码，绝不瞎发散。

## 定位

重度 AI Native 开发者，专注 AI Agent 的底层约束：**执行状态机、单轮写租约、MCP 白盒记忆路由、项目级工作区隔离**。

电气工程背景，能从 STM32 固件下到 Linux 自动化，也能用测试和可复现实验，把 AI 生成的代码约束成可交付系统。

**可验证的数据**：52 + 47 个 pytest · 7 态状态机 · 4 个 MCP 工具 · 8.5k 行商业交付 · CI 覆盖 Python 3.10–3.12。

---

## 核心项目

### [Agent-LongRun-Framework-v3](https://github.com/lss486558354-ship-it/Agent-LongRun-Framework-v3)

**长任务 Agent 的执行状态机 × 单轮写租约 × MCP 记忆路由** · 开源 / 独立架构

- **执行边界**：7 态状态机，默认 `read_only`；调研完成必须显式 `enable_writes(原因)` 才能写文件，非法流转抛 `TransitionError`。
- **单轮写租约**：`enable_writes()` 只绑定当前 `turn_index`；`begin_turn()` / `end_turn()` / `checkpoint()` / `resume()` 都会收回写权限，过期租约抛 `WriteGateViolation`。
- **断点协议**：`checkpoint()` 先 `save_memory` 成功、再输出断点；写入失败只落 `pending_checkpoint.json`，不输出「已保存」的假回执。
- **项目级隔离**：热状态 `.longrun/state.json` + 冷记忆 `memory.db` / `raw_data/` 绑定同一个项目根，`resume()` 不会读到别的项目。
- **可恢复性**：断点带 `<!-- longrun-state: {...} -->` 机器标记；`recover_from_memory()` 从记忆重建任务，不靠模型猜状态。
- **验证**：52 个 pytest · CI 覆盖 Python 3.10–3.12 · `agent-longrun demo` 一条命令跑通只读 → 授权 → 断点 → 恢复 → 租约失效 → 重新授权。

```bash
python -m pip install "agent-memory-router @ git+https://github.com/lss486558354-ship-it/agent-memory-router-v2.git"
python -m pip install "agent-longrun-framework @ git+https://github.com/lss486558354-ship-it/Agent-LongRun-Framework-v3.git"

agent-longrun demo
```

> 预期输出：`OK: checkpoint -> resume -> single-turn write lease -> finish`

### 项目矩阵

| 项目 | 关键词 | 可验证的结果 |
| --- | --- | --- |
| [agent-memory-router-v2](https://github.com/lss486558354-ship-it/agent-memory-router-v2) | 项目级白盒记忆路由 | 4 个 MCP 工具 · 47 pytest · 每个项目独立 `memory.db` + 原文目录 |
| [多平台制造报价 Agent](https://78456.tech) | 跨平台取价证据链 | 线上运行 · FastAPI + Playwright · 置信度建模 · 熔断与工单号溯源 |
| [diagnosis-agent](https://github.com/lss486558354-ship-it/diagnosis-agent) | 设备故障诊断 RAG × MCP | 17 份文档 / 288 块 · 6 个 MCP 工具 · Recall@5 80.0% · MRR@5 0.583 → 0.543 |
| [printer-controller](https://github.com/lss486558354-ship-it/printer-controller) | 无 API 软件自动化 | 8.5k 行 · 已交付验收 · Linux + 键鼠回放 + 像素识别 + PLC 状态机 |
| [scallion-washer-packer](https://github.com/lss486558354-ship-it/scallion-washer-packer) | 叶菜一体机电控系统 | 国一 + 省一 · STM32F103 · 9 状态工艺流程状态机 · 6 路步进 + 4 路总线舵机 |

> 前代项目：[engineering-workflow](https://github.com/lss486558354-ship-it/engineering-workflow) — AI 编程 Agent 的授权与推进协议，v3 的状态机、门禁与单轮租约设计从这里演化而来。

---

## 技术栈

| 方向 | 具体 |
| --- | --- |
| **Agent 基建** | 状态机设计、读写门禁、单轮写租约、checkpoint / resume、项目级沙盒、MCP Server、结构化输出、规则 / skill 设计 |
| **AI 应用** | RAG（分块 / BM25 / 向量 / RRF / 引用溯源）、检索评估、Ollama bge-m3、jieba、置信度建模 |
| **工程化** | Python、pytest、SQLite、FastAPI、Playwright、多线程 / 锁、Fernet、Git、Linux systemd、Cloudflare Tunnel |
| **底层 / 硬件** | C、STM32F103、FreeRTOS、Keil MDK、UART 协议、步进电机加减速、飞特总线舵机、硬件调试与干扰定位 |
| **AI 协同** | Claude Code / Cursor / Codex 日常开发、规则驱动、AI 代码审查与重构 |

---

## 工程原则

- **只写跑过的数字**：测试数、线上状态、检索指标都能在仓库或站点复现。
- **先把边界写进代码**：不靠 Prompt 祈祷 Agent 遵守流程，靠状态机、租约和失败路径。
- **Built with AI, Reviewed by Human.** 不隐藏 AI 辅助，也不把 AI 的产出直接当成自己的结论。

---

## 获奖

- **国家级一等奖** — 2026 中国大学生机械工程创新创意大赛 · 智能装备创新设计赛（证书编号 `MEICC02IEIDC2026-JB1-038`）· 角色：电控与上位机开发负责人
- **省级一等奖** — 2026 年第十二届湖南省大学生机械创新设计大赛 · 同一台设备、两场比赛之间未作任何改动

---

## 联系

📧 **lss486558354@gmail.com** · 🌐 [78456.tech/cv](https://78456.tech/cv) · GitHub [@lss486558354-ship-it](https://github.com/lss486558354-ship-it)
