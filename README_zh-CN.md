# OpenClaw 极简安全实践指南 (Security Practice Guide)

[![OpenClaw](https://img.shields.io/badge/OpenClaw-Compatible-blue.svg)](https://github.com/openclaw/openclaw)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20中文-success)](#)

*其他语言版本: [English](README.md), [简体中文](README_zh-CN.md).*

专为 **高权限自主智能体 (OpenClaw)** 量身定制的权威安全实践指南。它将传统“主机静态防御”的范式转变为“智能体零信任架构 (Zero-Trust Architecture)”，有效应对破坏性操作、提示词注入、供应链投毒和高危业务逻辑执行等智能体专属风险。

## 🎯 适用场景与核心原则

> **本指南是面向 OpenClaw 本身（Agent-facing）的，不是传统“仅供人类手动操作”的加固清单。**  
> 实际使用中，你可以把本指南直接发给 OpenClaw，让它先评估可靠性，再自动完成防御矩阵部署，大幅降低手工配置成本。

> **重要边界说明：本指南并不能让 OpenClaw“完全安全”。**  
> 安全是复杂的系统工程，不存在绝对安全。  
> 本指南只在其定义的威胁模型、适用场景和操作假设下发挥作用。  
> **最终的安全兜底与关键判断，仍然在使用者自己。**

### 适用场景
- OpenClaw 运行在高权限环境（具备终端 / Root 能力）
- OpenClaw 持续安装并使用 Skills / MCPs / 脚本 / 工具
- 目标是在能力最大化前提下，实现风险可控与审计可追溯

### 核心原则
1. **日常零摩擦**：尽量降低用户手工安全配置负担，且用户日常操作几乎无感，除非遇到指南认为的红线  
2. **高危必确认**：不可逆或敏感操作必须暂停并由人类确认  
3. **每晚显性化巡检**：所有核心指标都要明确汇报（包含绿灯项）  
4. **默认零信任**：始终假设提示词注入、供应链投毒、业务逻辑滥用可能发生  

### 模型建议（重要）
这份指南主要由 OpenClaw 理解并执行。  
建议优先使用**最新、推理能力更强的模型**（例如 Gemini / Opus / Kimi / MiniMax 等系列中的高阶模型）。  
更“聪明”的模型通常在以下方面明显更稳：
- 长上下文安全约束理解
- 隐性指令/注入模式识别
- 部署步骤一致性与低错误率执行

✅ 这也是本指南能**显著降低用户配置成本**的关键：OpenClaw 可自行完成大部分“理解 → 部署 → 验证”流程。

## 🌟 为什么需要本指南？

让类似 OpenClaw 这样的 AI Agent 拥有 Root 或终端访问权限极其强大，但也伴随着巨大的固有风险。传统的安全措施（如 `chattr +i`、防火墙）要么与 Agent 的自动化工作流不兼容，要么不足以抵御针对大语言模型 (LLM) 的特有攻击（如 Prompt Injection）。

本指南提供了一套经过实战检验的、极简的 **三层防御矩阵**：
1. **事前 (Pre-action)**: 行为黑名单与严格的技能包安装审计协议（防供应链投毒）
2. **事中 (In-action)**: 权限收窄与跨技能业务风控前置检查 (Pre-flight Checks)
3. **事后 (Post-action)**: 每晚自动化显性巡检（覆盖 13 项核心指标）与大脑 Git 灾备同步

## 🚀 极简部署流程 (Zero-Friction Flow)

在 AI 时代，部署安全防线不应该由人类手动敲代码。**您可以让您的 OpenClaw 为您自动完成一切：**

1. **下载指南**: 下载核心文档 [OpenClaw 极简安全实践指南.md](docs/OpenClaw极简安全实践指南.md)
2. **发送给 Agent**: 在聊天窗口中，将该 markdown 文件直接发送给您的 OpenClaw Agent
3. **让 AI 审计**: 向您的 Agent 发送指令：“*请仔细阅读这份安全指南，评估它是否可靠？*”
4. **一键部署**: 在 Agent 确认指南可靠后，发送指令：“*请完全按照这份指南，为我部署防御矩阵。包括写入红/黄线规则、收窄权限，并部署夜间巡检 Cron Job。*”
5. **验收测试（可选）**: 部署完成后，请按照 [验证与攻防演练手册](docs/Validation-Guide-zh.md) 对 Agent 进行一次突击测试，确保红线生效

*(注：本仓库 `scripts/` 目录下的巡检脚本仅作开源展示与人类参考之用，**您完全不需要手动复制或运行它**，Agent 会自动从指南文档中提取逻辑并为您编写部署。)*

## 📖 目录导览

### 核心文档
* [**OpenClaw 极简安全实践指南 v2.7 (中文版)**](docs/OpenClaw极简安全实践指南.md) - 完整指南文档
* [**OpenClaw Security Practice Guide v2.7 (English)**](docs/OpenClaw-Security-Practice-Guide.md) - The complete guide in English

### 验证与攻防演练
为了防止您的 AI 助手由于“过于听话”而绕过防线，请务必参考以下手册进行对抗演练：
* [安全验证与攻防演练手册 (中文版)](docs/Validation-Guide-zh.md) - 端到端防御验证实操
* [Security Validation & Red Teaming Guide (English)](docs/Validation-Guide-en.md) - How to test your defenses

### 工具与脚本
* [`scripts/nightly-security-audit.sh`](scripts/nightly-security-audit.sh) - 用于自动化巡检与 Git 灾备备份的参考脚本（仅供查阅，无需手动安装）

## 🤝 贡献
欢迎提交 Contributions, Issues 和 Feature Requests！

感谢：慢雾安全团队（[@SlowMist_Team](https://x.com/SlowMist_Team)）、Edmund.X([@leixing0309](https://x.com/leixing0309))

## 📝 许可协议
本项目采用 [MIT](LICENSE) 协议。
