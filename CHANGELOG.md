# Changelog

All additions and rejections are logged here. Most recent entries appear first.

---

## 2026-05-13

### Added
- [Not What You've Signed Up For](https://arxiv.org/abs/2302.12173) → §1.2 Indirect Prompt Injection | Named and formalized indirect prompt injection; foundational read
  - 来源：初始建库
  - 收录理由：该领域奠基论文

- [AgentDojo](https://arxiv.org/abs/2406.13352) → §1.2 Indirect Prompt Injection | Best current benchmark for indirect injection; limited to web/email scenarios
  - 来源：初始建库
  - 收录理由：目前最主要的间接注入 benchmark

- [PoisonedRAG](https://arxiv.org/abs/2402.07867) → §1.3 Memory & RAG Poisoning | 5 poisoned docs among millions achieve 90% attack success; alarming scalability
  - 来源：初始建库
  - 收录理由：RAG 投毒攻击中结果最有影响力的论文

- [AgentPoison](https://arxiv.org/abs/2407.12784) → §1.3 Memory & RAG Poisoning | Extends RAG poisoning to full agent pipelines; transfers across agent tasks
  - 来源：初始建库
  - 收录理由：将 RAG 投毒扩展到完整 agent 流程

- [Watch Out for Your Agents!](https://arxiv.org/abs/2402.11208) → §1.5 Backdoor Attacks | Systematic backdoor study via poisoned tool demos; NeurIPS 2024
  - 来源：初始建库
  - 收录理由：第一篇系统研究 agent 后门的顶会论文

- [Prompt Infection](https://arxiv.org/abs/2410.07283) → §1.6 Multi-Agent Propagation | First to formalize cross-agent injection propagation; exponential spread in large MAS
  - 来源：初始建库
  - 收录理由：多 agent 传播攻击的奠基论文

- [ShieldAgent](https://arxiv.org/abs/2502.17747) → §2.1 Input Filtering & Guardrails | Generates guardrail policies from documents; more flexible than rule-based systems
  - 来源：初始建库
  - 收录理由：ICML 2025，防御侧新方向

- [Agent Security Bench (ASB)](https://arxiv.org/abs/2410.02644) → §0 Surveys | Most comprehensive formalization; 10 attack scenarios, 10 agents, 398 environments
  - 来源：初始建库
  - 收录理由：目前最全面的 agent 安全 benchmark，ICLR 2025

## 2026-05-17

### Added
- [Hidden in the Metadata (MM-MEPA)](https://arxiv.org/abs/2603.00172) → §1.3 Memory & RAG Poisoning | Image-intact metadata-only poisoning achieves 91% ASR on multimodal RAG; bypasses query paraphrasing and consistency checks
  - 来源:arXiv cs.CR daily
  - 收录理由:多模态 RAG 投毒论文；攻击方式仅篡改元数据、不注入新内容
    
- [Dissecting Adversarial Robustness of Multimodal LM Agents](https://arxiv.org/abs/2406.12814) → §1.2 Indirect Prompt Injection | Imperceptible pixel perturbations hijack multimodal web agents (up to 67% ASR)
  - 来源:ICLR 2025 proceedings
  - 收录理由:首篇系统研究多模态 web agent 像素级对抗攻击的论文

- [AdvAgent: Controllable Blackbox Red-teaming on Web Agents](https://arxiv.org/abs/2410.17401) → §1.2 Indirect Prompt Injection | RL-trained black-box adversarial prompter, 97.5% ASR on GPT-4V web agents
  - 来源:ICML 2025 proceedings
  - 收录理由:目前 web agent 黑盒攻击中 ASR 最高的工作之一，且对现有防御依然有效

- [CVE-Bench](https://arxiv.org/abs/2503.17332) → §3 Benchmarks & Evaluation | First real-world CVE-based benchmark for evaluating LLM agent offensive capabilities
  - 来源:ICML 2025 Spotlight
  - 收录理由:首个基于真实 CVE 的 agent 能力评测，填补"评估 agent 攻击能力"维度

- [AgentFuzz](https://www.usenix.org/conference/usenixsecurity25/presentation/liu-fengyu) → §4 Tools & Frameworks | First fuzzing framework for taint-style vulnerabilities in LLM agents; 34 zero-days with 100% precision
  - 来源:USENIX Security 2025
  - 收录理由:首个针对 LLM agent 污点漏洞的模糊测试工具，实战价值高

---
