# Scalability & Reliability in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** ICLR, NeurIPS, EMNLP, ACL, arXiv

---

## PART A: SCALABILITY

## 1. Multi-Turn Conversations — Scalability

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Context Length Alone Hurts LLM Performance Despite Perfect Retrieval | Multiple authors | Findings of EMNLP 2025 | 2025 | https://arxiv.org/html/2510.05381v1 |
| 2 | MT-Eval: A Multi-Turn Capabilities Evaluation Benchmark | Kwan et al. | EMNLP 2024 | 2024 | https://aclanthology.org/2024.emnlp-main.1124/ |
| 3 | AgentBoard: An Analytical Evaluation Board of Multi-turn LLM Agents | Ma et al. (HKUST) | NeurIPS 2024 (Oral) | 2024 | https://arxiv.org/abs/2401.13178 |
| 4 | Beyond Single-Turn: A Survey on Multi-Turn Interactions with LLMs | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2504.04717v4 |
| 5 | LLM Task Interference: Multi-Turn Interaction Impact | Multiple authors | EMNLP 2024 | 2024 | https://aclanthology.org/2024.emnlp-main.811.pdf |

### Paper Details

#### 1. Context Length Alone Hurts LLM Performance (EMNLP 2025)
- **Significance:** 9/10
- **Key Findings:**
  - Extending input length substantially degrades LLM reasoning **even when retrieval is perfect (100% exact match recall)**.
  - Performance continues to degrade as input length increases with all relevant evidence available.
  - A fundamental scalability limit of current LLM architectures for long multi-turn conversations.
- **Methodology:** Controlled experiments decoupling context length from retrieval quality; tested with 100% exact-match retrieval across varying context lengths.

#### 2. MT-Eval (EMNLP 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Significant performance degradation in multi-turn settings across 10 LLMs — not correlated with single-turn capability.
  - Distance to relevant content and error propagation are key factors.
  - 4 dialogue task categories (Recollection, Expansion, Refinement, Follow-up) with 1,170 multi-turn queries.
- **Methodology:** Human-in-the-loop data creation; single-turn vs. multi-turn performance comparison across 10 LLMs.

#### 3. AgentBoard: Analytical Evaluation of Multi-turn LLM Agents (NeurIPS 2024 Oral)
- **Significance:** 9/10
- **Key Findings:**
  - Fine-grained **progress rate metric** captures incremental advances rather than just final success.
  - Most LLMs show sharply diminishing returns as task complexity (number of required actions) scales.
  - Partially-observable environments compound scalability challenges.
- **Methodology:** 9-task multi-turn evaluation framework; multi-round interaction benchmarking; open-source evaluation toolkit with visualization.

#### 4. Beyond Single-Turn Survey (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Research community has largely neglected multi-turn scalability in favor of single-turn benchmarking.
  - Performance degrades monotonically with number of turns but rate varies substantially across architectures and task types.
  - Evaluation, memory management, and consistency are the three core scalability challenges.
- **Methodology:** Systematic review of 276 papers from ICLR, NeurIPS, AAAI, NAACL, EMNLP, ACL (2022–2024).

#### 5. LLM Task Interference (EMNLP 2024)
- **Significance:** 7/10
- **Key Findings:**
  - Multi-turn interactions cause task interference: prior turns degrade performance on subsequent tasks even when semantically unrelated.
  - Performance drops scale with the number of prior turns.
  - Cross-task contamination is a scalability bottleneck in real-world multi-turn deployment.
- **Methodology:** Systematic study of task interference across multi-turn sequences; varied task types and orderings.

---

### Well-Established Findings (Multi-Turn Scalability)
1. Multi-turn performance degrades monotonically with increasing conversation length for most LLMs.
2. Context length imposes fundamental scalability limits even with perfect retrieval.
3. Task interference across turns is a systematic scalability challenge.

### Research Gaps (Multi-Turn Scalability)
1. No systematic study of the relationship between conversation depth and task complexity on scaling.
2. No theoretical framework for predicting multi-turn performance from single-turn metrics.
3. Insufficient study of scalability in domain-specific long-horizon dialogues.

---

## 2. Multi-Agent Systems — Scalability

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | AgentBench: Evaluating LLMs as Agents | Liu et al. (Tsinghua) | ICLR 2024 | 2024 | https://arxiv.org/abs/2308.03688 |
| 2 | MegaAgent: A Large-Scale Autonomous LLM-based Multi-Agent System | Multiple authors | ACL 2025 (Findings) | 2025 | https://aclanthology.org/2025.findings-acl.259/ |
| 3 | MultiAgentBench: Evaluating the Collaboration and Competition of LLM Agents | Zhu, Du et al. | ACL 2025 | 2025 | https://aclanthology.org/2025.acl-long.421/ |
| 4 | Multi-Agent Coordination via Multi-Level Communication (SeqComm) | Ding et al. | NeurIPS 2024 | 2024 | https://proceedings.neurips.cc/paper_files/paper/2024/file/d6be51e667e0b263e89a23294b57f8cf-Paper-Conference.pdf |
| 5 | Towards a Science of Scaling Agent Systems | Multiple authors | arXiv 2024 | 2024 | https://arxiv.org/html/2512.08296v1 |

### Paper Details

#### 1. AgentBench (ICLR 2024)
- **Significance:** 9/10 — (see Task Success section for full details)
- **Scalability-specific findings:** Performance degrades sharply with task complexity and horizon length; poor long-term reasoning is the main obstacle.

#### 2. MegaAgent: 590-Agent Simulation (ACL 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Successfully scales to **590 agents** in a national policy simulation; significantly outperforms MetaGPT in task completion efficiency and scalability.
  - Dynamic task decomposition and parallel execution are key enablers of scalability.
  - Communication overhead grows manageable when organized hierarchically.
- **Methodology:** Deployed on Gobang game development and national policy simulation; compared against MetaGPT and other baselines.

#### 3. MultiAgentBench (ACL 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Collaboration quality does not scale linearly with agent count.
  - Specific topologies and strategies matter more than sheer numbers.
  - Reveals fundamental limits in LLMs' ability to maintain coherent coordination at scale.
- **Methodology:** Comprehensive benchmark with diverse scenarios; milestone-based KPIs; topology and strategy evaluation.

#### 4. SeqComm: Multi-Level Communication (NeurIPS 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Without effective organization, systems degenerate into **O(N²)** full-mesh communication patterns.
  - Two-phase scheme (negotiation + launching) reduces communication overhead while maintaining coordination quality.
  - Better performance-communication tradeoffs than baseline methods as agent count grows.
- **Methodology:** Sequential Communication scheme; cooperative MARL benchmarks with varying agent counts; measured communication overhead and task performance tradeoffs.

#### 5. Towards a Science of Scaling Agent Systems (arXiv 2024)
- **Significance:** 7/10
- **Key Findings:**
  - Inter-agent message exchange overhead grows super-linearly without architectural constraints.
  - Communication compression and hierarchical organization are essential for scaling beyond tens of agents.
  - Proposes empirical scaling laws analogous to neural network scaling laws.
- **Methodology:** Empirical analysis of scaling behavior; measurement of communication overhead and coordination quality as agent count scales.

---

### Well-Established Findings (Multi-Agent Scalability)
1. Communication overhead grows O(N²) without hierarchical organization.
2. Coordination quality does not scale linearly with agent count.
3. Task complexity and horizon length are the primary scalability bottlenecks.

### Research Gaps (Multi-Agent Scalability)
1. No scaling laws analogous to neural network scaling laws for multi-agent systems.
2. No formal analysis of the relationship between task complexity and optimal agent count.
3. Insufficient benchmarks testing scalability beyond hundreds of agents.
4. Limited study of scalability under dynamic agent addition/removal.

---

## PART B: RELIABILITY

## 1. Multi-Turn Conversations — Reliability

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | MT-Eval: A Multi-Turn Capabilities Evaluation Benchmark | Kwan et al. | EMNLP 2024 | 2024 | https://aclanthology.org/2024.emnlp-main.1124/ |
| 2 | Logical Consistency of LLMs in Fact-Checking | Multiple authors | ICLR 2025 | 2025 | https://proceedings.iclr.cc/paper_files/paper/2025/file/3209cf3312b2cbb68e33644362ddc2bd-Paper-Conference.pdf |
| 3 | Revisiting the Reliability of LMs in Instruction-Following | Multiple authors | arXiv 2024 | 2024 | https://arxiv.org/html/2512.14754v1 |
| 4 | Quantifying Conversational Reliability of LLMs under Multi-Turn Interaction | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2603.01423 |
| 5 | Evaluating Performance Drift from Model Switching in Multi-Turn LLM Systems | Multiple authors | arXiv 2026 | 2026 | https://arxiv.org/html/2603.03111 |

### Paper Details

#### 1. MT-Eval (EMNLP 2024)
- **Reliability-specific findings:** Performance degradation in multi-turn settings is not correlated with single-turn capability — reliability is a distinct, measurable property. Error propagation from earlier turns is the primary mechanism of reliability degradation.

#### 2. Logical Consistency of LLMs in Fact-Checking (ICLR 2025)
- **Significance:** 8/10
- **Key Findings:**
  - LLMs fail systematically on distributive, associative, syllogism, and commutative logic rules.
  - Logical inconsistency is a fundamental reliability issue that compounds across multi-turn reasoning chains.
  - Neuro-symbolic integration can enforce logical consistency.
- **Methodology:** Propositional and FOL consistency evaluation; neuro-symbolic integration with symbolic provers.

#### 3. Reliability in Instruction-Following (arXiv 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Performance can drop by up to **61.8%** under nuanced prompts that convey analogous intents with subtle variations.
  - Reliability failures in instruction-following compound across multi-turn conversations.
- **Methodology:** Designed cousin prompt pairs with subtle nuances encoding the same intent; measured performance drops across LLMs.

#### 4. Quantifying Conversational Reliability (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Reliability degrades significantly as conversation length increases.
  - **Unreliability is a more significant problem than raw capability loss** in multi-turn settings.
  - Proposes reliability-adjusted evaluation metrics.
- **Methodology:** Multi-turn simulation; quantitative reliability metrics tracking consistency, correctness, and recoverability.

#### 5. Performance Drift from Model Switching (arXiv 2026)
- **Significance:** 7/10
- **Key Findings:**
  - When one model must continue another model's multi-turn conversation, significant **performance drift** occurs due to mismatched conversational assumptions.
  - Switch-matrix benchmark measuring handoff-induced drift as a key reliability metric.
  - Model switching is a practical reliability challenge in production multi-LLM systems.
- **Methodology:** Switch-matrix benchmark on CoQA and Multi-IF datasets; systematic evaluation of all pairwise model handoff combinations.

---

### Well-Established Findings (Multi-Turn Reliability)
1. Multi-turn reliability is a distinct property from single-turn capability.
2. Error propagation from early turns is the primary mechanism of multi-turn reliability failure.
3. Logical inconsistency compounds across multi-turn reasoning chains.

### Research Gaps (Multi-Turn Reliability)
1. No standardized reliability benchmarks for multi-turn conversational AI.
2. No formal reliability certification frameworks for deployed conversational systems.
3. Insufficient work on recovery mechanisms when LLMs "get lost" mid-conversation.
4. Limited study of reliability under user behavior variations (rephrasing, clarification, contradictions).

---

## 2. Multi-Agent Systems — Reliability

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Towards a Science of AI Agent Reliability | Rabanser, Kapoor et al. | arXiv 2026 | 2026 | https://arxiv.org/abs/2602.16666 |
| 2 | Why Do Multi-Agent LLM Systems Fail? | Cemri et al. | ICLR 2025 | 2025 | https://iclr.cc/virtual/2025/33314 |
| 3 | Which Agent Causes Task Failures and When? | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/pdf/2505.00212 |
| 4 | Reflective Multi-Agent Collaboration based on LLMs (COPPER) | Multiple authors | NeurIPS 2024 | 2024 | https://proceedings.neurips.cc/paper_files/paper/2024/file/fa54b0edce5eef0bb07654e8ee800cb4-Paper-Conference.pdf |
| 5 | ZSC-Eval: An Evaluation Toolkit for Multi-agent Zero-shot Coordination | Wang et al. (SJTU) | NeurIPS 2024 | 2024 | https://arxiv.org/abs/2310.05208 |

### Paper Details

#### 1. Towards a Science of AI Agent Reliability (arXiv 2026)
- **Significance:** 9/10 — (see Robustness section for full details)
- **Key metrics:** Outcome consistency 30–75% across 14 models; predictability is the weakest dimension.

#### 2. Why Do Multi-Agent LLM Systems Fail? (ICLR 2025)
- **Significance:** 9/10
- **Key Reliability Findings:**
  - 18 fine-grained failure modes; verification and quality control are the most impactful failure categories for reliability.
  - Performance gains over single-agent baselines remain minimal on many tasks due to reliability failures.

#### 3. Which Agent Causes Task Failures and When? (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Failures are concentrated in specific agent roles; early-stage failures have disproportionate impact.
  - Provides both algorithmic and hand-crafted benchmarks for attribution.
- **Methodology:** Failure attribution benchmark; annotation of failure causes; analysis of failure timing and severity.

#### 4. COPPER: Reflective Multi-Agent Collaboration (NeurIPS 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Reflection mechanisms allow agents to identify and correct coordination failures.
  - Reflection-augmented multi-agent systems show significantly improved consistency across repeated runs.
- **Methodology:** Counterfactual PPO-based reflector fine-tuning; measured consistency and reliability across multiple runs.

#### 5. ZSC-Eval: Zero-shot Coordination (NeurIPS 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Zero-shot coordination is a critical reliability challenge: agents trained in one partner distribution fail with unseen partners.
  - **Training partner distribution shapes what coordination strategies emerge.**
  - BR-Prox metric provides the first quantitative measure of ZSC generalization performance.
- **Methodology:** Behavior-preferring reward-based partner candidate generation; BR-Div partner selection; benchmarked on Overcooked and Google Research Football.

---

### Well-Established Findings (Multi-Agent Reliability)
1. Multi-agent systems show significantly lower reliability than single-agent baselines on many tasks.
2. Coordination failures and verification gaps are primary reliability bottlenecks.
3. Zero-shot coordination with unseen partners is a fundamental reliability challenge.

### Research Gaps (Multi-Agent Reliability)
1. No standardized reliability benchmarks for LLM-based multi-agent systems across domains.
2. No quantitative models predicting multi-agent reliability from component agent reliability.
3. Insufficient study of reliability under dynamic team composition changes.
4. Limited formal verification methods applicable to LLM-based MAS.

---

## Industry Best Practices

### Scalability
- **Multi-Turn:** Conversation summarization to manage context window limits; memory-augmented architectures (RAG, external memory); turn-level compression and information distillation.
- **Multi-Agent:** Hierarchical agent organization to reduce communication overhead; specialized agent roles; asynchronous execution and parallel agent pipelines.

### Reliability
- **Multi-Turn:** Consistency checks between system responses across turns; conversation state tracking; automated regression testing across conversational scenarios.
- **Multi-Agent:** End-to-end testing and CI/CD pipelines; output validation agents as dedicated reliability checkers; human-in-the-loop checkpoints at critical agent handoff points.

---

*Last updated: 2026-05-17*
