# Human-AI Interaction in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** CHI, FAccT, ACM JRC, arXiv (DeepMind Safety)

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Understanding the Effects of Miscalibrated AI Confidence on User Trust | Multiple authors | arXiv 2024 | 2024 | https://arxiv.org/html/2402.07632v4 |
| 2 | Measuring and Mitigating Overreliance is Necessary for Human-Compatible AI | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2509.08010v1 |
| 3 | A Systematic Review on Fostering Appropriate Trust in Human-AI Interaction | Multiple authors | ACM JRC 2024 | 2024 | https://dl.acm.org/doi/10.1145/3696449 |
| 4 | CUI@CHI 2024: Building Trust in Conversational User Interfaces | CUI Community | CHI 2024 | 2024 | https://dl.acm.org/doi/fullHtml/10.1145/3613905.3636287 |
| 5 | Is Conversational XAI All You Need? | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2501.17546v1 |

### Paper Details

#### 1. Miscalibrated AI Confidence and User Trust (arXiv 2024)
- **Significance:** 9/10
- **Key Findings:**
  - LLMs expressing high certainty leads to user over-reliance **regardless of actual correctness**.
  - Reward modeling favors confident-sounding responses over accurate ones.
  - Miscalibrated confidence in multi-turn dialogue compounds across turns as users update trust based on prior confident (but incorrect) turns.
  - Proposes calibrated uncertainty expression as an essential design requirement.
- **Methodology:** User study measuring trust, reliance, and decision accuracy under varied AI confidence levels; multi-turn trust dynamics analysis.

#### 2. Measuring and Mitigating Overreliance (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - LLMs contribute to overreliance through anthropomorphic qualities of their natural language output.
  - **Overreliance is harder to detect and correct** in multi-turn settings where trust accumulates.
  - Argues that measuring and mitigating overreliance is a necessary condition for human-compatible AI.
- **Methodology:** Survey of overreliance mechanisms; user studies; analysis of LLM conversational features that drive anthropomorphization.

#### 3. Fostering Appropriate Trust in Human-AI Interaction (ACM JRC 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Fostering appropriate trust — neither over nor under — is the central challenge in human-AI interaction.
  - Transparency and explanation features often backfire in conversational settings, increasing overreliance.
  - Proposes trust calibration framework based on systematic AI strength/weakness communication.
- **Methodology:** Systematic review across FAccT, CHI, IUI, HRI (50 papers); taxonomy of trust-fostering mechanisms; meta-analysis of intervention effectiveness.

#### 4. CUI@CHI 2024: Building Trust in Conversational UIs (CHI 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Trust is the central thread across diverse conversational AI applications.
  - LLM-powered chatbots fundamentally changed trust dynamics vs. rule-based systems.
  - Trust design must account for anthropomorphization effects that lead to miscalibrated trust.
- **Methodology:** Workshop synthesis; literature review; design case studies; user experience research.

#### 5. Is Conversational XAI All You Need? (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Conversational explainable AI does **not reliably improve** human decision-making accuracy or calibration.
  - Interactive explanation formats sometimes worsen over-reliance.
  - Conversation format and explanation timing are critical design variables.
- **Methodology:** Controlled user study with conversational XAI assistant vs. static explanations; measurement of decision accuracy, calibration, and reliance.

---

### Well-Established Findings
1. LLMs' human-like conversational qualities systematically drive user overreliance.
2. Trust calibration is the central human-AI interaction challenge in conversational settings.
3. Multi-turn dialogue accumulates trust in ways that are difficult to reset when AI makes errors.

### Mixed Results
1. Whether conversational explanations improve or worsen human decision calibration.
2. Relative effectiveness of different uncertainty expression formats for trust calibration.
3. Whether user control mechanisms (like conversation resets) meaningfully improve trust calibration.

### Research Gaps
1. No longitudinal studies of trust dynamics in extended multi-turn human-AI dialogue.
2. Limited work on trust repair mechanisms after AI errors in conversational settings.
3. No standardized metrics for measuring trust calibration in conversational AI.
4. Insufficient study of how conversation history affects trust in deployment settings.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | The Role of Explainability in Collaborative Human-AI Disinformation Detection | Multiple authors | FAccT 2024 | 2024 | https://dl.acm.org/doi/10.1145/3630106.3659031 |
| 2 | Exploring Human-AI Collaboration Using Mental Models of Early Adopters | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2510.06224v1 |
| 3 | Human-AI Complementarity: A Goal for Amplified Oversight | DeepMind Safety Research | DeepMind Blog 2024 | 2024 | https://deepmindsafetyresearch.medium.com/human-ai-complementarity-a-goal-for-amplified-oversight-0ad8a44cae0a |
| 4 | LLM-Based Human-Agent Collaboration and Interaction Systems: A Survey | Multiple authors | arXiv 2025 | 2025 | https://arxiv.org/html/2505.00753v4 |
| 5 | ChatCollab: Exploring Collaboration Between Humans and AI Agents in Software Teams | Multiple authors | arXiv 2024 | 2024 | https://arxiv.org/html/2412.01992v1 |

### Paper Details

#### 1. Explainability in Collaborative Human-AI Disinformation Detection (FAccT 2024)
- **Significance:** 9/10 — (see Interpretability section for full details)
- **Human-AI Interaction finding:** Explanation features do not reliably produce complementarity and may worsen over-reliance; human-centered explanation design is essential.

#### 2. Mental Models of Early Adopters of Multi-Agent AI Tools (arXiv 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Multi-agent generative AI introduces qualitatively new complexity in human oversight.
  - Users struggle to form accurate mental models of how multiple agents coordinate.
  - Clear communication strategies and well-defined roles are critical for user satisfaction.
- **Methodology:** Qualitative study of early adopters; mental model elicitation; thematic analysis of collaboration patterns.

#### 3. Human-AI Complementarity (DeepMind Safety 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Proposes human-AI complementarity (where the human-AI team outperforms either alone) as the target metric for multi-agent oversight design.
  - Amplified oversight requires humans remain meaningfully in the loop as agent capabilities scale.
  - Current multi-agent systems are **not designed with human complementarity** as an optimization target.
- **Methodology:** Theoretical framework development; analysis of current human oversight mechanisms; proposals for complementarity-optimizing design.

#### 4. LLM-Based Human-Agent Collaboration Survey (arXiv 2025)
- **Significance:** 7/10
- **Key Findings:**
  - Continuous feedback loops between human and agent are essential for behavioral calibration, error mitigation, and confidence building.
  - Current multi-agent systems lack standardized human-agent interaction protocols.
  - Division of labor between humans and AI agents requires new interaction paradigms beyond chatbot norms.
- **Methodology:** Systematic survey of human-agent collaboration literature; taxonomy of interaction patterns; analysis of feedback loop mechanisms.

#### 5. ChatCollab: Humans and AI Agents in Software Teams (arXiv 2024)
- **Significance:** 7/10
- **Key Findings:**
  - Humans and AI agents in collaborative software teams face coordination challenges including turn-taking, authority, and accountability not present in human-only teams.
  - Trust and clear role definition are critical success factors.
  - Mixed human-AI teams require new interaction protocols distinct from both human-human and human-AI dyadic interaction.
- **Methodology:** Empirical study of human-AI agent collaboration in software engineering tasks; user experience measurement.

---

### Well-Established Findings (Multi-Agent Human-AI Interaction)
1. Users struggle to form accurate mental models of how multiple agents coordinate.
2. Human oversight complexity scales with agent count and requires new design paradigms.
3. Continuous feedback loops between humans and agent teams are essential for calibration.

### Research Gaps (Multi-Agent Human-AI Interaction)
1. No standardized metrics for measuring human oversight effectiveness in multi-agent systems.
2. Limited longitudinal studies of human trust dynamics in persistent multi-agent collaborations.
3. No established design patterns for human-in-the-loop multi-agent systems.
4. Insufficient study of authority and accountability dynamics in mixed human-AI agent teams.

---

## Industry Best Practices

### Human-AI Interaction — Multi-Turn
- Uncertainty expression design (hedging, confidence indicators).
- Escalation mechanisms to human agents when AI confidence is low.
- Regular capability disclosure to users in onboarding flows.

### Human-AI Interaction — Multi-Agent
- Human approval checkpoints at high-stakes agent decisions.
- Transparent agent role and capability disclosure to human collaborators.
- Escalation protocols for uncertain or high-consequence agent actions.

---

*Last updated: 2026-05-17*
