# Fairness & Bias in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** FAccT, ACL, EMNLP, IJCAI, AIES, Computational Linguistics

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Bias and Fairness in Large Language Models: A Survey | Gallegos et al. | Computational Linguistics (MIT Press / ACL) | 2024 | https://aclanthology.org/2024.cl-3.8/ |
| 2 | Fairness Feedback Loops: Training on Synthetic Data Amplifies Bias | Multiple authors (MIT) | FAccT 2024 | 2024 | https://dl.acm.org/doi/10.1145/3630106.3659029 |
| 3 | Large Language Models are Not Fair Evaluators | Wang et al. | ACL 2024 | 2024 | https://aclanthology.org/2024.acl-long.511/ |
| 4 | Evaluating Bias in Spoken Dialogue LLMs for Real-World Decisions | Multiple authors | arXiv 2024 | 2024 | https://arxiv.org/html/2510.02352v1 |
| 5 | Systematic Biases in LLM Simulations of Debates | Multiple authors | EMNLP 2024 | 2024 | https://aclanthology.org/2024.emnlp-main.16.pdf |

### Paper Details

#### 1. Bias and Fairness in LLMs: A Survey (Computational Linguistics 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Proposes taxonomies of bias evaluation datasets (counterfactual inputs vs. prompts) and classifies mitigation methods across pre-processing, in-training, intra-processing, and post-processing stages.
  - Multi-turn dialogue systems can **amplify demographic biases** relative to single-turn interactions due to compounding contextual assumptions.
  - Critical gaps in consistent bias measurement across conversational contexts.
- **Methodology:** Systematic survey of 100+ papers; taxonomy construction; categorization of datasets and mitigation strategies.

#### 2. Fairness Feedback Loops: Synthetic Data Amplifies Bias (FAccT 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Chains of generative models trained on synthetic data from predecessors converge to majority representation and amplify model mistakes.
  - This **model-induced distribution shift (MIDS)** disproportionately impacts minoritized groups.
  - Proposes algorithmic reparation (AR) as a mitigation strategy.
  - Especially relevant for dialogue systems trained iteratively on synthetic conversation data.
- **Methodology:** Multi-generational model training and evaluation; analysis of performance and fairness properties across generations.

#### 3. LLMs are Not Fair Evaluators (ACL 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Positional bias in LLM-as-judge evaluation can alter quality rankings by changing response order of appearance.
  - This positional bias affects multi-turn dialogue evaluation where turn ordering matters.
  - Proposes calibration strategies to reduce positional bias.
- **Methodology:** Systematic manipulation of response ordering in LLM judge settings; statistical analysis of positional bias effects.

#### 4. Evaluating Bias in Spoken Dialogue LLMs (arXiv 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Paralinguistic attributes (age, gender, accent) consistently influence model judgments in spoken dialogue LLMs.
  - Biases **persist and intensify** under multi-turn conversations with repeated feedback.
  - Decision outputs should remain consistent across demographic attributes but do not.
- **Methodology:** Compared model outputs across speakers with varying paralinguistic attributes; tested across multi-turn feedback conditions.

#### 5. Systematic Biases in LLM Simulations of Debates (EMNLP 2024)
- **Significance:** 7/10
- **Key Findings:**
  - LLMs exhibit systematic biases when simulating multi-turn debates, consistently favoring certain ideological and demographic positions.
  - Simulation biases **compound across turns** as agents build on prior turns.
  - Bias pattern reflects training data demographics rather than argument merit.
- **Methodology:** Simulated multi-turn debates with varied agent personas; measured position change and bias patterns across turns.

---

### Well-Established Findings
1. LLMs exhibit demographic biases that manifest consistently in multi-turn dialogue.
2. Positional and order biases affect fairness of LLM evaluation in conversational settings.
3. Training on synthetic dialogue data can amplify existing demographic biases.

### Mixed Results
1. Whether multi-turn interaction mitigates or amplifies single-turn biases.
2. The degree to which bias mitigation techniques for single-turn generalize to multi-turn.
3. How conversational context influences the severity of demographic bias.

### Research Gaps
1. No dedicated benchmarks for measuring demographic bias specifically in multi-turn conversation settings.
2. Limited longitudinal studies of how bias evolves across conversation turns.
3. Insufficient work on intersectional bias in multi-turn dialogue.
4. No standardized fairness metrics specifically designed for conversational AI.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Interactional Fairness in LLM Multi-Agent Systems: An Evaluation Framework | Binkyte | AIES 2025 | 2025 | https://ojs.aaai.org/index.php/AIES/article/view/36563 |
| 2 | Towards Fairer AI: Multi-Agent Debiasing of LLMs With Online Evidence Retrieval | Multiple authors | AAAI Symposium 2024 | 2024 | https://ojs.aaai.org/index.php/AAAI-SS/article/download/36874/39012 |
| 3 | Emergent Bias and Fairness in Multi-Agent Decision Systems | Multiple authors | arXiv 2024 | 2024 | https://arxiv.org/pdf/2512.16433 |
| 4 | Fairness in AI Multi-Agent: Foundation, Framework and Implementation | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/pdf/2502.07254 |
| 5 | A Survey on Intersectional Fairness in Machine Learning | Multiple authors | IJCAI 2023 | 2023 | https://www.ijcai.org/proceedings/2023/0742.pdf |

### Paper Details

#### 1. Interactional Fairness in LLM Multi-Agent Systems (AIES 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Introduces a framework for evaluating **interactional fairness** (interpersonal respect and justification adequacy) in LLM-based MAS.
  - Tone and justification quality significantly affect acceptance decisions even when objective outcomes are held constant.
  - Fairness must be understood as a socially interpretable behavioral signal rather than a subjective experience.
- **Methodology:** Adapted Colquitt's Scale and Critical Incident Technique from organizational justice research; controlled simulations of resource negotiation.

#### 2. Towards Fairer AI: Multi-Agent Debiasing (AAAI Symposium 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Multi-agent debiasing framework with online evidence retrieval lifts accuracy by **+8 percentage points** and cuts directional bias by -0.08 on ambiguous prompts.
  - GPT-4 shows the largest gain from multi-agent debiasing.
  - Multi-agent architectures can be leveraged to **actively mitigate** rather than amplify bias.
- **Methodology:** Multi-agent pipeline with dedicated debiasing agents and evidence retrieval; evaluation on ambiguous prompt benchmarks.

#### 3. Emergent Bias in Multi-Agent Decision Systems (arXiv 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Bias toward specific social conventions amplifies in multi-agent decision systems.
  - Financial multi-agent systems show particularly pronounced fairness-related emergent bias.
  - Malicious agents can undermine fairness by exploiting system weaknesses.
- **Methodology:** Simulation of multi-agent decision systems in financial domain; analysis of bias amplification patterns; adversarial agent injection.

#### 4. Fairness in AI Multi-Agent: Foundation, Framework and Implementation (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Competitive resource allocation is the primary fairness-critical scenario in MAS.
  - Proposes three fairness dimensions for MAS: **procedural, distributive, and interactional**.
  - Adversarial robustness and fairness are deeply intertwined.
- **Methodology:** Theoretical framework development; taxonomy of fairness scenarios in MAS; implementation guidelines.

#### 5. Intersectional Fairness in Machine Learning (IJCAI 2023)
- **Significance:** 7/10
- **Key Findings:**
  - Single-attribute fairness constraints fail to capture intersectional disparities.
  - Current multi-agent systems do not account for intersectional identities.
  - Identifies key open problems in extending fairness constraints to distributed multi-agent architectures.
- **Methodology:** Systematic survey of fairness notions, metrics, and approaches; analysis of intersectional vs. single-attribute fairness.

---

### Well-Established Findings (Multi-Agent Fairness)
1. Multi-agent systems can both amplify and (with proper design) mitigate bias relative to single-agent systems.
2. Interactional fairness is a distinct dimension from distributional fairness in MAS.
3. Competitive resource allocation creates the most acute fairness challenges in multi-agent settings.

### Mixed Results (Multi-Agent Fairness)
1. Whether increasing agent diversity reduces or increases aggregate system bias.
2. How fairness guarantees in individual agent interactions aggregate to system-level fairness.
3. Relative effectiveness of centralized vs. decentralized fairness enforcement.

### Research Gaps (Multi-Agent Fairness)
1. No standardized fairness benchmarks specifically for LLM-based multi-agent systems.
2. Limited work on intersectional fairness in multi-agent conversational settings.
3. No formal frameworks for auditing emergent fairness properties in large MAS.
4. Insufficient study of fairness under adversarial agent injection.

---

## Industry Best Practices

### Fairness — Multi-Turn
- Red-teaming for demographic bias in conversational scenarios.
- Bias auditing of training data for dialogue systems.
- RLHF with diversity-aware preference data.

### Fairness — Multi-Agent
- Diversity requirements in agent team composition.
- Fairness monitoring agents as dedicated oversight components.
- Algorithmic reparation mechanisms in iterative multi-agent pipelines.

---

*Last updated: 2026-05-17*
