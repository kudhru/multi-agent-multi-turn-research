# Research Survey: Multi-Turn Conversations & Multi-Agent Systems

A comprehensive survey of academic research and industry practices across **13 key dimensions** for two system paradigms: **multi-turn conversational AI** and **multi-agent AI systems**.

> Papers sourced from top-tier venues: NeurIPS, ICML, ICLR, ACL, EMNLP, NAACL, USENIX Security, IEEE S&P, CCS, SOSP, OSDI, USENIX ATC, ASPLOS, WWW, SIGKDD, SIGMOD, VLDB, ICSE, CHI, FAccT, AAAI, IJCAI, ACM Computing Surveys, TACL, and arXiv preprints from leading labs.

---

## Repository Structure

```
.
├── papers/                          # Per-dimension paper surveys
│   ├── 01_safety.md                 # Safety, adversarial attacks, alignment
│   ├── 02_task_success.md           # Task/goal achievement, benchmarks
│   ├── 03_compliance.md             # Regulatory compliance, policy adherence
│   ├── 04_efficiency.md             # Computational cost, serving efficiency
│   ├── 05_performance.md            # Quality metrics, evaluation frameworks
│   ├── 06_robustness.md             # OOD robustness, adversarial degradation
│   ├── 07_fairness_and_bias.md      # Demographic bias, fairness frameworks
│   ├── 08_scalability_and_reliability.md  # Scaling behavior, consistency
│   ├── 09_interpretability.md       # Explainability, transparency
│   ├── 10_human_ai_interaction.md   # Trust calibration, overreliance
│   ├── 11_hallucination_and_factuality.md  # Factual grounding, propagation
│   ├── 12_coordination_and_emergence.md    # Emergent coordination behaviors
│   └── 13_self_evolving_agents.md          # Self-improvement, alignment drift, misevolution risks
│
├── research_gaps/
│   └── summary.md                   # 18 prioritized open research problems
│
├── industry_practices/
│   └── summary.md                   # Best practices from Anthropic, OpenAI, Google, Meta, Microsoft
│
├── research_ideas/                  # Proposed research directions with feasibility analysis
│   ├── 01_safety_alignment_drift.md
│   ├── 02_bias_amplification_multi_turn.md
│   └── 03_stac_compositional_tool_safety.md
│
├── paper_quality_review/
│   └── flagged_papers.md            # Quality review: papers flagged for removal or correction
│
└── README.md                        # This file
```

---

## Dimensions Covered

For each dimension, each file covers:
- **Top 5 papers** (with title, authors, venue, year, URL, key findings, methodology, significance score)
- **Well-established findings** — results with strong, replicated evidence
- **Mixed / contradictory results** — findings with contested or inconsistent evidence
- **Research gaps** — open problems not yet adequately addressed
- **Industry best practices** — real-world approaches from leading AI organizations

---

## Quick Reference: Top Papers by Dimension

### Safety
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | Crescendo Multi-Turn Jailbreak | USENIX Security 2025 | 29–61% higher ASR than SOTA; succeeds against all frontier models |
| Multi-turn | CoSafe: Coreference Safety | EMNLP 2024 | First multi-turn coreference attack benchmark; up to 56% ASR |
| Multi-agent | Agent Smith: Infectious Jailbreak | ICML 2024 | 1 image → 1M agents jailbroken exponentially fast |
| Multi-agent | Secret Collusion via Steganography | NeurIPS 2024 | AI agents collude covertly; detection capability is asymmetrically disadvantaged |
| Multi-agent | AgentPoison: Memory Poisoning | NeurIPS 2024 | >80% ASR with <0.1% knowledge base poisoning rate |

### Task Success
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | WebArena | ICLR 2024 | GPT-4: 11.70% vs human: 78.24% on web tasks |
| Multi-turn | MINT | ICLR 2024 | RLHF/SIFT **hurts** multi-turn task performance |
| Multi-turn | tau-bench | arXiv 2024 | GPT-4o: <50% success; pass^8 reliability <25% |
| Multi-agent | AgentBench | ICLR 2024 | 8-env benchmark reveals massive commercial vs. open-source gap |
| Multi-agent | TheAgentCompany | ICLR 2025 | Best agent completes only 24% of real-world workplace tasks |

### Compliance
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | Constitutional AI | arXiv 2022 | Foundational RLAIF framework for rule-following in LLMs |
| Multi-turn | Rule Based Rewards | NeurIPS 2024 | Fine-grained RL reward signals for precise compliance control |
| Multi-agent | SEAgent MAC | arXiv 2026 | 0% privilege escalation attack success rate with ABAC enforcement |
| Multi-agent | COMPL-AI | arXiv 2024 | First EU AI Act compliance benchmark: 27 measurable criteria |

### Efficiency
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | PagedAttention (vLLM) | SOSP 2023 | 2–4x throughput improvement; now industry standard |
| Multi-turn | CachedAttention | USENIX ATC 2024 | 87% TTFT reduction, 70% cost reduction for multi-turn serving |
| Multi-turn | StreamingLLM | ICLR 2024 | 22.2x speedup; stable generation up to 4M tokens |
| Multi-agent | Cascaded Orchestration | arXiv 2024 | >94% cost reduction via small→large model escalation |

### Performance / Quality
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | MT-Bench + LLM-as-Judge | NeurIPS 2023 | GPT-4 judge achieves >80% agreement with humans; now the standard |
| Multi-turn | LongBench v2 | ACL 2025 | Frontier LLMs at 50–60% on 2M token tasks; far from saturated |
| Multi-agent | MAST: Why MAS Fail | arXiv 2025 | 14 failure modes (kappa=0.88) across 7 popular MAS frameworks |
| Multi-agent | Multiagent Debate | ICML 2024 | Improves factuality but doesn't consistently beat single-agent test-time compute |

### Robustness
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | LLMs Get Lost in Multi-Turn | arXiv 2025 | Average 39% performance drop; 200K conversations analyzed |
| Multi-agent | Adversarial Robustness of Multimodal LM Agents | ICLR 2025 | Up to 67% agent hijack success from imperceptible image perturbations |

### Fairness
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | Fairness Feedback Loops | FAccT 2024 | Synthetic data training amplifies bias across model generations |
| Multi-agent | Multi-Agent Debiasing with Evidence Retrieval | AAAI 2024 | +8% accuracy, -0.08 directional bias via multi-agent debiasing |

### Scalability & Reliability
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | Context Length Alone Hurts | EMNLP 2025 | Reasoning degrades even with 100% perfect retrieval |
| Multi-agent | MegaAgent | ACL 2025 | Successfully scaled to 590 agents |
| Multi-agent | Science of AI Agent Reliability | arXiv 2026 | 30–75% outcome consistency; predictability is the weakest dimension |

### Interpretability
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | CoT Is Not Explainability | Oxford 2025 | CoT is post-hoc rationalization, not causally faithful |
| Multi-agent | Language Grounded MARL | NeurIPS 2024 | Natural language grounding dramatically improves MAS interpretability |

### Hallucination & Factuality
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | Self Reflection for Hallucination Mitigation | EMNLP 2023 | 3-loop self-reflection steadily improves factuality across turns |
| Multi-agent | GovSim: Cooperate or Collapse | NeurIPS 2024 | Hallucinations about shared state cause collective system collapse |

### Coordination & Emergence
| System | Top Paper | Venue | Key Result |
|--------|-----------|-------|------------|
| Multi-turn | ConsistentChat: Skeleton-Guided Dialogue | EMNLP 2025 | Intent-flow skeletons dramatically improve multi-turn coherence |
| Multi-agent | Emergent Coordination in Multi-Agent LMs | arXiv 2025 | Confirmed genuine higher-order emergent coordination via information theory |
| Multi-agent | Game-Theoretic Lens on LLM-MAS | arXiv 2025 | LLM agents cooperate and exhibit fairness reasoning vs. Nash equilibria |

---

## Key Cross-Cutting Findings

### Well-Established Across All Dimensions
1. **Multi-turn attacks consistently outperform single-turn attacks** — conversation history degrades safety alignment.
2. **Standard NLP metrics (BLEU, ROUGE) are poor proxies** for multi-turn or multi-agent quality — task-specific or LLM-judge metrics are necessary.
3. **KV-cache optimization is the highest-impact efficiency lever** for both multi-turn serving and multi-agent systems.
4. **Single-turn performance does not predict multi-turn or multi-agent performance** — agent-specific evaluation is necessary.
5. **A single compromised agent in a multi-agent network can propagate adversarial behavior exponentially fast** (Agent Smith, ICML 2024).
6. **Deterministic access control can eliminate privilege escalation** in LLM agent systems when properly enforced at the tool level (SEAgent, 0% ASR).

### Critical Open Problems
1. Long-horizon evaluation benchmarks (50+ turns, 50+ steps) with ground-truth annotations.
2. Formal trust frameworks for heterogeneous multi-agent systems.
3. Faithful interpretability methods for multi-turn dialogue and multi-agent coordination.
4. Production-scale reliability metrics; current agents show 30–75% outcome consistency.
5. Real-time hallucination containment at agent boundaries.

---

## Methodology

- **Search coverage:** 4 parallel research agents each conducting 30–45 web searches across targeted academic venues and preprint servers.
- **Venue filter:** Top-tier CS conferences in AI, ML, NLP, security, systems, HCI, and databases (see venue list above).
- **Paper selection:** Top 5 per dimension per system type, prioritizing citation impact, methodological rigor, and novelty.
- **Last updated:** 2026-05-17

---

## Contributing

To add a paper or update findings, submit a pull request with the relevant file in `papers/`. Follow the existing format for consistency.
