# Hallucination & Factuality in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** EMNLP, NeurIPS, TACL, arXiv

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Towards Mitigating LLM Hallucination via Self Reflection | Ji et al. | Findings of EMNLP 2023 | 2023 | https://aclanthology.org/2023.findings-emnlp.123/ |
| 2 | Temporal Graph Network: Hallucination Detection in Multi-Turn Conversation | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2601.03051v1 |
| 3 | HalluHard: A Hard Multi-Turn Hallucination Benchmark | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2602.01031v1 |
| 4 | Improving Factual Consistency for Knowledge-Grounded Dialogue Systems (K-Dial + RLFC) | Multiple authors | Findings of EMNLP 2023 | 2023 | https://aclanthology.org/2023.findings-emnlp.525/ |
| 5 | Knowledge Conflicts for LLMs: A Survey | Multiple authors | EMNLP 2024 | 2024 | https://aclanthology.org/2024.emnlp-main.486.pdf |

### Paper Details

#### 1. Mitigating LLM Hallucination via Self Reflection (EMNLP 2023)
- **Significance:** 9/10
- **Key Findings:**
  - Three-loop self-reflection (factual knowledge acquisition → knowledge-consistent answering → question-entailment answering) steadily enhances factuality, consistency, and entailment across multi-turn interactions.
  - First systematic mitigation of hallucination in multi-turn knowledge-grounded dialogue.
- **Methodology:** Three-loop self-reflection framework; evaluation on medical generative QA; factuality, consistency, and entailment measurement.

#### 2. Temporal Graph Network for Hallucination Detection (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Models multi-turn dialogue as a **temporal graph** where information propagates across nodes representing individual turns.
  - Hallucinations introduced in early turns **propagate and reinforce** through subsequent turns.
  - Temporal graph approach significantly outperforms turn-independent hallucination detection.
- **Methodology:** Temporal graph network modeling of multi-turn dialogues; hallucination propagation tracking; comparison with turn-independent detection methods.

#### 3. HalluHard: Hard Multi-Turn Hallucination Benchmark (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Existing hallucination benchmarks significantly underestimate multi-turn hallucination rates.
  - SoTA models still fail substantially on hard multi-turn factual reasoning chains.
  - Specifically targets scenarios where hallucinations are most likely to occur and propagate.
- **Methodology:** Curated hard multi-turn hallucination test cases; evaluation of SoTA LLMs; comparison with existing benchmarks.

#### 4. K-Dial + RLFC: Factual Consistency in Knowledge-Grounded Dialogue (EMNLP 2023)
- **Significance:** 8/10
- **Key Findings:**
  - PLM-based knowledge-grounded dialogue systems are systematically prone to factual inconsistency.
  - RLFC (reinforcement learning for factual consistency) achieves superior factual consistency over supervised methods alone.
- **Methodology:** K-Dial: extended FFNs in Transformers for knowledge expression; RLFC: RL-based alignment with gold knowledge; evaluated on WoW and CMU_DoG datasets.

#### 5. Knowledge Conflicts for LLMs: A Survey (EMNLP 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Multi-turn dialogue creates knowledge conflict scenarios where parametric LLM knowledge conflicts with contextual knowledge from prior turns, leading to systematic hallucination patterns.
  - Three conflict types: context-memory, inter-context, and intra-memory.
  - Conflict resolution is a critical unsolved problem for factual multi-turn dialogue.
- **Methodology:** Systematic survey of knowledge conflict types; analysis of conflict resolution behaviors; taxonomy of conflict scenarios.

---

### Well-Established Findings
1. Hallucinations introduced in early turns propagate and reinforce across subsequent turns.
2. Self-reflection mechanisms can substantially reduce hallucination in multi-turn settings.
3. Knowledge-grounded dialogue systems are systematically prone to factual inconsistency.

### Mixed Results
1. Whether RAG effectively reduces hallucination in multi-turn settings vs. single-turn.
2. Relative effectiveness of different self-correction strategies for multi-turn factuality.
3. Whether larger LLMs are less susceptible to hallucination accumulation across turns.

### Research Gaps
1. No standardized benchmark specifically measuring hallucination propagation across turns.
2. No formal models of hallucination propagation dynamics in multi-turn conversation.
3. Insufficient study of hallucination in domain-specific multi-turn dialogue (medical, legal).
4. Limited work on detecting vs. preventing hallucination accumulation in deployed dialogue systems.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Cooperate or Collapse: Emergence of Sustainable Cooperation in a Society of LLM Agents (GovSim) | Multiple authors | NeurIPS 2024 | 2024 | https://arxiv.org/abs/2404.16698 |
| 2 | LLM-based Agents Suffer from Hallucinations: A Survey | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2509.18970v1 |
| 3 | AgentHallu: Benchmarking Automated Hallucination Attribution of LLM-based Agents | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2601.06818v1 |
| 4 | Mitigating Hallucination via RAG, Reasoning, and Agentic Systems | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2510.24476v1 |
| 5 | An Empirical Study on Hallucinations in Embodied Agents | Multiple authors | Findings of EMNLP 2025 | 2025 | https://aclanthology.org/2025.findings-emnlp.1158.pdf |

### Paper Details

#### 1. GovSim: Cooperate or Collapse (NeurIPS 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Factual hallucinations about resource states in multi-agent resource management lead to **system collapse**.
  - Agent hallucinations about shared state compound through multi-agent communication.
  - Only the most powerful LLMs avoid hallucination-driven collapse; survival rates below **54%** for weaker models.
- **Methodology:** Governance of the Commons Simulation (GovSim); multi-agent resource management with shared state; measurement of hallucination-driven collapse.

#### 2. LLM-based Agents Suffer from Hallucinations: A Survey (arXiv 2025)
- **Significance:** 9/10
- **Key Findings:**
  - Hallucinated information from one agent is treated as valid input by others — creating a **propagation cycle** where false content is actively reinforced.
  - Agent hallucinations exhibit complex characteristics including hallucinatory accumulation and inter-module dependency.
  - Network updates can induce communication hallucinations due to inconsistent or outdated inter-agent connections.
- **Methodology:** Systematic survey of hallucination types, causes, detection methods, and mitigation strategies for LLM-based agents.

#### 3. AgentHallu: Hallucination Attribution Benchmark (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - First benchmark for attributing hallucinations to specific agents and pipeline stages in multi-agent systems.
  - Attribution accuracy is well below human-level — attributing which agent caused a hallucination is harder than detecting it.
  - Early-stage agent hallucinations have disproportionate downstream cascade effects.
- **Methodology:** Multi-agent hallucination attribution benchmark; automated attribution pipeline; evaluation of attribution accuracy vs. human annotation.

#### 4. Mitigating Hallucination via RAG, Reasoning, and Agentic Systems (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - RAG, reasoning enhancement, and agentic architectures are three complementary paradigms with distinct tradeoffs for multi-agent factuality.
  - Agentic verification loops significantly reduce factual errors in multi-step pipelines.
- **Methodology:** Survey of three mitigation paradigms; comparative analysis of effectiveness across task types.

#### 5. Hallucinations in Embodied Agents (EMNLP 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Embodied multi-agent systems exhibit hallucination patterns tied to **perception-action loops**.
  - A single root-cause hallucination can cascade into successive errors in long-horizon tasks.
  - Recovery from hallucination-induced errors is rare without explicit correction mechanisms.
- **Methodology:** Empirical study of hallucination patterns in embodied agent tasks; analysis of hallucination-to-action cascades; evaluation of recovery mechanisms.

---

### Well-Established Findings (Multi-Agent Hallucination)
1. Hallucinations from one agent propagate to and are reinforced by other agents in multi-agent pipelines.
2. Early-stage agent hallucinations have disproportionate downstream cascade effects.
3. Factual hallucinations about shared state can cause collective system failure in multi-agent settings.

### Mixed Results (Multi-Agent Hallucination)
1. Whether multi-agent debate and cross-checking reliably reduces hallucination propagation.
2. Relative effectiveness of RAG vs. agentic verification loops for multi-agent factuality.
3. Whether larger agent teams have higher or lower aggregate hallucination rates.

### Research Gaps (Multi-Agent Hallucination)
1. No standardized benchmark for measuring hallucination propagation across multi-agent pipelines.
2. No principled methods for hallucination containment at agent boundaries.
3. Insufficient study of hallucination in heterogeneous multi-agent systems.
4. Limited formal models of hallucination cascade dynamics in multi-agent networks.

---

## Industry Best Practices

### Hallucination & Factuality — Multi-Turn
- RAG-augmented dialogue systems to ground responses in verified sources.
- Factual consistency checkers as post-processing step.
- Citation requirements for knowledge-grounded responses.

### Hallucination & Factuality — Multi-Agent
- Dedicated fact-checking agents in multi-agent pipelines.
- Structured knowledge bases shared across agents to reduce hallucinatory drift.
- Cross-agent verification before high-stakes actions.

---

*Last updated: 2026-05-17*
