# 🛡️ Awesome Agentic Security

> A curated list of papers, benchmarks, tools, and resources on the security of agentic AI systems — organized by **attack entry point**, with concise commentary on contributions and limitations.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Last Updated](https://img.shields.io/badge/updated-May%202026-blue)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)
![Scope](https://img.shields.io/badge/scope-agentic%20security-orange)

---

## Why This List?

Most existing awesome lists on agent safety are **paper dumps** — long, flat, and hard to navigate. This list is different:

- 📌 **Organized by attack entry point** — so you know *where* the threat comes from
- 💬 **Each entry has a one-line commentary** — what it contributes, and what it misses
- 👥 **Useful for both researchers and engineers** — papers and tools side by side

**Scope**: Agentic AI systems (single and multi-agent). We cover attacks, defenses, benchmarks, and tools specific to agentic settings. We do *not* cover general LLM safety (jailbreaks without agent context) or embodied/robotics safety.

---

## Contents

- [0. Surveys & Position Papers](#0-surveys--position-papers)
- [1. Attacks by Entry Point](#1-attacks-by-entry-point)
  - [1.1 Direct Prompt Injection](#11-direct-prompt-injection)
  - [1.2 Indirect Prompt Injection](#12-indirect-prompt-injection)
  - [1.3 Memory & RAG Poisoning](#13-memory--rag-poisoning)
  - [1.4 Tool & MCP Poisoning](#14-tool--mcp-poisoning)
  - [1.5 Backdoor Attacks](#15-backdoor-attacks)
  - [1.6 Multi-Agent Propagation](#16-multi-agent-propagation)
- [2. Defenses](#2-defenses)
  - [2.1 Input Filtering & Guardrails](#21-input-filtering--guardrails)
  - [2.2 Instruction Hierarchy](#22-instruction-hierarchy)
  - [2.3 Sandboxing & Permission Control](#23-sandboxing--permission-control)
  - [2.4 Multi-Agent Trust Protocols](#24-multi-agent-trust-protocols)
- [3. Benchmarks & Evaluation](#3-benchmarks--evaluation)
- [4. Tools & Frameworks](#4-tools--frameworks)
- [Contributing](#contributing)

---

## Threat Model Overview

```
┌─────────────────────────────────────────────────────┐
│               Agentic AI System                     │
│                                                     │
│  User ──[1.1 Direct]──► LLM Core                   │
│                              │                      │
│  Environment ──[1.2 Indirect]┘                      │
│                                                     │
│  Memory/RAG ──[1.3]──────────► Planning             │
│                                    │                │
│  Tools/MCP ──[1.4]────────────────►│                │
│                                    │                │
│  Training Data ──[1.5 Backdoor]───►│                │
│                                    ▼                │
│  Other Agents ──[1.6]──────────► Actions            │
└─────────────────────────────────────────────────────┘
```

---

## 0. Surveys & Position Papers

| Paper | Venue | Commentary |
|-------|-------|------------|
| [A Survey on LLM-based Autonomous Agents](https://arxiv.org/abs/2308.11432) | arXiv 2023 | Good overview of agent architectures; safety treated as an afterthought |
| [Evil Geniuses: Delving into the Safety of LLM-based Agents](https://arxiv.org/abs/2311.11855) | arXiv 2023 | Early systematic look at agent-specific risks; taxonomy is now partially outdated |
| [Agent Security Bench (ASB)](https://arxiv.org/abs/2410.02644) | ICLR 2025 | Most comprehensive formalization of attack types; 10 attack scenarios, 10 agents, 398 adversarial environments |
| [A Comprehensive Survey in LLM(-Agent) Full Stack Safety](https://arxiv.org/abs/2407.01003) | arXiv 2025 | Covers the full lifecycle; broad but less deep on agent-specific entry points |
| [Practices for Governing Agentic AI Systems](https://openai.com/index/practices-for-governing-agentic-ai/) | OpenAI 2023 | Industry perspective from OpenAI; useful framing for deployment-level governance |

---

## 1. Attacks by Entry Point

### 1.1 Direct Prompt Injection

The attacker controls the user-facing input to the agent directly.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Prompt Injection Attacks and Defenses in LLM-Integrated Applications](https://arxiv.org/abs/2310.12815) | arXiv 2023 | Foundational taxonomy of direct injection; predates agentic tool-use context |
| [AgentHarm: A Benchmark for Direct Misuse of LLM Agents](https://arxiv.org/abs/2410.09024) | ICLR 2025 | Focuses on direct harmful requests (not adversarial injection); fills a gap vs. indirect-focused benchmarks |
| [Jailbreaking Leading Safety-Aligned LLMs with Simple Adaptive Attacks](https://arxiv.org/abs/2404.02151) | ICLR 2025 | Shows adaptive attacks break most existing defenses; highlights the fragility of guardrail-only approaches |

---

### 1.2 Indirect Prompt Injection

Malicious instructions are embedded in content the agent retrieves from the environment (web pages, emails, documents, API responses).

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injections](https://arxiv.org/abs/2302.12173) | AISec 2023 | The paper that named and formalized indirect prompt injection; foundational read |
| [AgentDojo: A Dynamic Environment to Evaluate Attacks and Defenses for LLM Agents](https://arxiv.org/abs/2406.13352) | NeurIPS 2024 | Best current benchmark for indirect injection; realistic task environments but limited to web/email scenarios |
| [WASP: Benchmarking Web Agent Security Against Prompt Injection Attacks](https://arxiv.org/abs/2504.18575) | arXiv 2025 | Specifically targets web navigation agents; more realistic threat model than AgentDojo |
| [(Ab)using Images and Sounds for Indirect Instruction Injection in Multi-modal LLMs](https://arxiv.org/abs/2307.10490) | arXiv 2023 | Extends indirect injection to non-text modalities; underexplored area |
| [Dissecting Adversarial Robustness of Multimodal LM Agents](https://arxiv.org/abs/2406.12814) | ICLR 2025 | Imperceptible pixel perturbations ; ARE framework decomposes robustness |
| [AdvAgent: Controllable Blackbox Red-teaming on Web Agents](https://arxiv.org/abs/2410.17401) | ICML 2025 | RL-trained adversarial prompter ; injects strings into invisible HTML fields|

---

### 1.3 Memory & RAG Poisoning

The attacker corrupts the agent's external memory or knowledge base, causing retrieval of malicious content at inference time.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [PoisonedRAG: Knowledge Corruption Attacks to Retrieval-Augmented Generation](https://arxiv.org/abs/2402.07867) | USENIX Security 2025 | Shows 5 poisoned documents among millions can achieve 90% attack success; alarming scalability |
| [AgentPoison: Red-teaming LLM Agents via Poisoning Memory or Knowledge Bases](https://arxiv.org/abs/2407.12784) | NeurIPS 2024 | Extends RAG poisoning to full agent pipelines; shows memory poisoning transfers across agent tasks |
| [Backdoored Retrievers for Prompt Injection Attacks on RAG](https://arxiv.org/abs/2410.14479) | arXiv 2024 | Targets the retriever component itself rather than the corpus; harder to detect than corpus poisoning |
| [Hidden in the Metadata: Stealth Poisoning Attacks on Multimodal Retrieval-Augmented Generation](https://arxiv.org/abs/2603.00172) | arXiv 2026 | Image-intact metadata-only poisoning ; bypasses query paraphrasing and consistency checks |

---

### 1.4 Tool & MCP Poisoning

The attacker compromises tools, plugins, or MCP servers that the agent calls, injecting malicious instructions through tool outputs or descriptions.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [ToolSword: Unveiling Safety Issues of LLMs in Tool Learning](https://arxiv.org/abs/2402.10753) | ACL 2024 | Identifies safety issues across three stages: tool selection, calling, and result handling; good taxonomy |
| [Compromising Agents via MCP](https://invariantlabs.ai/blog/mcp-security) | Invariant Labs 2025 | Practical demonstration of tool poisoning via MCP; covers cross-tool contamination and rug pulls |
| [LLM Platform Security: Applying a Systematic Evaluation Framework to OpenAI's ChatGPT Plugins](https://arxiv.org/abs/2307.09902) | AIES 2024 | Early plugin security analysis; now superseded by MCP-era work but useful for baseline comparison |

---

### 1.5 Backdoor Attacks

The attacker poisons training data or few-shot demonstrations so that a trigger at inference time causes malicious behavior.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Watch Out for Your Agents! Investigating Backdoor Threats to LLM-Based Agents](https://arxiv.org/abs/2402.11208) | NeurIPS 2024 | Systematic study of backdoor threats specific to agents; demonstrates attack via poisoned tool demonstrations |
| [BadAgent: Inserting and Activating Backdoor Attacks in LLM Agents](https://arxiv.org/abs/2406.03007) | arXiv 2024 | Shows backdoors survive fine-tuning; practical threat for fine-tuned agent deployments |
| [Rules File Backdoor](https://pillar.security/blog/the-rules-file-backdoor-ai-code-editors-under-attack) | Pillar Security 2025 | Real-world backdoor via poisoned IDE configuration files; demonstrates supply-chain attack surface |

---

### 1.6 Multi-Agent Propagation

In multi-agent systems, a compromised agent can spread malicious instructions to other agents through shared context, messages, or tool calls.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Prompt Infection: LLM-to-LLM Prompt Injection within Multi-Agent Systems](https://arxiv.org/abs/2410.07283) | arXiv 2025 | First paper to formalize cross-agent prompt injection propagation; shows exponential spread in large MAS |
| [PsySafe: Psychological-based Attack, Defense, and Evaluation of Multi-agent System Safety](https://arxiv.org/abs/2401.11401) | ACL 2024 | Unique angle: uses psychological manipulation to compromise agent personas; underexplored threat vector |
| [Evil Geniuses: Delving into the Safety of LLM-based Agents](https://arxiv.org/abs/2311.11855) | arXiv 2023 | Early multi-agent safety analysis; broad but surface-level by current standards |

---

## 2. Defenses

### 2.1 Input Filtering & Guardrails

| Paper / Tool | Venue | Commentary |
|-------|-------|------------|
| [NeMo Guardrails](https://arxiv.org/abs/2310.10501) | EMNLP 2023 | Programmable rule-based guardrails; flexible but bypassable via adaptive attacks |
| [Llama Guard](https://arxiv.org/abs/2312.06674) | arXiv 2023 | LLM-as-classifier for input/output safety; 6 safety categories; good baseline but not agent-specific |
| [ShieldAgent: Shielding Agents via Verifiable Safety Policy Reasoning](https://arxiv.org/abs/2502.17747) | ICML 2025 | Generates guardrail policies from documents; more flexible than rule-based systems |
| [Prompt Guard 2](https://huggingface.co/meta-llama/Llama-Prompt-Guard-2-86M) | Meta 2025 | Lightweight classifier for injection detection; fast but struggles with indirect/obfuscated injections |

---

### 2.2 Instruction Hierarchy

Enforcing that instructions from higher-privilege sources (system > developer > user > environment) cannot be overridden by lower-privilege ones.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Instructional Segment Embedding: Improving LLM Safety with Instruction Hierarchy](https://arxiv.org/abs/2404.13208) | ICLR 2025 | Adds segment embeddings to encode privilege levels; elegant approach but requires model retraining |
| [Rule-Based Rewards for Language Model Safety](https://cdn.openai.com/rule-based-rewards-for-language-model-safety.pdf) | OpenAI 2024 | RLHF-based approach to privilege-aware instruction following; hard to generalize beyond OpenAI's setup |

---

### 2.3 Sandboxing & Permission Control

| Paper / Tool | Venue | Commentary |
|-------|-------|------------|
| [ToolEmu: Identifying the Risks of LM Agents with an LM-Emulated Sandbox](https://arxiv.org/abs/2309.15817) | ICLR 2024 | LLM-emulated sandbox for identifying risky agent actions before real execution; false negative rate is a concern |
| [TrustAgent: Towards Safe and Trustworthy LLM-based Agents](https://arxiv.org/abs/2402.01586) | arXiv 2024 | Agent constitution approach to limit excessive agency; still relies on LLM self-regulation |

---

### 2.4 Multi-Agent Trust Protocols

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Securing Multi-Agent Systems](https://arxiv.org/abs/2504.16902) | arXiv 2026 | Systematic threat landscape of MAS; 193 threat items across 9 categories; evaluates 16 frameworks |
| [AutoDefense: Multi-Agent LLM Defense against Jailbreak Attacks](https://arxiv.org/abs/2403.04783) | arXiv 2024 | Uses a multi-agent pipeline to filter malicious outputs; adds latency overhead |

---

## 3. Benchmarks & Evaluation

| Benchmark | Venue | What it measures | Limitation |
|-----------|-------|-----------------|------------|
| [AgentDojo](https://arxiv.org/abs/2406.13352) | NeurIPS 2024 | Indirect injection success vs. task completion | Narrow scenario coverage |
| [R-Judge](https://arxiv.org/abs/2401.10019) | ACL 2024 | Agent safety risk awareness across 27 risk scenarios | Static scenarios; no multi-agent |
| [AgentHarm](https://arxiv.org/abs/2410.09024) | ICLR 2025 | Direct misuse by malicious users | Does not cover adversarial injection |
| [ASB (Agent Security Bench)](https://arxiv.org/abs/2410.02644) | ICLR 2025 | 10 attack types across 10 agents | Synthetic environments only |
| [AgentDoG](https://github.com/AI45Lab/AgentDoG) | arXiv 2025 | Trajectory-level safety evaluation with 3D taxonomy | New; limited third-party validation |
| [WASP](https://arxiv.org/abs/2504.18575) | arXiv 2025 | Web agent prompt injection | Web-only scope |
| [CVE-Bench](https://arxiv.org/abs/2503.17332) | ICML 2025 Spotlight | Agent offensive capability | Web app vulnerabilities only; measures attack capability |

---only

## 4. Tools & Frameworks

| Tool | Description |
|------|-------------|
| [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) | Programmable safety rails for LLM apps |
| [Invariant Labs Scanner](https://invariantlabs.ai) | MCP security scanning and monitoring |
| [AgentDoG](https://github.com/AI45Lab/AgentDoG) | Diagnostic guardrail framework with taxonomy-guided evaluation |
| [Garak](https://github.com/NVIDIA/garak) | LLM vulnerability scanner; some agent-specific probes |
| [PromptBench](https://github.com/microsoft/promptbench) | Robustness evaluation; useful baseline for injection testing |
| [AgentFuzz](https://www.usenix.org/conference/usenixsecurity25/presentation/liu-fengyu) | fuzzing framework for taint-style vulnerability detection; discovered  vulnerabilities (USENIX Security 2025) |

---

## Contributing

Contributions welcome! Please follow these guidelines:

1. **Format**: `[Paper Title](link) | Venue Year | One-line commentary`
2. **Commentary**: State what the paper contributes AND what it misses or assumes
3. **Placement**: Add to the most specific applicable category
4. **Quality bar**: Top-venue papers (ICLR/NeurIPS/ACL/USENIX/CCS/IEEE S&P) preferred; arXiv accepted if widely cited or fills a gap

Open a PR or issue to suggest additions.

---

## Maintainers

<!-- Add your name/GitHub handle here -->

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)
