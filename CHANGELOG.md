# Changelog

All additions and rejections are logged here. Most recent entries appear first.

---
## 2026-09-01

### Added (28 papers, multi-agent security batch update)

Sourced from a curated multi-agent-security annotation table; every paper screened against the inclusion criteria in MAINTENANCE.md (agentic scope, substantive contribution, experimental support, venue/citation/gap-filling).

#### §0 Surveys & Position Papers
- [Open Challenges in Multi-Agent Security](https://arxiv.org/abs/2505.02077) -> §0 | defines MASEC as a field; 9 threat classes, 7 attack axes, 3-layer governance
- [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/abs/2506.01245) -> §0 | formal argument that compositional (single-agent) security fails in MAS
- [Architecture Matters for Multi-Agent Security](https://arxiv.org/abs/2604.23459) -> §0 | ICML 2026; attack success varies up to 3.8x across topologies, no universally optimal architecture
- [Seven Security Challenges in Cross-domain Multi-Agent LLM Systems](https://arxiv.org/abs/2505.23847) -> §0 | npj AI (Nature family); seven cross-domain challenges incl. collusion, conflict-of-interest

#### §1.6 Multi-Agent Propagation
- [MultiAgent Collaboration Attack](https://arxiv.org/abs/2406.14711) -> §1.6 | Findings of EMNLP 2024; adversarial agent degrades debate accuracy
- [Flooding Spread of Manipulated Knowledge](https://arxiv.org/abs/2407.07791) -> §1.6 | knowledge manipulation propagates through agent communities
- [CORBA](https://arxiv.org/abs/2502.14529) -> §1.6 | contagious recursive blocking with theoretical propagation guarantees; AutoGen + Camel
- [Agents Under Siege](https://arxiv.org/abs/2504.00218) -> §1.6 | ACL 2025; max-flow/min-cost attack-path optimization, topology-agnostic ASR
- [Amplified Vulnerabilities (MAD jailbreak)](https://arxiv.org/abs/2504.16489) -> §1.6 | debate systems inherently more fragile than single agents
- [Secret Collusion among AI Agents](https://arxiv.org/abs/2402.07510) -> §1.6 | NeurIPS 2024; foundational steganographic collusion formalization
- [Red-Teaming via Communication Attacks (AiTM)](https://arxiv.org/abs/2502.14847) -> §1.6 | Findings of ACL 2025; Agent-in-the-Middle on the message channel
- [Tipping the Dominos: Topology-Aware Multi-Hop Attacks on LLM-Based Multi-Agent Systems](https://arxiv.org/abs/2512.04129) -> §1.6 | 5 topologies x 3 frameworks; 40-78% ASR swing
- [Topology Matters: Memory Leakage](https://arxiv.org/abs/2512.04668) -> §1.6 | Findings of ACL 2026; fully-connected graphs maximize memory leakage

#### §2.4 Multi-Agent Trust Protocols
- [Breaking and Fixing Defenses Against Control-Flow Hijacking](https://arxiv.org/abs/2510.17276) -> §2.4 | ICLR 2026; breaks existing MAS control-flow defenses then fixes them
- [On the Resilience of MAS with Faulty Agents](https://arxiv.org/abs/2408.00989) -> §2.4 | hierarchical structures most resilient (5.5% vs 10.5%)
- [Multi-Agent Security Tax](https://arxiv.org/abs/2502.19145) -> §2.4 | AAAI 2025; direct security-utility tradeoff evidence
- [SAC: Robust MA-LLMs under Byzantine Faults](https://arxiv.org/abs/2605.09076) -> §2.4 | Byzantine-fault-tolerance complement to prompt-injection framing
- [CP-WBFT](https://arxiv.org/abs/2511.10400) -> §2.4 | AAAI 2025; systematic 6-topology x 7-node BFT evaluation
- [AgentXposed (Who's the Mole?)](https://arxiv.org/abs/2507.04724) -> §2.4 | detection across 3 structures x 4 covert attacks
- [INFA-Guard](https://arxiv.org/abs/2601.14667) -> §2.4 | treats infected benign agents as a distinct threat class; ~33% ASR reduction
- [SentinelNet](https://arxiv.org/abs/2510.16219) -> §2.4 | WWW 2026; credit-based dynamic threat detection
- [SentinelAgent](https://arxiv.org/abs/2505.24201) -> §2.4 | LLM-as-judge graph anomaly detection (G-Safeguard/BlindGuard trilogy)
- [Don't Trust Stubborn Neighbors](https://arxiv.org/abs/2603.15809) -> §2.4 | Friedkin-Johnsen social model for agentic-network security
- [A-Trust](https://arxiv.org/abs/2506.02546) -> §2.4 | attention-based trust via Grice's cooperative principle
- [NARCBench (collusion detection)](https://arxiv.org/abs/2604.01151) -> §2.4 | first activation-level multi-agent collusion detection
- [AgentSafe](https://arxiv.org/abs/2503.04392) -> §2.4 | hierarchical data management; Cooperative Safety Index

#### §3 Benchmarks & Evaluation
- [TAMAS](https://arxiv.org/abs/2511.05269) -> §3 | ACL 2026; adversarial risks across multi-agent configurations
- [PEAR](https://arxiv.org/abs/2510.07505) -> §3 | Findings of EACL 2026; planner-executor robustness

### Fixed (sources / duplicates)
- **G-Safeguard**: verified ACL 2025 main (long, 2025.acl-long.359) — already correct, no change
- **Morris II**: verified CCS 2025 (ACM, 10.1145/3719027.3765196) — already correct, no change
- **BlindGuard**: venue ACL 2026 -> arXiv 2025 (no proceedings record; arXiv 2508.08127)
- **Prompt Infection**: venue arXiv 2025 -> ESORICS 2025 Workshop (Springer 10.1007/978-3-032-16092-8_28)
- **AutoDefense**: venue arXiv 2024 -> NeurIPS 2024 Workshop
- **WASP**: venue arXiv 2025 -> NeurIPS 2025 D&B (§1.2); removed duplicate WASP row in §3
- **Evil Geniuses**: removed duplicate row in §0 (kept §1.6 entry)

### Considered but Rejected
- [MAST — Why Do Multi-Agent Systems Fail?](https://arxiv.org/abs/2503.13657) | reliability/failure taxonomy, not security scope
- [TraceAegis](https://arxiv.org/abs/2510.11203) | single-agent execution-trace anomaly detection, not inter-agent MAS security
- [Understanding Information Propagation Effects of Communication Topologies](https://arxiv.org/abs/2505.23352) | topology-utility study, not a security contribution
- MAEBE (arXiv:2506.03053) | emergent moral-drift / alignment framing, not attack/defense/benchmark

---

## 2026-06-29

### Added (6 papers, batch update)

#### §1.1 Direct Prompt Injection
- [BrowserART](https://arxiv.org/abs/2410.13886) → §1.1 | 100 browser harmful behaviors; GPT-4o attempts 98/100 as browser agent
  - Source: ICLR 2025 (Scale AI Red Team + CMU, Zico Kolter / Matt Fredrikson)
  - Reason: Top venue ICLR; landmark result that refusal training doesn't transfer to agentic contexts; widely cited by OS-Harm, WebGuard, HarmonyGuard

#### §1.3 Memory & RAG Poisoning
- [Phantom](https://arxiv.org/abs/2405.20485) → §1.3 | Single-document trigger backdoor for RAG; enables DoS/privacy/harmful outputs on trigger
  - Source: ACM TAIP 2026 (Northeastern + Google DeepMind, Alina Oprea / Milad Nasr / Choquette-Choo)
  - Reason: Journal + industry-heavyweight authors; complements PoisonedRAG (multi-doc) and AgentPoison (embedding-optimized) with a trigger-conditioned single-doc angle

#### §2.1 Input Filtering & Guardrails
- [GuardAgent](https://arxiv.org/abs/2406.09187) → §2.1 | First guard-agent-safeguards-agent framework; >98% and 83% guardrail accuracy on healthcare and web benchmarks
  - Source: ICML 2025 (UChicago + Berkeley, Bo Li / Dawn Song)
  - Reason: Top venue ICML; pioneers "meta-agent as guardrail" paradigm; also introduces EICU-AC and Mind2Web-SC benchmarks

#### §2.4 Multi-Agent Trust Protocols
- [BlindGuard](https://arxiv.org/abs/2508.08127) → §2.4 | Unsupervised MAS defense; detects PI/TA/MA without labels
  - Source: ACL 2026 (Jilin University + Griffith + UNSW)
  - Reason: Top venue ACL; complementary to G-Safeguard (supervised) — enables practical deployment where labeled malicious traces are unavailable

#### §3 Benchmarks & Evaluation
- [ST-WebAgentBench](https://arxiv.org/abs/2410.06703) → §3 | 375 enterprise tasks × 3,057 policies; new Completion under Policy (CuP) metric
  - Source: ICLR 2026 (IBM Research Haifa)
  - Reason: Top venue ICLR; complements WASP (Meta) with enterprise-focused, policy-heavy evaluation; introduces widely-adopted CuP metric

#### §4 Tools & Frameworks
- [LlamaFirewall](https://arxiv.org/abs/2505.03574) → §4 | Meta's open-source three-layer agent guardrail (PromptGuard 2 + AlignmentCheck + CodeShield); AgentDojo ASR 17.6% → 1.7%
  - Source: Meta AI 2025
  - Reason: Industry-grade open-source release from Meta; already the reference framework for AgentDojo defenses; LangChain integration; complements Invariant's MCP-Scan

### Considered but Rejected

- [BadRAG (arXiv 2406.00083)](https://arxiv.org/abs/2406.00083) | Reason: Solid trigger-based RAG backdoor, but Phantom (higher venue + stronger single-doc claim) covers similar territory more compactly
- [AutoDefense duplicate check: keep as-is](#) | Reason: N/A
- [BrowserGym as a tool](#) | Reason: General-purpose web agent framework, not a security tool; belongs in agent-capability lists

---
## 2026-06-22

### Added (4 papers, batch update)

#### §1.4 Tool & MCP Poisoning
- [MPMA](https://arxiv.org/abs/2505.11154) → §1.4 | First MCP preference manipulation attack; GAPMA (genetic algorithm variant) achieves 100% ASR
  - Source: AAAI 2026
  - Reason: Top venue AAAI; introduces economically motivated attack angle (attackers profit from paid MCP services); complements MCPTox by targeting tool selection rather than execution

#### §1.6 Multi-Agent Propagation
- [Agent Smith](https://arxiv.org/abs/2402.08567) → §1.6 | Single adversarial image spreads exponentially to 1M+ multimodal agents; coined "infectious jailbreak"
  - Source: ICML 2024 (Sea AI Lab, Min Lin's group)
  - Reason: Top venue ICML; 250+ citations; naming authority — "infectious jailbreak" is now a standard research term followed by Cowpox, INFA-Guard, and related defense work

#### §2.3 Sandboxing & Permission Control
- [ETDI](https://arxiv.org/abs/2506.01333) → §2.3 | Enhanced Tool Definition Interface with cryptographic signing + immutable versioning + OAuth 2.0 scopes for MCP
  - Source: arXiv 2025 (AWS + Intuit + OWASP practitioners)
  - Reason: Industry-grade proposal directly countering rug pull and tool squatting; cited by MCP-Guard, MCPSECBENCH, and the SoK MCP survey; fills the MCP defense gap in §2.3

#### §4 Tools & Frameworks
- [MCP-Scan](https://github.com/invariantlabs-ai/mcp-scan) → §4 | Open-source MCP security scanner from Invariant Labs (Snyk acquired 2025); 2,000+ GitHub stars
  - Source: Invariant Labs (ETH Zurich spin-off, co-founded by Tramèr et al.)
  - Reason: Most widely adopted MCP scanner; Apache-2.0; supports major MCP clients (Claude Desktop, Cursor, Windsurf); Snyk acquisition validates industry impact

### Considered but Rejected

- [MCP-Guard (arXiv 2508.10991)](https://arxiv.org/abs/2508.10991) | Reason: Solid multi-stage MCP defense but overlaps significantly with ETDI on threat model; defer until published at venue
- [GuardAgent (arXiv 2406.09187)](https://arxiv.org/abs/2406.09187) | Reason: Interesting "guard agent guards agent" concept but currently no top-venue acceptance; revisit if published at ACL/NeurIPS

## 2026-06-15

### Added (3 papers, batch update)

#### §1.5 Backdoor Attacks
- [BadChain](https://arxiv.org/abs/2401.12242) → §1.5 | First backdoor attack against CoT prompting via demonstration poisoning; 97% ASR on GPT-4
  - Source: ICLR 2024 (UIUC + UW, Bo Li / Radha Poovendran groups)
  - Reason: Top venue ICLR; foundational CoT-backdoor work; §1.5 was severely underpopulated with only 2 entries

- [DemonAgent](https://arxiv.org/abs/2502.12575) → §1.5 | Dynamically encrypted multi-backdoor implantation; ~100% ASR with 0% detection rate; releases AgentBackdoorEval dataset
  - Source: EMNLP Findings 2025
  - Reason: Top venue; demonstrates that current safety audits fail against multi-fragment backdoors; provides accompanying benchmark

#### §2.2 Instruction Hierarchy
- [SecAlign](https://arxiv.org/abs/2410.05451) → §2.2 | DPO-based training on adversarial preference pairs; <10% ASR on unseen attacks; basis of open-source Meta-SecAlign-70B
  - Source: CCS 2025 (UC Berkeley + Meta, Sizhe Chen / David Wagner / Chuan Guo)
  - Reason: Top-tier security venue CCS; preference-optimization paradigm complementary to Instruction Hierarchy and StruQ; powering Meta's open-source secure LLM release

### Considered but Rejected

- [AutoBackdoor (arXiv 2511.16709)](https://arxiv.org/abs/2511.16709) | Reason: Automating backdoor attacks via LLM agents is novel angle but not yet at a top venue and citation count low
- [SkillTrojan (arXiv 2604.06811)](https://arxiv.org/abs/2604.06811) | Reason: Skill-based agent backdoor; interesting niche but currently no venue acceptance

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
