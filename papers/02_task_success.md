# Task Success & Goal Achievement in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** ICLR, NeurIPS, ACL, EMNLP, IJCAI, TACL, arXiv (widely adopted industry benchmarks)

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | WebArena: A Realistic Web Environment for Building Autonomous Agents | Zhou et al. | ICLR 2024 | 2024 | https://arxiv.org/abs/2307.13854 |
| 2 | MINT: Evaluating LLMs in Multi-turn Interaction with Tools and Language Feedback | Wang et al. | ICLR 2024 | 2024 | https://arxiv.org/abs/2309.10691 |
| 3 | tau-bench: A Benchmark for Tool-Agent-User Interaction in Real-World Domains | Yao et al. (Sierra) | arXiv 2024 | 2024 | https://arxiv.org/abs/2406.12045 |
| 4 | ComplexBench: Benchmarking Complex Instruction-Following with Multiple Constraints | He et al. | NeurIPS 2024 | 2024 | https://proceedings.neurips.cc/paper_files/paper/2024/file/f8c24b08b96a08ec7a7a975feea7777e-Paper-Datasets_and_Benchmarks_Track.pdf |
| 5 | Evaluating LLM-based Agents for Multi-Turn Conversations: A Survey | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/pdf/2503.22458 |

### Paper Details

#### 1. WebArena (ICLR 2024)
- **Significance:** 10/10
- **Key Findings:**
  - GPT-4 with CoT achieves only **11.70%** end-to-end task success vs. **78.24%** human performance on 812 long-horizon web tasks.
  - Reveals severe gaps in grounding, planning, and multi-step execution; SoTA agents have since climbed to ~60–68% by 2026.
  - Self-hosted environment with fully functional websites (e-commerce, forums, code repos, CMS).
- **Methodology:** Functional correctness evaluation (goal-state achievement regardless of path).

#### 2. MINT (ICLR 2024)
- **Significance:** 9/10
- **Key Findings:**
  - LLMs benefit from tools and language feedback: 1–8% per tool-use turn, 2–17% with natural language feedback.
  - **Better single-turn performance does NOT guarantee better multi-turn performance** — a critical finding.
  - RLHF and supervised instruction-finetuning (SIFT) **hurt** multi-turn capabilities.
- **Methodology:** 20 LLMs evaluated on multi-turn interactions using Python tool execution and GPT-4-simulated user feedback; covers reasoning, coding, and decision-making.

#### 3. tau-bench (arXiv 2024)
- **Significance:** 9/10
- **Key Findings:**
  - State-of-the-art function-calling agents (including GPT-4o) succeed on **fewer than 50%** of tasks; pass^8 reliability below 25% in retail scenarios.
  - Agents struggle with complex policy-constrained reasoning, compound multi-step requests, and maintaining consistency across long turns.
  - Introduces the **pass^k reliability metric** — now an emerging industry standard.
- **Methodology:** Multi-turn simulation of user-agent dialogues in retail and airline customer service; measures final database-state alignment.

#### 4. ComplexBench (NeurIPS 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Identifies dependency structures between constraint types (AND/OR/chain compositions) that LLMs cannot reliably satisfy simultaneously across conversation turns.
  - Significant deficiencies in all current LLMs on complex multi-constraint instructions.
- **Methodology:** LLM-based evaluators augmented with rules to verify each constraint satisfaction; organized around dependency-structure types.

#### 5. Survey: Evaluating LLM-based Agents for Multi-Turn Conversations (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Multi-turn task completion requires contextual coherence, error propagation mitigation, and adaptation to evolving user intents.
  - Standard metrics: Task Success Rate (TSR), Task Goal Completion (TGC), Pass Rate.
  - Evaluation methodologies: annotation-based, automated, hybrid, LLM-as-judge.
- **Methodology:** Comprehensive literature survey across multi-turn evaluation dimensions.

---

### Well-Established Findings

1. Task Success Rate (TSR) as a binary/continuous metric is the de facto standard, validated across WebArena, tau-bench, MINT, IFEval.
2. Tools and external feedback improve multi-turn task performance by measurable margins (1–17%) over pure language reasoning.
3. GPT-4-class models substantially outperform open-source models under 70B parameters on multi-turn task success (AgentBench finding).
4. LLMs "get lost" in long multi-turn conversations: context drift and error accumulation degrade goal-achievement rates.
5. Human performance on web-task benchmarks (WebArena ~78%, OSWorld ~72%) remains significantly above AI agents.

### Mixed / Contradictory Results

1. **RLHF/SIFT alignment:** MINT found alignment hurts multi-turn capabilities; yet other work shows alignment improves compliance and helpfulness. Trade-off unresolved.
2. **Chain-of-thought in multi-turn:** Improves reasoning in some settings but doesn't consistently transfer to multi-step goal achievement.
3. **Memory-augmented agents:** MemGuide raises task success by 11% on MS-TOD (88%→99%), but gains vary dramatically by domain and memory architecture.
4. **Scale and multi-turn performance:** Large models sometimes underperform smaller, task-specialized agents on specific multi-turn benchmarks.

### Research Gaps

1. Long multi-turn benchmarks (>7 turns) are scarce; most have fewer than 7 turns and don't model interleaved topic changes or backtracking.
2. No consensus on standardized metrics for "goal-shift" during conversations (partial completion, mid-conversation objective changes).
3. Multilingual and cross-cultural multi-turn evaluation is immature.
4. Reliable evaluation without human annotation at scale is unsolved; LLM-as-judge introduces systematic biases.
5. Error propagation and recovery mechanisms across conversation turns are under-studied.
6. Evaluation of truly open-domain, user-initiated multi-turn tasks (rather than predefined templates) is largely missing.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | AgentBench: Evaluating LLMs as Agents | Liu et al. (Tsinghua THUDM) | ICLR 2024 | 2024 | https://arxiv.org/abs/2308.03688 |
| 2 | AgentVerse: Facilitating Multi-Agent Collaboration and Exploring Emergent Behaviors | Chen, Su et al. (OpenBMB/Tsinghua) | ICLR 2024 | 2024 | https://arxiv.org/abs/2308.10848 |
| 3 | Magentic-One: A Generalist Multi-Agent System for Solving Complex Tasks | Fourney, Bansal et al. (Microsoft Research) | arXiv 2024 | 2024 | https://arxiv.org/abs/2411.04468 |
| 4 | MultiAgentBench: Evaluating the Collaboration and Competition of LLM Agents | Zhu, Du et al. (UIUC, Tsinghua) | ACL 2025 | 2025 | https://arxiv.org/abs/2503.01935 |
| 5 | Reflective Multi-Agent Collaboration based on LLMs (COPPER) | Multiple authors | NeurIPS 2024 | 2024 | https://proceedings.neurips.cc/paper_files/paper/2024/file/fa54b0edce5eef0bb07654e8ee800cb4-Paper-Conference.pdf |

### Paper Details

#### 1. AgentBench (ICLR 2024)
- **Significance:** 10/10
- **Key Findings:**
  - 8 diverse environments (OS, DB, knowledge graphs, web shopping, web browsing, household simulation, card games, lateral-thinking puzzles).
  - Significant disparity between commercial (GPT-4) and open-source models; poor long-term reasoning and instruction following are main obstacles.
  - A 70% aggregate score can mask **zero performance** in certain environments.
- **Methodology:** Multi-environment benchmark; evaluates reasoning, decision-making, and tool use via success rate (SR).

#### 2. AgentVerse (ICLR 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Four-stage process (Expert Recruitment, Collaborative Decision-Making, Action Execution, Evaluation) outperforms single agents on text understanding, reasoning, coding, tool use, and embodied AI.
  - Emergent collaborative behaviors improve group efficiency.
- **Methodology:** Dynamic group composition; evaluated across multiple task types.

#### 3. Magentic-One (Microsoft Research, 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Orchestrator-led architecture with specialized sub-agents (WebSurfer, FileSurfer, Coder, ComputerTerminal) achieves competitive performance on GAIA, AssistantBench, and WebArena.
  - Re-planning on failure is a viable path to robust agentic task completion.
- **Methodology:** Orchestrator plans, tracks progress, and re-plans; evaluated on three major agentic benchmarks.

#### 4. MultiAgentBench (ACL 2025)
- **Significance:** 9/10
- **Key Findings:**
  - **Graph coordination topology outperforms star/chain/tree** structures.
  - Cognitive planning improves milestone achievement rates by 3%.
  - First benchmark measuring both task completion quality AND collaboration/competition quality.
- **Methodology:** Diverse interactive multi-agent scenarios; novel milestone-based KPIs.

#### 5. COPPER (NeurIPS 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Addresses the credit assignment problem in multi-agent collaboration via counterfactual PPO and counterfactual rewards.
  - Improvements on multi-hop QA, mathematics, and chess.
- **Methodology:** Counterfactual PPO-based reflector fine-tuning; experiments on 3 diverse collaborative datasets.

---

### Well-Established Findings (Multi-Agent Task Success)

1. Multi-agent systems outperform single agents on complex, long-horizon tasks requiring diverse skill sets (AgentVerse, Magentic-One, COPPER).
2. Orchestrator-plus-specialized-agents architecture provides robust task recovery via re-planning — a dominant agentic design pattern.
3. Task success is highly sensitive to coordination topology; graph-based coordination outperforms hierarchical structures (MultiAgentBench).
4. Commercial LLMs (GPT-4 class) substantially outperform open-source models in multi-agent agentic settings (AgentBench, consistently replicated).
5. TheAgentCompany (2024): Even the best agent completes only **24%** of consequential real-world workplace tasks autonomously.

### Mixed / Contradictory Results (Multi-Agent Task Success)

1. **Multi-agent debate:** Improves factuality and reasoning but adds significant computational overhead; gains are task-dependent and don't uniformly exceed single expert-agent approaches.
2. **Emergent collaborative behaviors (AgentVerse):** Observed but not fully understood or reproducible across different LLM families.
3. **Credit assignment:** COPPER proposes counterfactual rewards, but not yet generalized across all collaborative task types.
4. **Increasing number of agents:** Shows diminishing returns and can introduce coordination overhead that reduces net task success rate.

### Research Gaps (Multi-Agent Task Success)

1. No standardized benchmark for multi-agent task decomposition quality (measuring how well a task is split, not just final outcome).
2. Long-horizon benchmarks with >50-step task horizons show task success rates dropping dramatically (~23%), indicating an unsolved long-horizon gap.
3. Human-AI teaming in multi-agent settings (where humans are one of the agents) is under-benchmarked.
4. Cross-agent knowledge sharing and persistent shared memory across agent boundaries is an open research problem.
5. Robustness and failure recovery in partially observable multi-agent environments remains poorly characterized.
6. Agent role specialization vs. generalization trade-offs not quantitatively studied at scale.

---

## Industry Best Practices

### Task Success — Multi-Turn
- **Sierra's tau-bench:** Dominant industry benchmark for customer service agents; adopted by Anthropic for Claude 3.5/3.7 evaluation.
- **Pass^k reliability metric:** Emerging industry standard for measuring agent consistency across repeated trials.
- **LLM-as-judge (GPT-4):** Widely used in production evaluation pipelines despite known biases.
- **LMSYS Chatbot Arena:** Multi-turn testing providing real-user preference signal at scale.

### Task Success — Multi-Agent
- **Microsoft AutoGen:** Dominant open-source multi-agent orchestration infrastructure (underpinning Magentic-One).
- **GAIA benchmark (Meta, 2023):** Widely used in industry leaderboards for general AI assistant capabilities.
- **SWE-bench / SWE-bench Verified:** Primary software engineering agent benchmark; Verified/Pro variants adopted to address benchmark contamination.
- **OSWorld (NeurIPS 2024):** Emerging standard for computer-use agent evaluation in real desktop environments.
- **TheAgentCompany (2024):** Benchmark of consequence; 24% completion rate establishes realistic baseline for enterprise expectations.

---

*Last updated: 2026-05-17*
