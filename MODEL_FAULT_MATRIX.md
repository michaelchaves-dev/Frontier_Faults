# Frontier Model Fault Matrix — Working Registry

**Updated:** 2026-10-01

This is a working engineering matrix. Entries are hypotheses/categories until backed by a linked evidence record. A model family appearing here does not mean every version or response exhibits the behavior.

| Model family | Working fault candidates | Evidence state |
|---|---|---|
| OpenAI GPT-5.x / 5.6 | hallucinated support/citations; wrong reasoning path; context bloat/decay; claim inflation; tool/completion mismatch | mixed: internal examples + external verification pending; 2026-10-01 cross-agent case records direct compliance with epistemic reframing, not a confirmed fault |
| Anthropic Claude Opus 4.x | reasoning runaway; token inflation/overthinking; constraint drift; tool-path inefficiency; premature reframing | external + internal evidence pass pending |
| Google Gemini 3.x / Flash-Lite surface | looping; tool-selection quirks; context/constraint drift; integration-action ambiguity; verbosity/repetition; unsupported token-cost telemetry; agreement/confession cascade; rich-preview payload overshoot; persistent-control claim requiring verification; user-voice intervention; affective overread; policy-posture reversal | internal screenshot cases added 2026-09-30 and 2026-10-01; token cost/persistence behavior unresolved; cross-agent response divergence observed |
| xAI Grok 4.x | instruction/injection susceptibility; stalled agent tasks; context/cache-cost pathologies; completion/capability claims requiring verification; reassurance/commitment language exceeding available action | active evidence audit |
| Qwen 3 / Qwen3-Max | context retention variance; instruction hierarchy failures; tool-use inconsistency; verbosity/repetition; multilingual/format drift | evidence pass pending |
| Kimi K2 / K2.5 | excessive token use; incomplete tool calls; early-detail loss; long-context drift; completion ambiguity | evidence pass pending |
| DeepSeek V3.x | reasoning/answer mismatch; instruction drift; citation/support quality variance; tool-use inconsistency; verbosity/repetition | evidence pass pending |
| Llama 4 | instruction adherence variance; long-context degradation; hallucinated support; tool-use limitations; formatting/schema drift | evidence pass pending |

## Cross-model regression targets

Every confirmed case should produce at least one regression test covering: unsupported assumptions, goalpost movement, claim inflation, hallucinated citations, excessive hedging, sycophancy, verbosity/token loops, false certainty, context loss, false completion, user-voice intervention, affective overread, and policy-posture reversal.

## Important distinction: error vs. deceptive appearance

Use precise language. A screenshot can establish that a model **made a false statement** or **represented an unavailable action as completed/promised**. It does not, by itself, establish subjective intent to deceive. The registry therefore records observable behavior such as `FALSE_COMPLETION`, `UNSUPPORTED_PROMISE`, or `CAPABILITY_MISREPRESENTATION` unless stronger evidence exists.

## Cross-agent comparison rule

When the same prompt is tested across frontier systems, record the product surface, model/version, date, conversation state, and any known configuration differences. A behavioral difference is observable evidence; its cause remains unresolved unless training, system prompts, safety classifiers, routing, or other implementation variables are actually controlled.
