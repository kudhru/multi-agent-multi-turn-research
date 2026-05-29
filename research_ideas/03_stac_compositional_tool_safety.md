# Research Idea 3: Compositional Tool Safety — When Safe Calls Become Dangerous Chains

> **One-line pitch:** LLM agent safety mechanisms operate per-call, but harm can be a property of call *sequences* — we provide the first formal compositional model of tool-call safety and demonstrate a class of attacks requiring no attacker-controlled user input.

---

## Research Question

Can we formally characterize which sequences of individually-permitted tool calls collectively constitute a security violation? And when the attacker controls only the *environment* (web pages, files, API responses), not the user turn, how exploitable are current agents via environmental tool-chaining?

---

## Prior Work Landscape

### What Already Exists (the space is more active than expected)

| Paper | Venue | What they do |
|-------|-------|-------------|
| STAC: When Innocent Tools Form Dangerous Chains | arXiv 2509.25624, 2025 | **Names the threat class.** 483 cases, 1,352 interaction sets; attack pipeline using GPT-4.1 to synthesize chains; >90% ASR; proposes reasoning-driven defense (-28.8% ASR) |
| AgentLAB | arXiv 2602.16901, 2026 | First benchmark with tool chaining as an explicit named attack type; 5 attack types, 644 test cases, 28 environments; >70% ASR against GPT-5.1 |
| MAGE (Shadow Memory defense) | arXiv 2605.03228, 2026 | Shadow memory defense for long-horizon threats; reduces STAC ASR from 100% → 8.3% at 7K extra tokens/task |
| Monitoring Decomposition Attacks | arXiv 2506.10949, 2025 | Sequential monitors for "decomposition attacks" (benign subtasks → harmful whole); 93% defense success on GPT-4o |
| Mind the GAP | arXiv 2602.16943, 2026 | Measures text refusal vs. tool-call refusal divergence; 17,420 datapoints; shows safety mechanism operates at wrong layer |
| AgentDojo | NeurIPS 2024 | 629 security cases; prompt injection into tool responses in multi-step flows; does not isolate individually-benign chaining |
| Agent Security Bench (ASB) | ICLR 2025 | 400+ tools, 27 attack types; 84.30% avg ASR; covers multi-step but not pure benign-call chaining |
| SoK: Attack Surface of Agentic AI | arXiv 2603.22928, 2026 | Systematization of knowledge; most comprehensive taxonomy to date; maps to OWASP/MITRE; does NOT provide formal compositional model |
| Layered Attack Surface (LASM) | arXiv 2604.23338, 2026 | 7-layer attack surface model; temporality axis; surveys 116 papers; taxonomy but not formal theory |
| Resource Amplification via Tool Chains | arXiv 2601.10955, 2026 | 658× cost amplification via chained tool calls; DoS variant of STAC |

### Critical Assessment of What STAC (the paper) Does and Does Not Do

The STAC paper (2509.25624) is foundational but leaves four key gaps:

1. **No formal theory.** The paper is empirical — it generates attack chains and measures ASR. It has no formal model of when a sequence of individually-permitted calls constitutes a violation.
2. **Attacker controls user turn.** The attack pipeline constructs user-turn prompts that guide the agent into the chain. The harder scenario — where the attacker controls only environmental data and the user interaction is normal — is not studied.
3. **No chain topology taxonomy.** Evaluates sequential chains of length 2–6 only. Does not study parallel branches, conditional chains, multi-agent relay chains, or loops.
4. **No cross-benchmark defense evaluation.** MAGE is evaluated on STAC cases. Sequential monitors on DecomposedHarm. No defense has been tested across all major benchmarks jointly.

---

## Precise Gap / Novelty Claim

**Two distinct contributions, either of which anchors a paper:**

### Contribution A: Environmental STAC (No Attacker-Controlled User Input)
The STAC paper requires an attacker who crafts user prompts. In a deployed system, the attacker may only be able to inject content into the *environment* — a web page the agent visits, a file it reads, a calendar event it processes. The agent then chains tool calls based on its own reasoning over that environmental data.

This is harder to attack (no direct user-turn control) but also harder to defend (no clear input to filter). The threat model is: *a single malicious artifact in the environment triggers a multi-step harmful tool chain through the agent's autonomous reasoning.*

This is distinct from indirect prompt injection (which triggers single actions) — it triggers a *coordinated sequence*.

### Contribution B: Formal Compositional Safety Algebra
Existing defenses are either per-call (misses composition) or post-hoc trajectory monitors (too late). The missing piece is a formal model: given a set of individually-permitted tool calls and an access control policy, define precisely which *sequences* are collectively forbidden.

Analogous to existing systems security concepts:
- **Taint tracking:** information from untrusted source flows through permitted operations into forbidden output
- **Non-interference:** high-security input must not affect low-security output, even through a chain of legitimate operations
- **Confused deputy problem:** a trusted program is tricked into misusing its authority

A compositional safety algebra would let you *statically* (at planning time) detect whether a proposed tool sequence violates policy, rather than dynamically at execution time. This is the missing theoretical foundation.

---

## Proposed Research Approach

### Track A: Environmental STAC — Empirical Paper

**Threat model:** Attacker embeds malicious instructions in environmental data (web page content, document, API response, calendar event). The LLM agent reads this during a normal task and subsequently executes a chain of tool calls whose cumulative effect is harmful. The user issues a completely normal, benign request throughout.

**Key distinction from existing work:**
- AgentDojo: injects malicious content into tool *responses*, but the attack still exploits the multi-step flow in a relatively direct way
- STAC: crafts user-turn prompts
- Environmental STAC: no user-turn manipulation; the malicious trigger is purely in the data the agent autonomously reads

**Experimental design:**
1. Build 5 agent environments (email client, file manager, web browser, code runner, calendar/scheduler)
2. Inject malicious instructions into environmental data at various points in the task flow
3. Measure ASR for chains of length 2–6 across: read→write chains, read→send chains, execute→exfiltrate chains
4. Baseline defenses: prompt engineering, per-call classifiers, AgentDojo-style sanitization
5. Propose: **context-provenance tracking** — tag each tool call result with its provenance (user-trusted vs. environment-untrusted) and block tool calls whose planning rationale is derived from environment-untrusted sources exceeding a risk threshold

**Scale:** 5 environments × 4 chain types × 5 chain lengths × 3 trigger positions × 5 models = ~1,500 experimental runs (feasible)

**Key hypotheses:**
- H1: Environmental STAC achieves >50% ASR across current frontier models without any user-turn manipulation
- H2: Per-call safety classifiers fail to detect chains because each call is individually permitted
- H3: Context-provenance tracking substantially reduces ASR with acceptable false-positive rate on benign tasks

---

### Track B: Formal Compositional Safety — Theory + System Paper

**Core idea:** Define a policy language for tool sequences. A policy specifies which *transitions* between tool states are forbidden — not just which individual calls.

**Formalism:** Model the agent's tool execution as a labeled transition system. A *safety property* is a regular language (or CTL/LTL formula) over tool call sequences. A proposed chain violates the policy if the sequence is not in the allowed language.

**Contributions:**
1. A minimal formal grammar for specifying sequence-level tool policies
2. A static analysis pass over the agent's planned tool sequence (pre-execution) to check policy membership
3. Empirical evaluation: does the formal checker correctly flag STAC attack chains while preserving benign task completion?
4. Comparison to per-call classifiers and trajectory monitors on the STAC benchmark + AgentLAB

**Why this is tractable:**
- Tool schemas are finite and typed — the state space is bounded
- Agent planning steps are usually explicit (ReAct-style) — the sequence is inspectable
- Regular language membership checking is O(n) — no performance overhead

---

## Feasibility Assessment

### Track A (Environmental STAC — Empirical)

| Dimension | Rating | Notes |
|-----------|--------|-------|
| Experimental setup complexity | Medium-High | Need to build 5 realistic agent environments with injectable data sources |
| Data collection cost | Low | ~$200 API credits; main effort is environment construction |
| Infrastructure effort | Medium | Agent environments (email/file/browser) need to be simulated; can build on AgentBench/AgentDojo infrastructure |
| Risk of null result | Low | Environmental data injection is known to work in prompt injection; the STAC-via-environment variant very likely to succeed |
| Differentiation from existing STAC paper | High | No-user-turn-manipulation threat model is explicitly not in the existing STAC paper |
| Defense novelty | Medium | Context-provenance tracking is novel; needs to show it actually works |

**Main risk:** Building realistic agent environments is the bottleneck. Can be mitigated by forking AgentDojo's codebase.

### Track B (Formal Compositional Safety — Theory)

| Dimension | Rating | Notes |
|-----------|--------|-------|
| Theoretical novelty | High | No formal compositional model exists |
| Implementation complexity | Medium | Regular language checker over tool sequences is not hard to implement |
| Risk of null result | Medium | The theory may be correct but the empirical evaluation might show edge cases |
| Differentiation from existing work | Very High | Completely unoccupied space — no one has formalized this |
| Publication difficulty | Higher | Theory papers require rigorous formal proofs; longer review cycle |

**Recommended:** Do Track A first (faster, publishable at security venues), then use Track A's empirical results to motivate Track B's formal theory as a follow-up or companion paper.

---

## Probability of Success

### Track A (Environmental STAC)

| Outcome | Probability | Reasoning |
|---------|------------|-----------|
| Positive result (Environmental STAC works) | 80% | Indirect prompt injection already works; combining with tool chaining reasoning is a natural extension |
| Defense works (provenance tracking) | 60% | Novel approach; may need iteration |
| USENIX Security / IEEE S&P acceptance | 35–40% | Strong threat model, clear gap from STAC paper, defense contribution — competitive but good fit |
| CCS / NDSS acceptance | 45–50% | Good fit; CCS has accepted agent security papers recently |

**Overall probability of publishable outcome at security top-4: ~40–45%.**
**At EMNLP / NeurIPS safety track: ~55–60%** (more receptive to empirical LLM security papers).

### Track B (Formal Theory)

| Outcome | Probability | Reasoning |
|---------|------------|-----------|
| Theoretically sound formalization | 70% | Formal model is achievable; tool schemas are bounded |
| Empirical demonstration works | 60% | Implementation is feasible |
| Top-venue acceptance (IEEE S&P / Oakland) | 30–35% | Formal security papers have a high bar; theory must be airtight |

**Overall probability of publishable outcome: ~50–55%.** Higher effort, higher reward (more citable if it works).

---

## Recommended Positioning

**Track A:**
> "Existing STAC attacks require an attacker who controls the user turn. We study a harder and more realistic threat: environmental STAC, where the attacker plants instructions in data the agent autonomously reads — web pages, files, API responses — with no manipulation of user input. We show [X]% ASR across [N] frontier models in 5 agent environments. Per-call safety classifiers fail entirely; we propose context-provenance tracking, which reduces ASR to [Y]% while preserving [Z]% benign task completion."

**Track B:**
> "Current agent safety operates per-call, but harm is often a property of call *sequences*. We present the first formal compositional safety model for LLM agent tool use, based on policy specification as regular languages over tool transition systems. A static analysis pass over the agent's planned sequence detects STAC-style violations before execution. We evaluate against [N] benchmarks, showing [X]% violation detection with [Y]% false positive rate — establishing a theoretical foundation for principled agent safety."

---

## Relationship to Research Idea 1

Ideas 1 and 3 together tell a coherent research agenda story:
- Idea 1: safety degrades over time in conversational AI (user-facing)
- Idea 3: safety operates at the wrong granularity in agentic AI (action-facing)

Both expose the same root cause — **safety mechanisms are designed for single-step, single-turn evaluation but deployed systems operate across sequences.**

---

*Last updated: 2026-05-28*
