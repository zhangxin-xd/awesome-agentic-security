# Changelog

All additions and rejections are logged here. Most recent entries appear first.

---
## 2026-06-08

### Added (3 papers, batch update)

#### §1.1 Direct Prompt Injection
- [Imprompter](https://arxiv.org/abs/2410.14923) → §1.1 | Auto-generated obfuscated prompts that hijack production agents to exfiltrate PII; ~80% end-to-end ASR
  - Source: arXiv 2024 (UCSD, Earlence Fernandes group) / imprompter.ai
  - Reason: High-impact attack with confirmed real-world mitigation by Mistral; widely cited by SecAlign, WASP, VIGIL; covered by Wired and 404 Media [high-impact, industry-mitigated]

#### §2.1 Input Filtering & Guardrails
- [MELON](https://arxiv.org/abs/2502.05174) → §2.1 | Masked re-Execution and TooL comparisON; outperforms SOTA on AgentDojo
  - Source: ICML 2025 (UCSB)
  - Reason: Top venue ICML; new detection paradigm orthogonal to Spotlighting/Task Shield (execution-level, not input-level)

#### §3 Benchmarks & Evaluation
- [WASP](https://arxiv.org/abs/2504.18575) → §3 | End-to-end web-agent security benchmark with realistic adversary model
  - Source: NeurIPS 2025 Datasets & Benchmarks Track (Meta FAIR)
  - Reason: Top venue NeurIPS D&B; addresses AgentDojo's limitation on web-specific multi-step adversarial scenarios; standard adversary-constrained setup

### Considered but Rejected

- [Breaking Agents (Zhang et al., arXiv 2024)](https://arxiv.org/abs/2407.20859) | Reason: Solid work on malfunction amplification, but overlaps with Watch Out for Your Agents (already in §1.5) on backdoor-style triggers
- [ToolTweak (arXiv 2510.02554)](https://arxiv.org/abs/2510.02554) | Reason: Tool selection attack, but not yet at venue; defer until citation count or top-venue acceptance

## 2026-05-25

### Added (15 papers, batch update — agent safety classics)

#### §0 Surveys & Position Papers
- [Personal LLM Agents Survey](https://arxiv.org/abs/2401.05459) → §0 | On-device personal agent survey with dedicated security/privacy section; broad rather than deep on attack mechanisms
  - Source: arXiv 2024 / highly cited (500+)
  - Reason: Representative survey for the personal/edge agent dimension; existing §0 entries are all attack-focused surveys

- [MCP Landscape & Security Survey](https://arxiv.org/abs/2503.23278) → §0 | First systematic MCP security survey; 4 attacker types × lifecycle threats + real CVE case studies
  - Source: ACM TOSEM 2025
  - Reason: Journal venue; the only systematic MCP security survey; fills the MCP dimension gap in §0

#### §1.2 Indirect Prompt Injection
- [InjecAgent](https://arxiv.org/abs/2403.02691) → §1.2 | 1,054 cases × 17 user tools × 62 attacker tools; ReAct GPT-4 fails 24%
  - Source: ACL Findings 2024 (UIUC, Daniel Kang)
  - Reason: The most important IPI benchmark before AgentDojo; 200+ citations; standard comparison baseline for follow-up defense work

- [EIA](https://arxiv.org/abs/2409.11295) → §1.2 | Invisible HTML form fields steal PII; 70% ASR on SeeAct
  - Source: ICLR 2025
  - Reason: Top venue ICLR; landmark work on web agent privacy leakage; the hidden HTML attack vector was missing from the README

#### §1.4 Tool & MCP Poisoning
- [MCPTox](https://arxiv.org/abs/2508.14925) → §1.4 | 45+ real MCP servers across 8 domains; >60% ASR on o1-mini/DeepSeek-R1
  - Source: AAAI 2026
  - Reason: Top venue AAAI; first TPA benchmark on real (not simulated) MCP servers; §1.4 was severely underpopulated

#### §1.6 Multi-Agent Propagation
- [Here Comes the AI Worm (Morris II)](https://arxiv.org/abs/2403.02817) → §1.6 | First self-replicating adversarial prompt against RAG-based GenAI ecosystems
  - Source: CCS 2025 (Cornell Tech + Technion, Nassi et al.)
  - Reason: Top-tier security venue CCS; naming authority ("Morris II" is now the de facto community term); extensive coverage in WIRED and other media

- [NetSafe](https://arxiv.org/abs/2410.15686) → §1.6 | Topological analysis of MAS safety; star topology degrades 29.7%
  - Source: ACL Findings 2025
  - Reason: Top venue; complements Prompt Infection with a topological perspective

#### §2.1 Input Filtering & Guardrails
- [Spotlighting](https://arxiv.org/abs/2403.14720) → §2.1 | Datamarking/encoding/delimiting; >50% → <2% ASR on basic attacks
  - Source: CAMLIS 2024 (Microsoft)
  - Reason: Microsoft industry practice; 100+ citations; established AgentDojo baseline

- [Task Shield](https://arxiv.org/abs/2412.16682) → §2.1 | Task-alignment verification; 2.07% ASR with 69.79% utility on AgentDojo
  - Source: ACL 2025
  - Reason: Top venue ACL; complements CaMeL with the "user intent alignment" defense perspective

#### §2.2 Instruction Hierarchy
- [StruQ](https://arxiv.org/abs/2402.06363) → §2.2 | Structured prompt/data channels + adversarial SFT; <2% ASR
  - Source: USENIX Security 2025 (UC Berkeley, Wagner group)
  - Reason: Top-tier security venue USENIX; training-time defense paradigm on par with Instruction Hierarchy

#### §2.3 Sandboxing & Permission Control
- [CaMeL](https://arxiv.org/abs/2503.18813) → §2.3 | Capability-based control/data-flow separation; 77% AgentDojo tasks with provable security
  - Source: SaTML 2026 (Tramèr/Carlini, Google DeepMind + ETH)
  - Reason: Tramèr/Carlini heavyweight team; capability-based defense is a paradigm-shifting work [early, high-attention]

- [IsolateGPT](https://arxiv.org/abs/2403.04960) → §2.3 | Per-app isolation with spoke-and-hub; <30% overhead on 75% queries
  - Source: NDSS 2025
  - Reason: Top-tier security venue NDSS; first complete LLM agent isolation architecture

- [Progent](https://arxiv.org/abs/2504.11703) → §2.3 | DSL for tool-call policies; ASR to 0% on AgentDojo/ASB/AgentPoison
  - Source: arXiv 2025 (UC Berkeley, Dawn Song group)
  - Reason: Dawn Song's team; 0% ASR on three benchmarks; strong community attention [early, high-attention]

#### §2.4 Multi-Agent Trust Protocols
- [G-Safeguard](https://arxiv.org/abs/2502.11127) → §2.4 | GNN-based anomaly detection on MAS utterance graphs; recovers 40%+ utility
  - Source: ACL 2025
  - Reason: Top venue; §2.4 had only 2 entries — clear gap; GNN-based MAS defense is a new paradigm

### Fixed (corrections to existing README entries)

- §2.2: arXiv 2404.13208 title corrected from "Instructional Segment Embedding" to the actual paper by Wallace et al., **"The Instruction Hierarchy: Training LLMs to Prioritize Privileged Instructions"** (OpenAI 2024)
  - Reason: Verified the actual paper behind the arXiv ID; ISE is a different paper (arXiv 2410.09102)

- §3: R-Judge venue corrected from "ACL 2024" to "EMNLP Findings 2024"
  - Reason: Cross-checked ACL Anthology and confirmed the actual publication venue

- §3: Removed separator typo `---only` → `---`

### Considered but Rejected

- [Universal and Transferable Adversarial Attacks on Aligned LMs (GCG)](https://arxiv.org/abs/2307.15043) | Reason: Pure LLM jailbreak, no agentic scenario (no tools, memory, or multi-turn)
- [Tensor Trust (Toyer et al., ICLR 2024)](https://arxiv.org/abs/2311.01011) | Reason: Prompt extraction/hijacking benchmark, but the setting is a single-turn dialogue game — not an agent
- [AgentBench (Liu et al., ICLR 2024)](https://arxiv.org/abs/2308.03688) | Reason: Capability benchmark, not a safety benchmark

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

针对 LLM agent 污点漏洞的模糊测试工具，实战价值高

---
