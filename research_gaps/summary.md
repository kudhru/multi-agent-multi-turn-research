# Research Gaps: Multi-Turn Conversations & Multi-Agent Systems

A synthesis of open problems across all measured dimensions. Gaps are categorized by urgency and cross-cutting scope.

---

## TIER 1: Critical Gaps (High Impact, Widely Acknowledged, Practically Blocking)

### 1. Long-Horizon Evaluation Benchmarks
- **Problem:** Most multi-turn benchmarks cap at 5–10 turns. Most multi-agent benchmarks test tasks requiring <20 steps. Real-world deployments involve hundreds of turns and dozens of steps.
- **Dimensions affected:** Safety, Task Success, Performance, Robustness, Reliability, Scalability
- **Current best:** WebArena (12 actions avg), tau-bench (5–10 turns), AgentBench (8 envs)
- **What's missing:** Benchmarks with 50+ turns/steps, interleaved topic changes, mid-conversation goal shifts, and long-horizon factual consistency evaluation.

### 2. Standardized Multi-Turn Safety Evaluation Protocol
- **Problem:** No agreed-upon protocol for evaluating safety across multi-turn conversations. Existing benchmarks (MultiBreak, CoSafe) vary in turn count, topic distribution, attack diversity, and metrics.
- **Dimensions affected:** Safety, Compliance
- **What's missing:** A unified benchmark with multi-turn adversarial scenarios that mirrors real-world attack diversity, replicable across research groups.

### 3. Formal Trust Frameworks for Multi-Agent Systems
- **Problem:** How trust is established, delegated, revoked, and verified between heterogeneous agents (including across organizational boundaries) lacks both theoretical grounding and practical standardization.
- **Dimensions affected:** Safety, Compliance, Coordination
- **What's missing:** Composable trust protocols, cryptographic agent identity standards, cross-trust-boundary prompt injection defenses.

### 4. Multi-Agent Compliance Benchmarks
- **Problem:** No standardized benchmark for multi-agent compliance evaluation equivalent to tau-bench or AgentBench for task success. The field lacks a compliance leaderboard.
- **Dimensions affected:** Compliance, Safety
- **What's missing:** Benchmark measuring policy adherence in multi-step agent workflows across domains (healthcare, finance, legal).

### 5. Production-Scale Reliability Metrics
- **Problem:** Outcome consistency ranges 30–75% across state-of-the-art agents. Predictability (the ability to distinguish correct from incorrect predictions) is the weakest reliability dimension.
- **Dimensions affected:** Reliability, Scalability
- **What's missing:** Standardized reliability benchmarks for LLM-based multi-agent systems; quantitative models predicting multi-agent reliability from component agent reliability.

---

## TIER 2: Significant Gaps (Well-Identified, Early-Stage Research)

### 6. Hallucination Containment at Agent Boundaries
- **Problem:** A hallucinated fact from one agent is treated as ground truth by downstream agents, creating a propagation cycle. No principled methods for hallucination containment at agent boundaries exist.
- **Dimensions affected:** Hallucination, Reliability, Safety
- **Current best:** AgentHallu (attribution benchmark, 2025), GovSim (collapse demonstration, NeurIPS 2024)
- **What's missing:** Runtime hallucination detection and quarantine at agent handoff points.

### 7. Long-Horizon Alignment Degradation
- **Problem:** Safety alignment in LLMs is "shallow" — it primarily gates initial output tokens. Alignment degradation across hundreds of turns (persistent user sessions) is virtually unstudied.
- **Dimensions affected:** Safety, Compliance, Robustness
- **What's missing:** Empirical studies of alignment over 100+ turns; personalization-induced safety relaxation.

### 8. Faithful Interpretability for Multi-Turn and Multi-Agent Systems
- **Problem:** Chain-of-thought explanations are post-hoc rationalizations, not causally linked to the actual decision. No faithful interpretability methods exist for either multi-turn conversational dynamics or multi-agent coordination.
- **Dimensions affected:** Interpretability, Human-AI Interaction
- **What's missing:** Turn-by-turn explanation attribution; causal interpretability methods for multi-agent information flow; emergent behavior interpretability frameworks.

### 9. Fairness-Specific Evaluation in Multi-Turn and Multi-Agent Settings
- **Problem:** Demographic biases amplify in multi-turn dialogue through compounding contextual assumptions. No benchmarks exist specifically for measuring demographic bias across turns.
- **Dimensions affected:** Fairness, Compliance
- **What's missing:** Multi-turn fairness benchmarks, intersectional bias evaluation in MAS, longitudinal fairness tracking.

### 10. Trust Calibration in Conversational AI
- **Problem:** Multi-turn dialogue accumulates user trust in ways that are difficult to reset when AI makes errors. Users systematically over-rely on LLMs due to their human-like conversational qualities.
- **Dimensions affected:** Human-AI Interaction, Reliability
- **What's missing:** Longitudinal trust dynamics studies; standardized trust calibration metrics; trust repair mechanisms after AI errors.

### 11. Cross-Organizational Multi-Agent Security
- **Problem:** Agents from different organizations interacting raises seven unsolved challenges: policy conflicts, identity verification, cross-trust-boundary prompt injection, data sovereignty, audit trail ownership, compliance jurisdiction, and incident attribution.
- **Dimensions affected:** Safety, Compliance, Coordination
- **What's missing:** Standards for cross-organizational agent interaction; Agent-to-Agent (A2A) security protocols beyond the current draft standard.

---

## TIER 3: Emerging Gaps (Recently Identified, Nascent Research)

### 12. Sequential Tool Attack Chaining (STAC)
- **Problem:** Individually safe tool calls can chain into collectively harmful outcomes. No dedicated threat models or defenses for STAC exist.
- **Dimensions affected:** Safety, Compliance
- **Reference:** Emerging from agent security audits (Palo Alto Unit 42, 2025).

### 13. Near-Miss Policy Failures Detection
- **Problem:** Latent policy violations that didn't result in visible harm but indicate compliance risk — near-miss events — are essentially unstudied in agentic settings.
- **Dimensions affected:** Compliance, Safety
- **Reference:** arXiv:2603.29665

### 14. Multi-Agent Scaling Laws
- **Problem:** No empirical scaling laws analogous to neural network scaling laws exist for multi-agent systems. Optimal agent count for given task complexity is unknown.
- **Dimensions affected:** Scalability, Performance
- **What's missing:** Systematic study of performance and coordination quality as agent count scales from 2 to 1000+.

### 15. Multimodal Multi-Turn Safety
- **Problem:** Multi-turn attacks exploiting interleaved image/audio/code across turns are nascent. SafeMT (arXiv 2025) is an early attempt but the space is largely uncharted.
- **Dimensions affected:** Safety, Robustness

### 16. Privacy-Preserving Multi-Agent Computation
- **Problem:** How to enable agents to collaborate on sensitive tasks (healthcare, legal, financial) without leaking private information through shared communication channels or shared memory.
- **Dimensions affected:** Compliance, Safety

### 17. Coordination Recovery After Intent Mismatch
- **Problem:** Once an intent mismatch occurs in multi-turn dialogue, LLMs rarely recover coordination even with explicit correction attempts. No dedicated recovery mechanisms exist.
- **Dimensions affected:** Coordination, Reliability, Task Success

### 18. Benchmark Contamination and Reward Hacking Resistance
- **Problem:** SWE-bench and other top agentic benchmarks have been shown to be vulnerable to reward hacking (Berkeley/RDI, April 2026). Benchmark reliability in rapidly evolving agentic evaluation is contested.
- **Dimensions affected:** Task Success, Performance
- **What's missing:** Contamination-resistant agentic benchmarks; adversarial benchmark validation protocols.

---

## Cross-Cutting Research Gaps Summary

| Gap | Multi-Turn | Multi-Agent | Urgency |
|-----|-----------|-------------|---------|
| Long-horizon benchmarks (50+ turns/steps) | ✓ | ✓ | Critical |
| Multi-turn safety evaluation standard | ✓ | ✓ | Critical |
| Formal trust frameworks for agents | — | ✓ | Critical |
| Multi-agent compliance benchmarks | — | ✓ | Critical |
| Production-scale reliability metrics | ✓ | ✓ | Critical |
| Hallucination containment at boundaries | ✓ | ✓ | Significant |
| Long-horizon alignment degradation | ✓ | — | Significant |
| Faithful interpretability methods | ✓ | ✓ | Significant |
| Multi-turn fairness benchmarks | ✓ | ✓ | Significant |
| Trust calibration at scale | ✓ | ✓ | Significant |
| Cross-organizational agent security | — | ✓ | Significant |
| STAC attacks and defenses | — | ✓ | Emerging |
| Near-miss policy failure detection | ✓ | ✓ | Emerging |
| Multi-agent scaling laws | — | ✓ | Emerging |
| Multimodal multi-turn safety | ✓ | ✓ | Emerging |
| Privacy-preserving multi-agent computation | — | ✓ | Emerging |
| Coordination recovery mechanisms | ✓ | ✓ | Emerging |
| Benchmark contamination resistance | ✓ | ✓ | Emerging |

---

*Last updated: 2026-05-17*
