# Snapforge

**A composable open-source toolkit for LLM and agentic AI observability.**

---

## What is Snapforge?

Snapforge is a suite of focused, independent tools that together form a complete observability ecosystem for LLM applications and agentic AI systems.

Each tool solves one problem sharply. Each is installable on its own. Together, they share a common OpenTelemetry-compatible event schema — so outputs compose freely, route into each other without custom integration, and drop into existing stacks like Grafana or Datadog without friction.

Built for individual developers, DevOps teams, and enterprise ML engineers — at whatever layer they need.

---

## Objective

Modern LLM applications — especially agentic ones — are hard to observe. Prompts drift, costs balloon silently, tool calls fail without trace, and multi-step agent runs are nearly impossible to debug after the fact.

Snapforge addresses the four critical gaps in LLM observability:

- **Output quality** — did the model produce what you expected?
- **Agent execution** — what did the agent actually do, step by step?
- **Cost and latency** — what did that run cost, and how long did it take?
- **Tool call correctness** — did the model use its tools the right way?

The goal is not to be a platform. Each Snapforge tool can go viral on its own. The ecosystem emerges from composition — not from a hosted dashboard or locked-in infrastructure.

---

## The Toolkit

| Tool | Purpose | Package |
|---|---|---|
| [**llm-diff**](#llm-diff) | LLM output quality comparison and evaluation | `pip install llm-diff` |
| [**llm-trace**](#llm-trace) | Multi-step agent execution tracing | `pip install llm-trace` |
| [**llm-cost**](#llm-cost) | Cost and latency tracking per call, run, and agent | `pip install llm-cost` |
| [**llm-inspect**](#llm-inspect) | Tool call inspection for agentic systems | `pip install llm-inspect` |

---

### llm-diff

> _The evaluation layer._

Diffs LLM outputs across model versions, prompt changes, or time — so you can see exactly how your outputs shifted and whether quality improved or regressed.

- Side-by-side output comparison
- Regression detection across prompt versions
- Per-call cost tracking
- Integrates with `llm-trace` spans for quality regression on agentic runs

**[→ View llm-diff](https://github.com/snapforge/llm-diff)**

---

### llm-trace

> _The agent execution layer._

Captures the full span tree of an agentic run — which tools were called, in what order, with what inputs and outputs, and where the run branched or failed. Works across any agent framework, not just LangChain.

- Full OpenTelemetry-compatible span capture
- Tool call ordering and branching visibility
- Framework-agnostic — works with LangChain, LlamaIndex, custom agents, and raw API calls
- Feeds directly into `llm-diff` and `llm-cost`

**[→ View llm-trace](https://github.com/snapforge/llm-trace)**

---

### llm-cost

> _The cost and latency layer._

Token and USD accounting at every level — per API call, per agent run, per workflow — with trend views over time. A natural expansion of the cost tracking already in `llm-diff` v1.2.

- Per-call and per-run token and USD tracking
- Latency breakdowns across model calls and tool calls
- Trend views for cost drift detection
- Ingests `llm-trace` span data natively

**[→ View llm-cost](https://github.com/snapforge/llm-cost)**

---

### llm-inspect

> _The tool call inspection layer._

The agentic equivalent of a network inspector. Surfaces exactly what arguments were passed to each tool, what it returned, and whether the model used the result correctly downstream.

- Argument and return value capture for every tool call
- Model reasoning trace — did it act on what the tool returned?
- Highlights tool misuse and ignored results
- Pairs with `llm-trace` for full agentic run visibility

**[→ View llm-inspect](https://github.com/snapforge/llm-inspect)**

---

## Shared Schema

All four tools emit and consume a shared **OpenTelemetry-compatible JSON/OTLP event schema**. This is the glue.

It means:
- `llm-trace` output pipes into `llm-diff` for quality regression — no custom integration
- `llm-cost` reads from `llm-trace` spans natively
- Enterprise users route all events into Grafana, Datadog, or any OTLP-compatible backend without modification
- Each tool is independently useful; composing them is additive, not required

---

## Philosophy

- **One tool, one job.** Sharp identity over sprawling features.
- **Composable over bundled.** Adopt one tool or all four — at your own pace.
- **Structured data over dashboards.** Emit clean, portable data. Let the ecosystem visualize it.
- **Open source first.** Every tool lives on PyPI and GitHub with its own docs, community, and entry point.

---

## License

MIT — see [LICENSE](LICENSE)
