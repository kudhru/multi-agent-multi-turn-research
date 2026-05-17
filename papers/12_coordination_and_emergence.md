# Coordination & Emergent Behavior in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** NeurIPS, ACL, EMNLP, ACM Computing Surveys, arXiv

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | A Survey on Recent Advances in LLM-Based Multi-Turn Dialogue Systems | Multiple authors | ACM Computing Surveys | 2024 | https://dl.acm.org/doi/10.1145/3771090 |
| 2 | Building Skeleton-Guided Consistent Multi-Turn Dialogues (ConsistentChat) | Multiple authors | EMNLP 2025 | 2025 | https://aclanthology.org/2025.emnlp-main.424.pdf |
| 3 | Intent Mismatch Causes LLMs to Get Lost in Multi-Turn Conversation | Multiple authors | arXiv 2026 | 2026 | https://arxiv.org/html/2602.07338v1 |
| 4 | Evaluating LLM-based Agents for Multi-Turn Conversations: A Survey | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/pdf/2503.22458 |
| 5 | Logical Consistency of LLMs in Fact-Checking (Coordination Dimension) | Multiple authors | ICLR 2025 | 2025 | https://proceedings.iclr.cc/paper_files/paper/2025/file/3209cf3312b2cbb68e33644362ddc2bd-Paper-Conference.pdf |

### Paper Details

#### 1. Survey on LLM-Based Multi-Turn Dialogue Systems (ACM Computing Surveys 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Multi-turn dialogue systems exhibit emergent coordination between turns — successful systems develop implicit state tracking, topic management, and intent fulfillment patterns.
  - Reviews advances in architecture, training, and evaluation with emphasis on turn-level coordination mechanisms.
  - Implicit coordination is a key differentiator of high-quality dialogue systems.
- **Methodology:** Systematic survey of multi-turn dialogue advances; taxonomy of coordination mechanisms.

#### 2. ConsistentChat: Skeleton-Guided Dialogue (EMNLP 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Nine human conversational intent types with curated information flows used as dialogue skeletons.
  - Skeleton-guided coordination **dramatically improves topical coherence** and informational consistency.
  - Demonstrates that explicit coordination structures (intent flows) improve multi-turn dialogue quality substantially.
- **Methodology:** Taxonomy of 9 conversational intent types; skeleton-guided dialogue construction pipeline; consistency and coherence evaluation.

#### 3. Intent Mismatch Causes LLMs to Get Lost (arXiv 2026)
- **Significance:** 7/10
- **Key Findings:**
  - Intent mismatches between user and LLM create cascading coordination failures across multi-turn conversations.
  - Once intent mismatch occurs, LLMs rarely recover coordination even with explicit correction attempts.
  - Intent alignment is the **primary coordination challenge** in multi-turn human-AI dialogue.
- **Methodology:** Analysis of intent mismatch patterns; measurement of recovery rates; characterization of coordination failure modes.

#### 4. Survey: Evaluating LLM-based Agents for Multi-Turn Conversations (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Multi-turn evaluation must account for emergent coordination properties across turns that cannot be captured by turn-level metrics alone.
  - Most benchmarks treat turns independently, missing the emergent coordination dimension.
- **Methodology:** Survey of 276 papers on multi-turn agent evaluation; gap analysis for emergent coordination measurement.

#### 5. Logical Consistency of LLMs (ICLR 2025) — Coordination Dimension
- **Significance:** 7/10
- **Key Findings:**
  - Multi-turn dialogue produces emergent coordination patterns between model knowledge and conversation context not predictable from single-turn behavior.
  - Neuro-symbolic integration can enforce coordination between logical constraints and generative behavior.

---

### Well-Established Findings (Multi-Turn Coordination)
1. Intent alignment is the primary coordination challenge in multi-turn human-AI dialogue.
2. Explicit structural coordination (e.g., skeleton-guided dialogue) improves multi-turn coherence.
3. Most existing evaluation benchmarks miss emergent multi-turn coordination properties.

### Research Gaps (Multi-Turn Coordination)
1. No formal theory of emergent coordination in multi-turn human-AI dialogue.
2. No metrics specifically measuring intent alignment maintenance across conversation turns.
3. Limited work on coordination recovery mechanisms after intent mismatches.
4. Insufficient study of how different dialogue styles (collaborative, adversarial) affect emergent coordination.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Cooperate or Collapse: Emergence of Sustainable Cooperation in a Society of LLM Agents | Multiple authors | NeurIPS 2024 | 2024 | https://arxiv.org/abs/2404.16698 |
| 2 | Emergent Coordination in Multi-Agent Language Models | Riedl et al. | arXiv 2025 | 2025 | https://arxiv.org/abs/2510.05174 |
| 3 | Game-Theoretic Lens on LLM-based Multi-Agent Systems | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2601.15047v1 |
| 4 | ZSC-Eval: Multi-agent Zero-shot Coordination | Wang et al. (SJTU) | NeurIPS 2024 | 2024 | https://arxiv.org/abs/2310.05208 |
| 5 | From Debate to Equilibrium: Bayesian Nash Equilibrium for Multi-Agent LLMs | Multiple authors | OpenReview 2025 | 2025 | https://openreview.net/forum?id=RQwexjUCxm |

### Paper Details

#### 1. GovSim: Cooperate or Collapse (NeurIPS 2024)
- **Significance:** 10/10
- **Key Findings:**
  - Sustainable cooperation emerges in LLM agent societies only under specific conditions: communication, universalization-based moral reasoning, and sufficient model capability.
  - Most LLM agents fail to achieve sustainable equilibria — survival rates below **54%** for weaker models.
  - Successful multi-agent coordination requires both individual reasoning capability and emergent group-level strategy.
- **Methodology:** GovSim — society of LLM agents managing shared resource; measurement of cooperation emergence and sustainability; ablation of communication and reasoning components.

#### 2. Emergent Coordination in Multi-Agent Language Models (arXiv 2025)
- **Significance:** 9/10
- **Key Findings:**
  - Information-theoretic framework confirms LLM-based MAS can exhibit genuine **higher-order emergent coordination** (synergy beyond pairwise interactions).
  - Prompt design can steer systems from mere aggregates to genuine higher-order collectives.
  - Emergent coordination is measurable and performance-relevant, not just a superficial pattern.
- **Methodology:** Information-theoretic measures (synergy, redundancy, higher-order structure); tested across diverse LLM families; prompt design effects analysis.

#### 3. Game-Theoretic Lens on LLM-based Multi-Agent Systems (arXiv 2025)
- **Significance:** 9/10
- **Key Findings:**
  - LLM-based MAS can be analyzed using game theory (players, strategies, payoffs, information) to understand emergent coordination strategies.
  - LLM agents tend to **cooperate and exhibit fairness reasoning** rather than converging to Nash equilibria in multi-round settings.
  - Language-mediated coordination enables novel strategies not available to reward-only MARL agents.
- **Methodology:** Game-theoretic framework applied to LLM-MAS; analysis of emergent strategies across cooperative, competitive, and mixed settings.

#### 4. ZSC-Eval: Zero-shot Coordination (NeurIPS 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Zero-shot coordination (ZSC) with unseen partners is a fundamental emergent behavior challenge.
  - Training partner distribution profoundly shapes what coordination strategies emerge.
  - BR-Div and BR-Prox metrics provide the first principled evaluation of ZSC generalization performance.
- **Methodology:** Partner candidate generation via behavior-preferring rewards; BR-Div selection; BR-Prox generalization metric; benchmarked on Overcooked and Google Research Football; validated with human experiments.

#### 5. From Debate to Equilibrium: Bayesian Nash Equilibrium for Multi-Agent LLMs (OpenReview 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Recasts multi-LLM coordination as an incomplete-information game seeking a Bayesian Nash Equilibrium (BNE).
  - BNE-based coordination (ECON) allows each LLM to independently select responses maximizing expected reward conditioned on beliefs about co-agents.
  - Achieves coordination emergence through belief modeling rather than explicit communication — more efficient.
- **Methodology:** BNE formulation for multi-LLM coordination; hierarchical RL for belief-conditioned strategy learning; evaluated on cooperative and competitive coordination benchmarks.

---

### Well-Established Findings (Multi-Agent Coordination & Emergence)
1. Emergent sustainable cooperation in LLM agent societies requires **both** communication AND strong individual reasoning capability.
2. LLM agents exhibit fairness reasoning and tend to cooperate rather than converging to Nash equilibria.
3. Zero-shot coordination with unseen partners is a fundamental emergent behavior challenge.
4. Graph-based coordination topologies outperform star/chain/tree structures (MultiAgentBench, ACL 2025).

### Mixed Results (Multi-Agent Coordination & Emergence)
1. Whether emergent cooperation in simulated multi-agent settings generalizes to real-world deployment.
2. Relative importance of individual agent capability vs. communication for emergent coordination.
3. Whether game-theoretic equilibria are descriptively accurate for LLM multi-agent behavior.

### Research Gaps (Multi-Agent Coordination & Emergence)
1. No formal theory explaining when and why emergent cooperation vs. defection arises in LLM agent societies.
2. Limited study of emergent coordination in heterogeneous multi-agent systems (different LLMs interacting).
3. No systematic study of how coordination strategies evolve over extended multi-agent interactions.
4. Insufficient work on the relationship between individual agent capability and emergent collective intelligence.

---

## Industry Best Practices

### Coordination — Multi-Turn
- Explicit dialogue state tracking systems.
- Intent classification at each turn.
- Topic management and coherence enforcement mechanisms.

### Coordination & Emergence — Multi-Agent
- Structured communication protocols to channel emergent coordination.
- Role specialization to reduce coordination search space.
- Simulation-based testing of coordination emergence before deployment.

---

*Last updated: 2026-05-17*
