# 🛡️ Awesome Agentic Security

[![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome)
[![GitHub stars](https://img.shields.io/github/stars/zhangxin-xd/awesome-agentic-security?style=flat&logo=github&color=yellow)](https://github.com/zhangxin-xd/awesome-agentic-security/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/zhangxin-xd/awesome-agentic-security?style=flat&logo=github&color=blue)](https://github.com/zhangxin-xd/awesome-agentic-security/network/members)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Last Updated](https://img.shields.io/badge/updated-Jun%202026-orange)](https://github.com/zhangxin-xd/awesome-agentic-security/commits/main)
[![Papers](https://img.shields.io/badge/papers-54-red)](https://github.com/zhangxin-xd/awesome-agentic-security)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/zhangxin-xd/awesome-agentic-security/pulls)
[![Scope](https://img.shields.io/badge/scope-agentic%20security-purple)](https://github.com/zhangxin-xd/awesome-agentic-security)

> A curated list of papers, benchmarks, tools, and resources on the **security of agentic AI systems** — organized by **attack entry point** with one-line notes on contribution and limitation.

---

## Why this list?

Most existing awesome-security lists are **paper graveyards** — long, flat, hard to navigate. This list is different:

- 📌 **Organized by attack entry point** — so you know *where* the threat enters
- 💬 **One sentence per entry** — what it contributed, what it left open
- 👥 **Useful for both researchers and engineers** — papers *and* tools side by side

**Scope:** Agentic AI systems (single- and multi-agent). We cover attacks against the agentic setting, defenses, benchmarks, and tools. We do **not** cover general LLM safety (jailbreaks with no agent context) or embodied/robotic safety.

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
| [Personal LLM Agents: Insights and Survey about the Capability, Efficiency and Security](https://arxiv.org/abs/2401.05459) | arXiv 2024 | On-device personal agent survey with dedicated security/privacy section; broad rather than deep on attack mechanisms |
| [Model Context Protocol (MCP): Landscape, Security Threats, and Future Research Directions](https://arxiv.org/abs/2503.23278) | ACM TOSEM 2025 | First systematic MCP security survey |
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
| [Imprompter: Tricking LLM Agents into Improper Tool Use](https://arxiv.org/abs/2410.14923) | arXiv 2024 (UCSD, Fernandes group) | Automatically generates obfuscated adversarial prompts that hijack production agents (Mistral LeChat, ChatGLM) to exfiltrate PII; ~80% end-to-end ASR; led to real CVE-style mitigation by Mistral |

---

### 1.2 Indirect Prompt Injection

Malicious instructions are embedded in content the agent retrieves from the environment (web pages, emails, documents, API responses).

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Not What You've Signed Up For: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injections](https://arxiv.org/abs/2302.12173) | AISec 2023 | The paper that named and formalized indirect prompt injection; foundational read |
| [InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated LLM Agents](https://arxiv.org/abs/2403.02691) | ACL Findings 2024 | ReAct-prompted GPT-4 vulnerable 24% of the time; single-turn only, superseded by AgentDojo for multi-step |
| [EIA: Environmental Injection Attack on Generalist Web Agents for Privacy Leakage](https://arxiv.org/abs/2409.11295) | ICLR 2025 | Invisible HTML form fields trick web agents into typing PII into attacker-controlled fields |
| [AgentDojo: A Dynamic Environment to Evaluate Attacks and Defenses for LLM Agents](https://arxiv.org/abs/2406.13352) | NeurIPS 2024 | Best current benchmark for indirect injection; realistic task environments but limited to web/email scenarios |
| [WASP: Benchmarking Web Agent Security Against Prompt Injection Attacks](https://arxiv.org/abs/2504.18575) | arXiv 2025 | Specifically targets web navigation agents; more realistic threat model than AgentDojo |
| [(Ab)using Images and Sounds for Indirect Instruction Injection in Multi-modal LLMs](https://arxiv.org/abs/2307.10490) | arXiv 2023 | Extends indirect injection to non-text modalities; underexplored area |
| [Dissecting Adversarial Robustness of Multimodal LM Agents](https://arxiv.org/abs/2406.12814) | ICLR 2025 | Imperceptible pixel perturbations ; ARE framework decomposes robustness |
| [AdvAgent: Controllable Blackbox Red-teaming on Web Agents](https://arxiv.org/abs/2410.17401) | ICML 2025 | RL-trained adversarial prompter ; injects strings into invisible HTML fields |

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
| [MCPTox: A Benchmark for Tool Poisoning Attack on Real-World MCP Servers](https://arxiv.org/abs/2508.14925) | AAAI 2026 | 45+ real-world MCP servers across 8 domains |
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
| [BadChain: Backdoor Chain-of-Thought Prompting for Large Language Models](https://arxiv.org/abs/2401.12242) | ICLR 2024 (UIUC, Bo Li group) | First backdoor against CoT prompting via poisoned demonstrations; 97% ASR on GPT-4 across 6 reasoning tasks; shuffling-based defenses fail |
| [DemonAgent: Dynamically Encrypted Multi-Backdoor Implantation Attack on LLM-based Agent](https://arxiv.org/abs/2502.12575) | EMNLP Findings 2025 | Decomposes backdoor into encrypted sub-fragments triggered cumulatively across the workflow; ~100% ASR with 0% detection rate; releases AgentBackdoorEval dataset |

---

### 1.6 Multi-Agent Propagation

In multi-agent systems, a compromised agent can spread malicious instructions to other agents through shared context, messages, or tool calls.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Prompt Infection: LLM-to-LLM Prompt Injection within Multi-Agent Systems](https://arxiv.org/abs/2410.07283) | arXiv 2025 | First paper to formalize cross-agent prompt injection propagation; shows exponential spread in large MAS |
| [Here Comes the AI Worm (Morris II)](https://arxiv.org/abs/2403.02817) | CCS 2025 | First self-replicating adversarial prompt against RAG-based GenAI ecosystems |
| [NetSafe: Exploring the Topological Safety of Multi-agent Networks](https://arxiv.org/abs/2410.15686) | ACL Findings 2025 | Identifies "Agent Hallucination" and "Aggregation Safety" phenomena |
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
| [Spotlighting: Defending Against Indirect Prompt Injection Attacks](https://arxiv.org/abs/2403.14720) | CAMLIS 2024 (Microsoft) | Datamarking/encoding/delimiting techniques to signal data provenance |
| [The Task Shield: Enforcing Task Alignment to Defend Against Indirect Prompt Injection in LLM Agents](https://arxiv.org/abs/2412.16682) | ACL 2025 | Task-alignment verification |
| [MELON: Provable Defense Against Indirect Prompt Injection Attacks in AI Agents](https://arxiv.org/abs/2502.05174) | ICML 2025 | Dual-execution detection — re-runs the agent with a masked user prompt and flags an attack if tool calls match; outperforms SOTA on AgentDojo; adds inference cost |
| [Prompt Guard 2](https://huggingface.co/meta-llama/Llama-Prompt-Guard-2-86M) | Meta 2025 | Lightweight classifier for injection detection; fast but struggles with indirect/obfuscated injections |


---

### 2.2 Instruction Hierarchy

Enforcing that instructions from higher-privilege sources (system > developer > user > environment) cannot be overridden by lower-privilege ones.

| Paper | Venue | Commentary |
|-------|-------|------------|
| [The Instruction Hierarchy: Training LLMs to Prioritize Privileged Instructions](https://arxiv.org/abs/2404.13208) | arXiv 2024 (OpenAI) | Defines a 4-level privilege hierarchy (system > developer > user > tool) and teaches it via SFT data augmentation |
| [StruQ: Defending Against Prompt Injection with Structured Queries](https://arxiv.org/abs/2402.06363) | USENIX Security 2025 | Structured prompt/data channels via reserved tokens + adversarial SFT |
| [Rule-Based Rewards for Language Model Safety](https://cdn.openai.com/rule-based-rewards-for-language-model-safety.pdf) | OpenAI 2024 | RLHF-based approach to privilege-aware instruction following; hard to generalize beyond OpenAI's setup |
| [SecAlign: Defending Against Prompt Injection with Preference Optimization](https://arxiv.org/abs/2410.05451) | CCS 2025 (UC Berkeley + Meta) | Trains LLMs via DPO on (clean, adversarial) preference pairs to prefer the intended instruction; <10% ASR even on attacks unseen during training; basis of open-source Meta-SecAlign-70B |

---

### 2.3 Sandboxing & Permission Control

| Paper / Tool | Venue | Commentary |
|-------|-------|------------|
| [ToolEmu: Identifying the Risks of LM Agents with an LM-Emulated Sandbox](https://arxiv.org/abs/2309.15817) | ICLR 2024 | LLM-emulated sandbox for identifying risky agent actions before real execution; false negative rate is a concern |
| [CaMeL: Defeating Prompt Injections by Design](https://arxiv.org/abs/2503.18813) | SaTML 2026 | Capability-based control/data-flow separation around the LLM via custom Python interpreter |
| [IsolateGPT: An Execution Isolation Architecture for LLM-Based Agentic Systems](https://arxiv.org/abs/2403.04960) | NDSS 2025 | Per-app isolation with spoke-and-hub orchestration + separate memory banks |
| [Progent: Programmable Privilege Control for LLM Agents](https://arxiv.org/abs/2504.11703) | arXiv 2025 | DSL for fine-grained tool-call policies with LLM-generated rules |
| [TrustAgent: Towards Safe and Trustworthy LLM-based Agents](https://arxiv.org/abs/2402.01586) | arXiv 2024 | Agent constitution approach to limit excessive agency; still relies on LLM self-regulation |

---

### 2.4 Multi-Agent Trust Protocols

| Paper | Venue | Commentary |
|-------|-------|------------|
| [Securing Multi-Agent Systems](https://arxiv.org/abs/2504.16902) | arXiv 2026 | Systematic threat landscape of MAS; 193 threat items across 9 categories; evaluates 16 frameworks |
| [G-Safeguard: A Topology-Guided Security Lens for LLM-MAS](https://arxiv.org/abs/2502.11127) | ACL 2025 | GNN-based anomaly detection on multi-agent utterance graphs + topological intervention |
| [AutoDefense: Multi-Agent LLM Defense against Jailbreak Attacks](https://arxiv.org/abs/2403.04783) | arXiv 2024 | Uses a multi-agent pipeline to filter malicious outputs; adds latency overhead |

---

## 3. Benchmarks & Evaluation

| Benchmark | Venue | What it measures | Limitation |
|-----------|-------|-----------------|------------|
| [AgentDojo](https://arxiv.org/abs/2406.13352) | NeurIPS 2024 | Indirect injection success vs. task completion | Narrow scenario coverage |
| [R-Judge](https://arxiv.org/abs/2401.10019) | EMNLP Findings 2024 | Agent safety risk awareness across 27 risk scenarios | Static scenarios; no multi-agent |
| [AgentHarm](https://arxiv.org/abs/2410.09024) | ICLR 2025 | Direct misuse by malicious users | Does not cover adversarial injection |
| [ASB (Agent Security Bench)](https://arxiv.org/abs/2410.02644) | ICLR 2025 | 10 attack types across 10 agents | Synthetic environments only |
| [AgentDoG](https://github.com/AI45Lab/AgentDoG) | arXiv 2025 | Trajectory-level safety evaluation with 3D taxonomy | New; limited third-party validation |
| [WASP](https://arxiv.org/abs/2504.18575) | arXiv 2025 | Web agent prompt injection | Web-only scope |
| [CVE-Bench](https://arxiv.org/abs/2503.17332) | ICML 2025 Spotlight | Agent offensive capability | Web app vulnerabilities only; measures attack capability |
| [WASP](https://arxiv.org/abs/2504.18575) | NeurIPS 2025 D&B (Meta FAIR) | Realistic end-to-end web-agent prompt injection benchmark | Attacker constrained to plausible site-user capabilities; only web tasks |

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
