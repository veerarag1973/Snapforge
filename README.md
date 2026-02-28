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

Snapforge addresses three critical gaps in the LLM development lifecycle:

- **Output quality** — did the model produce what you expected?
- **Prompt governance** — are prompts versioned, auditable, and enterprise-ready?
- **Prompt engineering** — can prompts be composed, templated, and reused systematically?

The goal is not to be a platform. Each Snapforge tool can go viral on its own. The ecosystem emerges from composition — not from a hosted dashboard or locked-in infrastructure.

---

## The Toolkit

| Tool | Purpose | Status | Package |
|---|---|---|---|
| [**llm-diff**](#llm-diff) | LLM output quality comparison and evaluation | ✅ Done | `pip install llm-diff` |
| [**promptlock**](#promptlock) | Prompt version control and enterprise governance | 🔧 Under development | — |
| [**promptblock**](#promptblock) | Prompt template engine with variable management, composition, and inheritance | 🔧 Under development | — |

---

### llm-diff

> _The evaluation layer._

Diffs LLM outputs across model versions, prompt changes, or time — so you can see exactly how your outputs shifted and whether quality improved or regressed.

- Side-by-side output comparison
- Regression detection across prompt versions
- Per-call cost tracking
- Pairs with `promptlock` to tie quality regressions back to specific prompt versions

**[→ View llm-diff](https://github.com/veerarag1973/llmdiff)**

---

### promptlock _(under development)_

> _The prompt governance layer._

Version control and enterprise governance for prompts — so every prompt change is tracked, auditable, and reversible. Designed for teams that need to manage prompts at scale without losing control.

- Full version history for every prompt
- Diff and rollback across prompt versions
- Approval workflows and access controls for enterprise teams
- Integrates with `llm-diff` to surface quality regressions tied to specific prompt changes
- Emits `llm-schema` events for full audit trail

> **Under development.** Follow along or contribute at [github.com/veerarag1973/promptlock](https://github.com/veerarag1973/promptlock).

---

### promptblock

> _The prompt engineering layer._

A prompt template engine with variable management, composition, and inheritance — so complex prompts can be built systematically rather than assembled by hand.

- Variable injection with type validation
- Template composition — build complex prompts from reusable blocks
- Inheritance — extend and override base templates cleanly
- Works alongside `promptlock` for versioned, governed template libraries

**[→ View promptblock](https://github.com/veerarag1973/promptblock)**

---

## Shared Foundation

### llm-schema _(under development)_

> _The shared event schema._

`llm-schema` defines the OpenTelemetry-compatible JSON/OTLP event schema that all Snapforge tools emit and consume. This is the glue that makes the ecosystem composable without custom integration.

- OpenTelemetry-compatible JSON/OTLP format
- Covers prompt events, evaluation results, governance audit trails, and template rendering spans
- Routes cleanly into Grafana, Datadog, or any OTLP-compatible backend
- Each Snapforge tool is independently useful; `llm-schema` makes composing them additive, not required

> **Under development.** Follow along or contribute at [github.com/veerarag1973/llm-schema](https://github.com/veerarag1973/llm-schema).

---

## Philosophy

- **One tool, one job.** Sharp identity over sprawling features.
- **Composable over bundled.** Adopt one tool or all four — at your own pace.
- **Structured data over dashboards.** Emit clean, portable data. Let the ecosystem visualize it.
- **Open source first.** Every tool lives on PyPI and GitHub with its own docs, community, and entry point.

---

## License

MIT — see [LICENSE](LICENSE)
