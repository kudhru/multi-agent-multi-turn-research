# Interpretability & Explainability in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** NAACL, EMNLP, FAccT, NeurIPS, arXiv (Oxford AIGI)

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Chain-of-Thought Is Not Explainability | Barez et al. (Oxford) | AIGI Oxford 2025 | 2025 | https://aigi.ox.ac.uk/wp-content/uploads/2025/07/Cot_Is_Not_Explainability.pdf |
| 2 | Trends in NLP Model Interpretability in the Era of LLMs | Multiple authors | NAACL 2025 | 2025 | https://aclanthology.org/2025.naacl-long.29.pdf |
| 3 | How Interpretable are Reasoning Explanations from LLMs? | Multiple authors | Findings of NAACL 2024 | 2024 | https://aclanthology.org/2024.findings-naacl.138.pdf |
| 4 | Explainability and Interpretability of Multilingual LLMs | Multiple authors | EMNLP 2025 | 2025 | https://aclanthology.org/2025.emnlp-main.1033.pdf |
| 5 | Layered Chain-of-Thought Prompting for Multi-Agent LLM Systems | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2501.18645v2 |

### Paper Details

#### 1. Chain-of-Thought Is Not Explainability (Oxford, 2025)
- **Significance:** 9/10
- **Key Findings:**
  - CoT reasoning chains are **post-hoc rationalizations** that are often not causally linked to the final answer.
  - The explanation does not faithfully reflect the model's true decision process.
  - Critical for multi-turn dialogue where users rely on reasoning traces to understand agent decisions.
  - Calls for faithful interpretability methods beyond CoT.
- **Methodology:** Analysis of CoT chains vs. actual model decisions; counterfactual intervention studies.

#### 2. Trends in NLP Interpretability (NAACL 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Shift from local (token/feature attribution) to global (concept-level, emergent behavior) interpretability as LLMs scale.
  - Dialogue systems present unique challenges because of evolving context.
  - Current interpretability methods designed for single-turn settings **fail to account for turn-dependent reasoning evolution**.
- **Methodology:** Systematic survey; taxonomy of interpretability methods; gap analysis for multi-turn settings.

#### 3. How Interpretable are Reasoning Explanations from LLMs? (NAACL 2024)
- **Significance:** 8/10
- **Key Findings:**
  - LLM-generated reasoning explanations are often not interpretable to users in the way designers assume.
  - Significant gaps between technical faithfulness and user comprehension.
  - Explanations in multi-turn dialogues are often contextually underspecified and fail to convey uncertainty.
- **Methodology:** Human studies evaluating interpretability; comparison of explanation types; user comprehension testing.

#### 4. Interpretability of Multilingual LLMs (EMNLP 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Interpretability methods developed for English LLMs fail to generalize to multilingual settings.
  - Feature attribution methods show inconsistent results across languages in conversational settings.
  - Cross-lingual dialogue interpretability is essentially an open problem.
- **Methodology:** Applied multiple interpretability methods to multilingual LLMs in dialogue settings; cross-lingual evaluation.

#### 5. Layered Chain-of-Thought Prompting (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Layered CoT structures reasoning into verifiable layers — each reasoning layer can be independently verified.
  - Demonstrates practical benefits including higher transparency, improved correctness, and heightened user trust.
  - Evaluated in healthcare, finance, and engineering applications.
- **Methodology:** Layered CoT framework with verifiable reasoning steps; user study measuring transparency and trust.

---

### Well-Established Findings
1. Chain-of-thought explanations are post-hoc rationalizations, not faithful representations of model reasoning.
2. Current interpretability methods designed for single-turn settings fail for multi-turn dialogue.
3. User comprehension of LLM explanations is significantly lower than designers assume.

### Mixed Results
1. Whether more elaborate explanation formats improve or worsen user decision-making.
2. The relative interpretability of different prompting strategies (CoT, ToT, ReAct).
3. Whether explanations improve or worsen over-reliance in conversational settings.

### Research Gaps
1. No interpretability methods specifically designed for multi-turn conversational dynamics.
2. Limited work on turn-by-turn explanation attribution in long dialogues.
3. No standardized evaluation framework for multi-turn dialogue interpretability.
4. Insufficient methods for visualizing reasoning evolution across conversation turns.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Emergent Coordination in Multi-Agent Language Models | Riedl et al. | arXiv 2025 | 2025 | https://arxiv.org/abs/2510.05174 |
| 2 | Language Grounded MARL with Human-interpretable Communication | Multiple authors | NeurIPS 2024 | 2024 | https://proceedings.neurips.cc/paper_files/paper/2024/file/a06e129e01e0d2ef853e9ff67b911360-Paper-Conference.pdf |
| 3 | The Role of Explainability in Collaborative Human-AI Disinformation Detection | Multiple authors | FAccT 2024 | 2024 | https://dl.acm.org/doi/10.1145/3630106.3659031 |
| 4 | Chain-of-Thought Is Not Explainability (Multi-Agent Context) | Barez et al. (Oxford) | AIGI Oxford 2025 | 2025 | https://aigi.ox.ac.uk/wp-content/uploads/2025/07/Cot_Is_Not_Explainability.pdf |
| 5 | A Comprehensive Survey on Multi-Agent Cooperative Decision-Making | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2503.13415v1 |

### Paper Details

#### 1. Emergent Coordination in Multi-Agent LMs (arXiv 2025)
- **Significance:** 9/10
- **Key Findings:**
  - Information-theoretic framework tests whether MAS exhibit genuine higher-order emergent structure beyond pairwise interactions.
  - Demonstrates that prompt design can steer systems from mere aggregates to genuine higher-order collectives.
  - Provides the first interpretability framework for emergent multi-agent coordination.
- **Methodology:** Information-theoretic measures of synergy and redundancy; tested across LLM family variations; analysis of prompt design effects.

#### 2. Language Grounded MARL with Human-interpretable Communication (NeurIPS 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Grounding multi-agent communication in natural language **dramatically improves human interpretability** without sacrificing performance.
  - Human-interpretable communication protocols emerge that correlate with task-relevant coordination strategies.
  - Language grounding provides a natural audit trail for multi-agent decision making.
- **Methodology:** MARL framework with language-grounded communication; human study of interpretability; comparison with non-grounded protocols.

#### 3. Explainability in Collaborative Human-AI Disinformation Detection (FAccT 2024)
- **Significance:** 9/10
- **Key Findings:**
  - AI explanations in human-multi-agent collaborative settings do **not reliably reduce over-reliance** and can worsen it.
  - Simply providing explanations is insufficient — they must be human-centered and calibrated.
  - Human oversight is legally required (EU AI Act) in fundamental rights domains.
- **Methodology:** Controlled experiment with human participants and multi-agent AI; varied explanation presence/type; measured complementarity and over-reliance.

#### 4. CoT Not Explainability (Multi-Agent Context)
- **Significance:** 8/10
- **Key Findings:**
  - In multi-agent settings, lack of faithful explanations from individual agents compounds into system-level opacity.
  - Each agent's CoT may mask the true coordination mechanism.
  - Calls for emergent behavior-level interpretability methods for MAS.

#### 5. Survey on Multi-Agent Cooperative Decision-Making (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Interpretability of complex multi-agent decision-making is a critical unsolved challenge.
  - Current methods provide only post-hoc approximations of coordination mechanisms.
  - Lack of interpretability is a primary obstacle to deployment in high-stakes domains.
- **Methodology:** Systematic survey of cooperative decision-making approaches; taxonomy of interpretability mechanisms.

---

### Well-Established Findings (Multi-Agent Interpretability)
1. Multi-agent coordination decisions are fundamentally opaque to external observers.
2. Language-grounded communication dramatically improves interpretability without major performance costs.
3. AI explanations in multi-agent collaborative settings can worsen rather than improve human oversight.

### Research Gaps (Multi-Agent Interpretability)
1. No formal interpretability frameworks specifically for multi-agent coordination.
2. Limited work on explaining emergent collective behaviors in LLM-based MAS.
3. No causal interpretability methods for multi-agent information flow.
4. Insufficient human-centered evaluation of multi-agent explanation quality.

---

## Industry Best Practices

### Multi-Turn Interpretability
- CoT prompting as proxy for transparency (with known faithfulness limitations).
- User-facing explanation summaries at key decision points.
- Citation/source attribution in knowledge-grounded dialogue systems.

### Multi-Agent Interpretability
- Structured logging of agent-to-agent communication for post-hoc audit.
- Designated explanation-generating agents in multi-agent pipelines.
- Human oversight agents monitoring coordination patterns.

---

*Last updated: 2026-05-17*
