# Robustness in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** ICLR, EMNLP, NeurIPS, arXiv (Microsoft Research, CMU)

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | LLMs Get Lost In Multi-Turn Conversation | Laban, Hayashi, Zhou, Neville (Microsoft) | arXiv 2025 | 2025 | https://arxiv.org/abs/2505.06120 |
| 2 | Evaluating the Sensitivity of LLMs to Prior Context | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2506.00069v1 |
| 3 | Are Code Language Models Robust Against Multi-Turn Adversarial Prompts? | Multiple authors | Findings of EMNLP 2025 | 2025 | https://aclanthology.org/2025.findings-emnlp.1249.pdf |
| 4 | Revisiting Out-of-Distribution Robustness in NLP | Multiple authors | NeurIPS Workshop 2023 | 2023 | https://arxiv.org/abs/2306.04618 |
| 5 | Drift No More? Context Equilibria in Multi-Turn LLM Interactions | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2510.07777v1 |

### Paper Details

#### 1. LLMs Get Lost In Multi-Turn Conversation (arXiv 2025)
- **Significance:** 9/10
- **Key Findings:**
  - All top open- and closed-weight LLMs show an average **39% performance drop** in multi-turn vs. single-turn settings across six generation tasks.
  - LLMs make early wrong assumptions and fail to recover; degradation decomposes into minor aptitude loss + major increase in unreliability.
  - LLMs prematurely generate final solutions and over-rely on them even when incorrect.
- **Methodology:** 200,000+ simulated multi-turn conversations across Python programming, SQL, API calling, math, data2text, summarization.

#### 2. Sensitivity of LLMs to Prior Context (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Performance on multiple-choice questions can degrade by up to **73%** for certain models in multi-turn interactions.
  - Evaluates GPT, Claude, and Gemini across benchmarks systematically varying volume and nature of prior context.
  - Sensitivity to prior context is a fundamental reliability issue in multi-turn systems.
- **Methodology:** Novel benchmarks systematically varying prior context volume and nature; measured sensitivity to contextual variations.

#### 3. Code LLMs Robustness Against Multi-Turn Adversarial Prompts (EMNLP 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Code Decomposition Attacks elicit harmful functionality through benign-looking multi-turn interactions.
  - Malicious functionality distributed across turns is harder to detect than single-turn attacks.
  - Multi-turn jailbreaks are substantially more effective and harder to defend against.
- **Methodology:** Multi-turn adversarial prompts via code decomposition; tested on code LLMs; compared with single-turn attack success rates.

#### 4. OOD Robustness in NLP (NeurIPS Workshop 2023)
- **Significance:** 7/10
- **Key Findings:**
  - LLMs exhibit stronger OOD robustness than smaller models but still fail significantly under covariate and semantic shifts.
  - Distributional assumptions embedded in benchmarks confound robustness evaluations.
- **Methodology:** Multi-domain OOD benchmarks; evaluated LLMs alongside fine-tuned models; analysis of different distribution shift types.

#### 5. Drift No More? Context Equilibria (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Formalizes alignment drift using KL divergence metrics; LLMs progressively deviate from initial alignment constraints as turns accumulate.
  - Proposes context equilibria as a theoretical framework for stable vs. drifting conversational states.
- **Methodology:** KL divergence-based drift measurement; theoretical formalization; multi-model evaluation.

---

### Well-Established Findings
1. Multi-turn performance shows average 39% drop vs. single-turn across task types.
2. LLMs fail to recover when they make wrong assumptions early in conversations.
3. Context length alone hurts performance even when retrieval is perfect.
4. Multi-turn jailbreaks are more effective than single-turn adversarial attacks.

### Mixed Results
1. Whether larger models are more robust to multi-turn degradation is inconsistent across studies.
2. Relative impact of context accumulation vs. task complexity on degradation is unclear.
3. Whether fine-tuned or prompted models are more robust to multi-turn adversarial attacks.

### Research Gaps
1. No standardized benchmarks specifically measuring multi-turn OOD robustness.
2. No established metrics for cross-turn consistency under distribution shift.
3. Limited study of robustness in domain-specific multi-turn conversations (medical, legal).
4. No dedicated adversarial training methods for multi-turn dialogue robustness.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Dissecting Adversarial Robustness of Multimodal LM Agents | Wu et al. (CMU) | ICLR 2025 | 2024 | https://arxiv.org/abs/2406.12814 |
| 2 | AgentHarm: A Benchmark for Measuring the Harmfulness of LLM Agents | Multiple authors | ICLR 2025 | 2024 | https://arxiv.org/pdf/2410.09024 |
| 3 | Why Do Multi-Agent LLM Systems Fail? | Cemri et al. | ICLR 2025 | 2025 | https://iclr.cc/virtual/2025/33314 |
| 4 | Towards a Science of AI Agent Reliability | Rabanser, Kapoor et al. | arXiv 2026 | 2026 | https://arxiv.org/abs/2602.16666 |
| 5 | Robust Cooperative MARL via Adversary Generation | Multiple authors | Science China Information Sciences | 2024 | http://scis.scichina.com/en/2024/142102.pdf |

### Paper Details

#### 1. Adversarial Robustness of Multimodal LM Agents (ICLR 2025)
- **Significance:** 10/10
- **Key Findings:**
  - All evaluated agents including GPT-4o-based agents can be hijacked with success rates up to **67%**, triggered by imperceptible image perturbations occupying <5% of web page pixels.
  - ARE (Agent Robustness Evaluation) framework models agents as graphs tracking adversarial information flow across components.
  - Compound agent systems introduce unique vulnerability surfaces not present in single-model settings.
- **Methodology:** 200 targeted adversarial tasks on VisualWebArena-Adv; ARE framework; black-box adversarial perturbations on multimodal web agents.

#### 2. AgentHarm (ICLR 2025)
- **Significance:** 9/10 — (see Safety section for full details)
- **Robustness-specific findings:** Robustness in single-turn chatbot settings has limited implications for multi-step agent robustness — categorically different challenges.

#### 3. Why Do Multi-Agent LLM Systems Fail? (ICLR 2025)
- **Significance:** 9/10
- **Key Findings:**
  - 18 fine-grained failure modes across 4 categories: specification ambiguities, organizational breakdowns, coordination gaps, weak verification.
  - Multi-agent performance gains over single-agent baselines remain minimal on many tasks due to robustness failures.
- **Methodology:** Human annotation of failures across 5 MAS on 150+ tasks; taxonomy of 18 failure modes.

#### 4. Towards a Science of AI Agent Reliability (arXiv 2026)
- **Significance:** 9/10
- **Key Findings:**
  - 12-metric reliability framework across 4 dimensions: consistency, robustness, predictability, safety.
  - Outcome consistency ranges 30–75% across 14 evaluated models; recent capability gains yield only small reliability improvements.
  - Predictability is the weakest dimension — most models cannot distinguish their correct from incorrect predictions better than chance.
- **Methodology:** 12 reliability metrics grounded in safety-critical engineering; evaluated 14 agentic models across two complementary benchmarks.

#### 5. Robust Cooperative MARL via Adversary Generation (SCIS 2024)
- **Significance:** 7/10
- **Key Findings:**
  - Communication hallucinations from adversarial agents cascade through multi-agent networks.
  - Adaptively generated adversaries during training improve OOD coordination robustness substantially.
- **Methodology:** Auxiliary adversary agent generation; tested on cooperative MARL benchmarks with communication channel attacks.

---

### Well-Established Findings (Multi-Agent Robustness)
1. Adversarial perturbations transfer effectively from single-component to compound multi-agent systems.
2. Multi-step agent pipelines face categorically different robustness challenges than single-turn chatbots.
3. Communication channel attacks cascade through multi-agent networks.
4. Coordination failures are the primary driver of multi-agent robustness failures.

### Mixed Results (Multi-Agent Robustness)
1. Whether larger agent populations increase or decrease adversarial robustness.
2. Relative robustness of centralized vs. decentralized multi-agent architectures.
3. Whether reflection and self-correction mechanisms improve adversarial robustness.

### Research Gaps (Multi-Agent Robustness)
1. No standardized adversarial robustness benchmark for LLM-based multi-agent systems.
2. Limited work on OOD robustness when agent team composition changes at deployment.
3. No formal adversarial training frameworks for multi-agent LLM coordination.
4. Insufficient study of cascading failures across heterogeneous agent types.

---

## Industry Best Practices

### Multi-Turn
- Context window management and summarization to mitigate drift.
- Red-teaming with multi-turn adversarial scenarios.
- RAG-augmented grounding to maintain factual stability across turns.

### Multi-Agent
- Agent sandboxing and action monitoring to contain adversarial propagation.
- Red-teaming multi-agent pipelines end-to-end.
- Input validation and output verification at agent boundaries.

---

*Last updated: 2026-05-17*
