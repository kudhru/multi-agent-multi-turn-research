# Performance & Quality in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** NeurIPS, ICLR, ICML, ACL, TACL, IJCAI, arXiv

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena | Zheng, Chiang et al. | NeurIPS 2023 | 2023 | https://arxiv.org/abs/2306.05685 |
| 2 | LongBench: A Bilingual, Multitask Benchmark for Long Context Understanding | Bai, Lv et al. (Tsinghua) | ACL 2024 | 2024 | https://arxiv.org/abs/2308.14508 |
| 3 | LongBench v2: Towards Deeper Understanding and Reasoning on Realistic Long-context Multitasks | THUDM Group | ACL 2025 | 2025 | https://longbench2.github.io/ |
| 4 | mtRAG: A Multi-Turn Conversational Benchmark for Evaluating RAG Systems | Multiple authors | TACL 2025 | 2025 | https://direct.mit.edu/tacl/article/doi/10.1162/TACL.a.19/132114/mtRAG-A-Multi-Turn-Conversational-Benchmark-for |
| 5 | Beyond Single-Turn: A Survey on Multi-Turn Interactions with LLMs | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2504.04717v5 |

### Paper Details

#### 1. MT-Bench and Chatbot Arena (NeurIPS 2023)
- **Significance:** 10/10
- **Key Findings:**
  - Introduces MT-Bench (80 expert-crafted multi-turn questions across 8 domains) and the **LLM-as-judge methodology**.
  - GPT-4 as judge achieves **>80% agreement with human preferences** — same level as inter-human agreement.
  - Identifies key biases: position bias, verbosity bias, self-enhancement bias, with proposed mitigations.
  - Establishes the gold standard for automated multi-turn evaluation.
- **Methodology:** Human preference collection via crowdsourcing (Chatbot Arena); LLM-as-judge evaluation; bias analysis across model families.

#### 2. LongBench (ACL 2024)
- **Significance:** 9/10
- **Key Findings:**
  - First bilingual (English+Chinese) long-context benchmark: 21 tasks across 6 categories, average lengths 6.7k words (EN) / 13.4k characters (ZH).
  - Most LLMs degrade significantly on tasks requiring retrieval from **8k+ tokens**.
  - Single-turn long-context task performance does not reliably predict multi-turn conversational coherence.
- **Methodology:** Benchmark construction from real-world data sources; automated and human evaluation; cross-model comparison.

#### 3. LongBench v2 (ACL 2025)
- **Significance:** 9/10
- **Key Findings:**
  - 503 challenging multiple-choice questions; context lengths 8k to **2M tokens**; 6 major task categories including long-dialogue history understanding.
  - Frontier LLMs (GPT-4, Claude 3) achieve only **50–60% accuracy** on the hardest tasks — long-context performance remains far from saturated.
  - Introduces stricter contamination controls and difficulty calibration.
- **Methodology:** Expert annotation; multi-model evaluation; difficulty calibration via human baseline scoring.

#### 4. mtRAG (TACL 2025)
- **Significance:** 8/10
- **Key Findings:**
  - First end-to-end human-generated multi-turn RAG benchmark: 110 conversations, 7.7 turns each, 842 tasks across 4 domains.
  - SoTA RAG systems **fail significantly on later turns**, unanswerable questions, and non-standalone questions requiring coreference resolution.
  - Single-turn RAG evaluation severely overestimates real-world conversational performance.
- **Methodology:** Human-generated conversation annotation; end-to-end evaluation pipeline; LLM and traditional retrieval model comparison.

#### 5. Beyond Single-Turn Survey (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Taxonomy of multi-turn dependency types: Recollection, Refinement, Expansion, Follow-up, Instruction Retention, Inference Memory, Reliable Versioned Editing, Self-Coherence.
  - Short conversations (3–5 turns) fail on task completion; long conversations (20+ turns) fail on context drift and knowledge retention — **distinct failure modes**.
  - Gap between current automated metrics and human-perceived conversation quality.
- **Methodology:** Literature survey; taxonomy construction; benchmark comparison.

---

### Well-Established Findings

1. LLM-as-judge (GPT-4) matches human preference agreement at >80% — now the standard for multi-turn evaluation.
2. Current LLMs degrade measurably at 8k+ token context in both factual retrieval and coherence tasks.
3. Short conversations fail on task completion; long conversations fail on context drift — distinct failure modes requiring different mitigations.
4. Standard NLP metrics (BLEU, ROUGE) are poor proxies for multi-turn dialogue quality; task-specific or LLM-judge metrics are preferred.
5. RAG significantly improves factual consistency in multi-turn settings, particularly for knowledge-intensive domains.

### Mixed / Contradictory Results

1. **LLM-as-judge biases:** Position, verbosity, self-enhancement biases can misrank models; mitigations exist but are not universally adopted.
2. **Context compression:** Pruning 30–50% of middle-history tokens maintains factual consistency in some evaluations but degrades coherence in others.
3. **Benchmark-to-deployment gap:** Performance on LongBench doesn't reliably predict multi-turn conversational coherence in open-domain dialogue.
4. **Chain-of-thought + multi-turn consistency:** Improves single-turn reasoning but effect on multi-turn consistency is mixed and task-dependent.

### Research Gaps

1. Benchmarks covering very long conversations (50+ turns) with ground-truth annotations for context drift and factual consistency.
2. Evaluation metrics jointly capturing task success, contextual coherence, and factual consistency without LLM-judge biases.
3. Systematic study of how instruction-following degrades as conversation length increases (instruction retention over 10+ turns).
4. Evaluation of multi-turn performance under distribution shift (user queries changing topic mid-conversation).
5. Ground-truth multi-turn benchmarks for specialized domains (medical, legal, scientific dialogue).

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Improving Factuality and Reasoning in Language Models through Multiagent Debate | Du et al. | ICML 2024 | 2024 | https://arxiv.org/abs/2305.14325 |
| 2 | AgentBench: Evaluating LLMs as Agents | Liu et al. (Tsinghua) | ICLR 2024 | 2024 | https://arxiv.org/abs/2308.03688 |
| 3 | Why Do Multi-Agent LLM Systems Fail? (MAST) | Cemri et al. | arXiv 2025 | 2025 | https://arxiv.org/abs/2503.13657 |
| 4 | Large Language Model based Multi-Agents: A Survey of Progress and Challenges | Guo, Chen et al. | IJCAI 2024 | 2024 | https://arxiv.org/abs/2402.01680 |
| 5 | MultiAgentBench: Evaluating the Collaboration and Competition of LLM Agents | Zhu, Du et al. | ACL 2025 | 2025 | https://arxiv.org/abs/2503.01935 |

### Paper Details

#### 1. Multiagent Debate (ICML 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Multiple LLM instances proposing and debating responses over multiple rounds significantly improves mathematical reasoning (GSM8K), strategic reasoning, and factual QA accuracy.
  - Multi-agent debate reduces hallucinations as agents identify and remove uncertain/inconsistent facts.
  - However, later analyses (2024–2025) show MAD does not consistently outperform single-agent test-time compute strategies.
- **Methodology:** Multi-agent debate framework; evaluation on math, factual QA, chess; comparison to CoT and self-consistency baselines.

#### 2. AgentBench (ICLR 2024)
- **Significance:** 9/10 — (see Task Success section for full details)
- **Key Performance Findings:**
  - Performance on standard NLP benchmarks does NOT predict agent task success — agent-specific evaluation is necessary.
  - Commercial LLMs substantially outperform open-source models on multi-step agent tasks.

#### 3. MAST: Why Multi-Agent LLM Systems Fail (arXiv 2025)
- **Significance:** 9/10
- **Key Findings:**
  - First empirically grounded failure taxonomy for multi-agent LLM systems.
  - **14 failure modes** in 3 clusters: system design issues, inter-agent misalignment, and task verification failures.
  - Derived from 150 annotated traces, validated across 1600+ traces from 7 popular MAS frameworks; inter-annotator agreement kappa=0.88.
  - Failure patterns differ significantly across model families (GPT-4 vs. Claude 3 vs. Qwen2.5).
- **Methodology:** Qualitative failure analysis; LLM-as-judge annotation pipeline; multi-framework evaluation (AutoGen, CrewAI, etc.).

#### 4. Multi-Agent Survey (IJCAI 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Comprehensive taxonomy covering agent profiling, environment interaction, communication topologies (peer-to-peer, centralized, shared message pool), and capability acquisition.
  - Orchestration is the pivotal challenge at scale; existing benchmarks evaluate narrow scenarios, overlooking complex emergent behaviors.
  - Performance gains from multi-agent approaches are highly task-dependent.
- **Methodology:** Systematic literature review; taxonomy construction; gap analysis across 200+ papers.

#### 5. MultiAgentBench (ACL 2025)
- **Significance:** 8/10 — (see Task Success section for full details)
- **Key Performance Findings:**
  - Graph coordination topology outperforms star/chain/tree structures.
  - Significant variance in performance across tasks and coordination strategies.

---

### Well-Established Findings (Multi-Agent Performance)

1. Multi-agent debate improves reasoning on math and factual QA tasks compared to single-agent baselines (ICML 2024), though margins are smaller than initially claimed.
2. Performance on standard NLP benchmarks does not predict multi-agent task success — agent-specific benchmarks are necessary.
3. Task decomposition and role specialization improves performance on breadth-first tasks by up to 90% vs. single agents.
4. Inter-agent communication topology has significant impact on both performance and communication overhead.
5. 14 empirically validated failure modes exist across multi-agent systems (MAST, 2025).

### Mixed / Contradictory Results (Multi-Agent Performance)

1. **Multi-agent debate (MAD):** Does not consistently outperform single-agent test-time compute strategies across all tasks (ICLR 2025 analysis).
2. **Emergent coordination:** "Greater-than-sum-of-parts" effects are often not replicated across different task types and model combinations.
3. **SWE-bench reliability:** Vulnerable to reward hacking (Berkeley/RDI, April 2026) — benchmark reliability contested.
4. **Theory of Mind:** LLM agents excel at environment-variable-driven decisions but struggle with partner-belief reasoning; significantly below human-level.

### Research Gaps (Multi-Agent Performance)

1. Standardized evaluation frameworks measuring both task success AND coordination quality (communication efficiency, role adherence, consensus quality) jointly.
2. Formal understanding of when multi-agent systems outperform single agents — current evidence is empirical and task-specific.
3. Long-horizon multi-agent task evaluation (tasks requiring 50+ steps and hours of agent runtime).
4. Benchmark resilience to reward hacking and contamination in agentic settings.
5. Evaluation of multi-agent systems in safety-critical domains (medical diagnosis, legal reasoning) where hallucination cascades are unacceptable.
6. Systematic study of emergent behaviors (beneficial and harmful) in large agent networks (50–100 agents).

---

## Industry Best Practices

### Performance — Multi-Turn
- **Anthropic:** Multi-turn evals focus on instruction retention, self-coherence, and task completion rates; uses Claude models with extended context windows.
- **OpenAI:** ChatGPT uses conversation summaries and memory features (opt-in) for very long sessions; evaluates with human preference A/B testing.
- **Google (Gemini):** Evaluated on SSA (Sensibleness, Specificity, Interestingness) and grounding metrics; Gemini 2.5 reports near-perfect retrieval at 2M tokens.
- **Meta:** LLaMA-based dialogue systems evaluated on MT-Bench and custom internal benchmarks; open-source evaluation scripts released.
- **Cohere (Command R):** Specifically optimized for multi-turn RAG; evaluated on retrieval accuracy and faithfulness across conversation turns.

### Performance — Multi-Agent
- **Anthropic:** Engineering blog on multi-agent research system architecture; orchestrator+subagent pattern; parallel subagent execution for independent subtasks; detailed task descriptions to prevent agent duplication.
- **OpenAI (Agents SDK):** Handoff primitives; model routing between GPT-4o and GPT-4o-mini; built-in tool-call reliability monitoring.
- **Google (ADK + A2A):** SWE-bench performance as primary engineering metric; Magentic-One-style generalist orchestrator with specialist sub-agents.
- **Microsoft (AutoGen 0.4, Jan 2025):** Modular memory and orchestration; merging AutoGen + Semantic Kernel (Oct 2025) for production deployments.
- **General consensus:** Milestone-based KPIs outperform simple task-success metrics; human-in-the-loop reduces error rates by **60%** in production deployments.

---

*Last updated: 2026-05-17*
