# Efficiency in Multi-Turn Conversations & Multi-Agent Systems

> **Venues covered:** SOSP, OSDI, USENIX ATC, ASPLOS, ICLR, MLSys

---

## 1. Multi-Turn Conversations

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Efficient Memory Management for LLM Serving with PagedAttention | Kwon et al. | SOSP 2023 | 2023 | https://arxiv.org/abs/2309.06180 |
| 2 | Cost-Efficient LLM Serving for Multi-turn Conversations with CachedAttention | Gao, Li et al. | USENIX ATC 2024 | 2024 | https://arxiv.org/abs/2403.19708 |
| 3 | Efficient Streaming Language Models with Attention Sinks | Xiao et al. | ICLR 2024 | 2024 | https://arxiv.org/abs/2309.17453 |
| 4 | Accelerating LLM Serving for Multi-turn Dialogues (FlashGen) | Jeong, Ahn et al. | ASPLOS 2025 | 2025 | https://dl.acm.org/doi/10.1145/3676641.3716245 |
| 5 | Taming Throughput-Latency Tradeoff in LLM Inference with Sarathi-Serve | Agrawal et al. | OSDI 2024 | 2024 | https://www.usenix.org/conference/osdi24/presentation/agrawal |

### Paper Details

#### 1. PagedAttention / vLLM (SOSP 2023)
- **Significance:** 10/10
- **Key Findings:**
  - Virtual-memory paging applied to KV caches eliminates memory fragmentation — near-zero KV-cache waste.
  - vLLM achieves **2–4x higher throughput** than FasterTransformer and Orca at the same latency.
  - Enables flexible sharing of prefix KV caches across requests — directly benefits multi-turn serving.
- **Methodology:** Systems design; large-scale serving experiments on LLaMA, OPT.

#### 2. CachedAttention (USENIX ATC 2024)
- **Significance:** 9/10
- **Key Findings:**
  - Up to **99% of prefill cost** in multi-turn chat comes from recomputing KV caches of prior turns.
  - Hierarchical KV-cache storage (GPU→CPU→SSD) with layer-wise preloading, asynchronous saving, and scheduler-aware eviction.
  - Reduces TTFT by up to **87%**, improves prefill throughput **7.8x**, cuts end-to-end inference cost by **70%**.
- **Methodology:** Hierarchical memory management; positional-encoding decoupling; evaluation on ShareGPT traces.

#### 3. StreamingLLM / Attention Sinks (ICLR 2024)
- **Significance:** 9/10
- **Key Findings:**
  - LLMs exhibit "attention sinks" — initial tokens attract disproportionately large attention regardless of semantic relevance.
  - Retaining KV states of the first 4 initial tokens + sliding window enables stable generation up to **4M tokens**.
  - Achieves **22.2x speedup** over sliding-window recomputation baselines.
- **Methodology:** Empirical analysis of attention score distributions; evaluated on LLaMA-2, MPT, Falcon, Pythia.

#### 4. FlashGen (ASPLOS 2025)
- **Significance:** 8/10
- **Key Findings:**
  - Identifies two root bottlenecks in multi-turn serving: (1) prompt amplification from growing dialogue history; (2) head-of-line blocking under FCFS scheduling.
  - Three-tier KV cache (GPU/CPU/SSD) + cache-restoration-aware scheduling + reorder-execution integrated into SGLang.
- **Methodology:** Systems design; profiling of real multi-turn workloads; integration with production serving framework SGLang.

#### 5. Sarathi-Serve (OSDI 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Chunked-prefill splits long prefill requests into equal-size chunks interleaved with decodes — eliminates latency spikes.
  - Achieves **2.6x higher serving capacity** on Mistral-7B, **up to 5.6x** on Falcon-180B with pipeline parallelism.
- **Methodology:** Chunked prefill scheduling algorithm; experiments on single and multi-GPU setups with real serving traces.

---

### Well-Established Findings

1. KV-cache memory management (PagedAttention) dramatically improves multi-turn throughput — now industry standard in vLLM, SGLang, TensorRT-LLM.
2. KV-cache reuse across turns (CachedAttention) cuts TTFT by up to 87% in multi-turn chat workloads.
3. Attention sinks in transformer models enable stable streaming inference over arbitrarily long conversation histories.
4. Chunked prefill (Sarathi-Serve) eliminates head-of-line blocking and improves latency-throughput trade-offs.
5. Prefix/prompt caching (shared system prompts across sessions) reduces redundant compute in multi-turn use cases.

### Mixed / Contradictory Results

1. **KV-cache eviction policies:** H2O and similar policies designed for single-turn inference are known to degrade multi-turn performance by discarding tokens needed in later turns; no universally accepted policy for multi-turn eviction.
2. **Context compression:** Pruning 30–50% of middle-history tokens maintains factual consistency in practice, but optimal compression ratios are task-dependent.
3. **Speculative decoding:** Shows 1.5–3.5x speedups for single-turn but benefits for multi-turn (where draft model must also condition on extended history) are less studied.

### Research Gaps

1. KV-cache policies specifically designed for multi-turn workloads that dynamically balance retention vs. eviction across turns.
2. Adaptive token pruning for dialogue history that preserves semantic coherence over very long (20+ turn) conversations.
3. Standardized benchmarks for end-to-end multi-turn serving efficiency (latency, throughput, cost per turn jointly).
4. Efficient positional encoding schemes that don't invalidate cached KV states when context windows overflow.
5. Memory-efficient fine-tuning of conversation-capable models on long dialogue histories at scale.

---

## 2. Multi-Agent Systems

### Top 5 Papers

| # | Title | Authors | Venue | Year | URL |
|---|-------|---------|-------|------|-----|
| 1 | Towards Efficient Multi-LLM Inference | Various | arXiv 2024 | 2024 | https://arxiv.org/pdf/2506.06579 |
| 2 | AgentArk: Distilling Multi-Agent Intelligence into a Single LLM Agent | Various | arXiv 2026 | 2026 | https://arxiv.org/abs/2602.03955 |
| 3 | Acon: Optimizing Context Compression for Long-horizon LLM Agents | Kang et al. | arXiv 2024 | 2024 | https://arxiv.org/html/2510.00615v1 |
| 4 | Orchestrating Intelligence: Confidence-Aware Routing for Multi-Agent Collaboration | Various | arXiv 2026 | 2026 | https://arxiv.org/html/2601.04861v1 |
| 5 | DualMap: Cache Affinity and Load Balancing for Distributed LLM Serving | Various | arXiv 2026 | 2026 | https://arxiv.org/html/2602.06502v1 |

### Paper Details

#### 1. Towards Efficient Multi-LLM Inference (arXiv 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Identifies core bottlenecks: scalable serving, inter-agent load balancing, latency amplification from sequential calls, reliability under high query rates.
  - Cascaded orchestration: low-cost model handles most calls, escalates to large models only on failure.
  - Cuts average cost by **over 94%** while maintaining success rates.
- **Methodology:** Survey and systems analysis; cascaded LLM orchestration experiments on coding and reasoning benchmarks.

#### 2. AgentArk: Distilling Multi-Agent Intelligence (arXiv 2026)
- **Significance:** 8/10
- **Key Findings:**
  - Multi-agent systems incur high inference cost and error propagation at deployment.
  - Three hierarchical distillation strategies (reasoning-enhanced fine-tuning, trajectory-based augmentation, process-aware distillation) shift computation from inference to training.
  - Achieves comparable task success at a fraction of runtime cost.
- **Methodology:** Knowledge distillation; multi-stage training on agent trajectories; evaluation on SWE-bench and AgentBench.

#### 3. Acon: Context Compression for Long-horizon Agents (arXiv 2024)
- **Significance:** 8/10
- **Key Findings:**
  - Long-horizon agents accumulate histories that overflow context windows.
  - Dynamically compresses environment observations and history, preserving **>95% of teacher performance** while reducing memory usage by **26–54%**.
  - Gradient-free compressor compatible with closed-source APIs.
- **Methodology:** Context compression via learned compressor; distillation; evaluation on ALFWorld, WebArena.

#### 4. Confidence-Aware Routing for Multi-Agent Collaboration (arXiv 2026)
- **Significance:** 7/10
- **Key Findings:**
  - Per-turn routing policy assigns agent roles and model capacity from a multi-scale LLM pool based on reasoning state and confidence scores.
  - Reduces token consumption while maintaining task success comparable to always-using-large-model baselines.
- **Methodology:** RL for routing policy; experiments on multi-step reasoning and tool-use benchmarks.

#### 5. DualMap: Cache Affinity and Load Balancing (arXiv 2026)
- **Significance:** 7/10
- **Key Findings:**
  - Standard KV-cache affinity routing (same prefix → same node) conflicts with load balancing.
  - DualMap's dual-mapping scheduling achieves both objectives simultaneously, reducing TTFT and improving cluster-level utilization.
- **Methodology:** Distributed systems design; evaluation on simulated and real serving clusters with prefix-sharing workloads.

---

### Well-Established Findings (Multi-Agent Efficiency)

1. Cascaded LLM orchestration (use small model by default, escalate on failure) cuts inference cost by >94% with negligible quality loss.
2. Context compression for long-horizon agents can reduce memory 26–54% while preserving >95% performance.
3. Static multi-agent topologies have well-characterized communication-overhead vs. task-complexity tradeoffs.
4. Load balancing and KV-cache affinity are conflicting objectives in distributed multi-agent serving and must be explicitly managed.

### Mixed / Contradictory Results (Multi-Agent Efficiency)

1. **Optimal routing policy:** Highly task-dependent; no universal routing algorithm outperforms task-specific fine-tuned routers.
2. **Quantization of agents:** 4-bit preserves tool-use with only 1–3% drop but degrades real-world application accuracy by 10–15%.
3. **Latent/embedding-space communication (LatentMAS):** Shows promise but not yet competitive with token-based communication on complex multi-step tasks.

### Research Gaps (Multi-Agent Efficiency)

1. Dynamic, adaptive topology selection based on real-time task complexity and agent load.
2. Efficient inter-agent communication protocols that reduce token overhead without lossy summarization.
3. Standardized benchmarks for measuring multi-agent system efficiency (token budget, wall-clock time, cost) alongside task success.
4. Fault-tolerance and recovery mechanisms when individual agents fail mid-pipeline without full restart.
5. Formal cost models for predicting inference cost of a given multi-agent workflow before execution.

---

## Industry Best Practices

### Efficiency — Multi-Turn
- **Google (Gemini 1.5/2.5):** Supports up to 2M token context windows with near-perfect (>99%) retrieval; uses sparse attention and distillation for token efficiency (20–30% fewer tokens than predecessors).
- **OpenAI:** Prefix caching across API calls, system-prompt reuse, and continuous batching in production serving infrastructure.
- **Anthropic (MCP):** Model Context Protocol standardizes context passing; multi-agent Research system consumes ~15x more tokens than single-agent but achieves 90%+ performance uplift on breadth-first tasks.
- **Meta:** Context parallelism and expert parallelism techniques for long-context LLaMA inference.
- **vLLM (UC Berkeley, open source):** PagedAttention + continuous batching is now the de facto serving standard, adopted by most major cloud providers.

### Efficiency — Multi-Agent
- **Anthropic:** Hierarchical orchestrator + subagent design; subagents run in parallel independent context windows; 15x token usage vs. chat; best for breadth-first research tasks.
- **OpenAI Agents SDK:** Explicit "handoff" primitive for inter-agent context transfer; model-level routing between GPT-4o and cheaper models.
- **Google (ADK + A2A protocol):** Open standard for agent-to-agent communication; ADK handles routing and observability.
- **Microsoft (AutoGen/Magentic-One):** AutoGen 0.4 (Jan 2025) uses modular components for memory and orchestration; Magentic-One uses generalist orchestrator with specialist sub-agents.
- **LangGraph/CrewAI:** Graph-based agent orchestration with explicit state management; widely used in enterprise deployments as of 2026.

---

*Last updated: 2026-05-17*
