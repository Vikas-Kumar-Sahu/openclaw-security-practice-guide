# OpenClaw Security Practice Guide

[![OpenClaw](https://img.shields.io/badge/OpenClaw-Compatible-blue.svg)](https://github.com/openclaw/openclaw)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Language](https://img.shields.io/badge/Language-English%20%7C%20中文-success)](#)

*Read this in other languages: [English](README.md), [简体中文](README_zh-CN.md).*

A definitive security practice guide designed specifically for **High-Privilege Autonomous AI Agents** (OpenClaw). It shifts the paradigm from traditional "host-based static defense" to "Agentic Zero-Trust Architecture", effectively mitigating risks like destructive operations, prompt injection, supply chain poisoning, and high-risk business logic execution.

## 🎯 Scope, Scenario & Core Principles

> **This guide is designed for OpenClaw itself (Agent-facing), not as a traditional human-only hardening checklist.**  
> In practice, you can send this guide directly to OpenClaw in chat, let it evaluate reliability, and deploy the defense matrix with minimal manual setup.

> **Important boundary:** This guide does **not** make OpenClaw “fully secure.”  
> Security is a complex systems engineering problem, and absolute security does not exist.  
> This guide is built for a specific threat model, scenario, and operating assumptions.  
> **Final responsibility and last-resort judgment remain with the human operator.**

### Target Scenario
- OpenClaw runs with high privileges (terminal/root-capable environment)
- OpenClaw continuously installs and uses Skills / MCPs / scripts / tools
- The objective is capability maximization with controllable risk and explicit auditability

### Core Principles
1. **Zero-friction operations**: reduce manual security setup burden for users and keep daily interactions seamless, except when hitting a guideline-defined red line  
2. **High-risk requires confirmation**: irreversible or sensitive actions must pause for human approval  
3. **Explicit nightly auditing**: all core metrics are reported, including healthy ones (no silent pass)  
4. **Zero-Trust by default**: assume prompt injection, supply chain poisoning, and business-logic abuse are always possible  

### Model Recommendation (Important)
This guide is primarily interpreted and executed by OpenClaw.  
For best reliability, use a **strong, latest-generation reasoning model** (e.g., current top-tier models such as Gemini / Opus / Kimi / MiniMax families).  
Higher-quality models generally perform better at:
- understanding long-context security constraints
- detecting hidden instruction patterns and injection attempts
- executing deployment steps consistently with fewer mistakes

✅ This is exactly how this guide **reduces user configuration cost**: OpenClaw can understand, deploy, and validate most of the security workflow for you.

## 🌟 Why This Guide?

Running an AI Agent like OpenClaw with root/terminal access is powerful but inherently risky. Traditional security measures (`chattr +i`, firewalls) are either incompatible with Agentic workflows or insufficient against LLM-specific attacks like Prompt Injection.

This guide provides a battle-tested, minimalist **3-Tier Defense Matrix**:
1. **Pre-action**: Behavior blacklists & strict Skill installation audit protocols (Anti-Supply Chain Poisoning)
2. **In-action**: Permission narrowing & Cross-Skill Pre-flight Checks (Business Risk Control)
3. **Post-action**: Nightly automated explicit audits (13 core metrics) & Brain Git disaster recovery

## 🚀 Zero-Friction Flow

In the AI era, humans shouldn't have to manually execute security deployments. **Let your OpenClaw Agent do all the heavy lifting.**

1. **Download the Guide**: Get the core document [OpenClaw-Security-Practice-Guide.md](docs/OpenClaw-Security-Practice-Guide.md)
2. **Send to Agent**: Drop the markdown file directly into your chat with your OpenClaw Agent
3. **Agent Evaluation**: Ask your Agent: "*Please read this security guide carefully. Is it reliable?*"
4. **One-Click Deployment**: Once the Agent confirms its reliability, issue the command: "*Please deploy this defense matrix exactly as described in the guide. Include the red/yellow line rules, tighten permissions, and deploy the nightly audit Cron Job.*"
5. **Validation Testing(Optional)**: After deployment, use the [Red Teaming Guide](docs/Validation-Guide-en.md) to simulate an attack and ensure the Agent correctly interrupts the operation

*(Note: The `scripts/` directory in this repository is strictly for open-source transparency and human reference. **You do NOT need to manually copy or run it.** The Agent will automatically extract the logic from the guide and handle the deployment for you.)*

## 📖 Table of Contents

### Core Documents
* [**OpenClaw Minimalist Security Practice Guide v2.7 (English)**](docs/OpenClaw-Security-Practice-Guide.md) - The complete guide
* [**OpenClaw 极简安全实践指南 v2.7 (中文版)**](docs/OpenClaw极简安全实践指南.md) - Complete guide in Chinese

### Validation & Red Teaming
To ensure your AI assistant doesn't bypass its own defenses out of "obedience", be sure to run these drills:
* [Security Validation & Red Teaming Guide (English)](docs/Validation-Guide-en.md) - End-to-end defense testing
* [安全验证与攻防演练手册 (中文版)](docs/Validation-Guide-zh.md) - The guide in Chinese

### Tools & Scripts
* [`scripts/nightly-security-audit.sh`](scripts/nightly-security-audit.sh) - Reference shell script for nightly OpenClaw automated auditing and Git backups (for reading only, manual installation not required)

## 🤝 Contributing
Contributions, issues, and feature requests are welcome!

Thanks: SlowMist Security Team([@SlowMist_Team](https://x.com/SlowMist_Team)), Edmund.X([@leixing0309](https://x.com/leixing0309))

## 📝 License
This project is [MIT](LICENSE) licensed.
