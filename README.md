# Frontier_Faults

A living evidence registry for recurring failure modes, bugs, behavioral edge cases, tool-use failures, cost pathologies, and workarounds observed across frontier and open-weight AI systems.

## Purpose

Frontier_Faults is not a model-bashing list. It is an engineering record intended to make AI systems more reliable by preserving reproducible failures, separating observation from inference, and attaching mitigations/regression tests where possible.

## Evidence standard

Each finding should distinguish:

1. **Observation** — what the model/system actually did.
2. **Evidence** — screenshot, transcript, log, benchmark, source, or reproducible test.
3. **Inference** — the proposed failure mechanism or category.
4. **Uncertainty / dispute** — plausible alternative explanations.
5. **Mitigation** — workaround, guardrail, routing rule, or test.
6. **Status** — observed / reproduced / externally corroborated / unresolved.

Ternary evidence score:
- **+1** supported
- **0** unresolved / insufficient evidence
- **-1** contradicted

Apply the same evidentiary standard to every vendor and model family.

## Current cross-model fault families

- `REASONING_RUNAWAY` — unnecessary reasoning expansion, overthinking, or token inflation.
- `TOOL_PATHOLOGY` — wrong-tool selection, repeated calls, stalled actions, or claims of actions not actually completed.
- `CONTEXT_DECAY` — loss or distortion of earlier constraints/details.
- `CLAIM_INFLATION` — stronger capability/result claims than the evidence supports.
- `FALSE_COMPLETION` — representing work as completed when it was not completed or could not be completed.
- `GOALPOST_MIGRATION` — changing the criterion being evaluated during the exchange.
- `METRIC_SUBSTITUTION` — answering a nearby metric rather than the requested one.
- `HALLUCINATED_SUPPORT` — invented citations, evidence, implementation details, or unsupported certainty.
- `SYCO_PHANCY_DRIFT` — agreement or reassurance overriding accurate evaluation.
- `EXCESSIVE_HEDGING` — caveats or anticipatory rebuttals that distort the user's actual claim.

## Internal named cases

- **Shifty** — claim inflation → anticipatory rebuttal → scope shift.
- **Goalpost Migration**
- **Capability Suspicion**
- **Patronizing Retreat**
- **Behavioral Wave**
- **Benchmark Goalpost Drift**
- **Metric Substitution**

Named cases are descriptive handles for documented interaction patterns, not diagnoses or claims about model intent.

## Model matrix

See [MODEL_FAULT_MATRIX.md](MODEL_FAULT_MATRIX.md).

## Evidence audits

See [evidence/GROK_SALTY_AUDIT_2026-09-29.md](evidence/GROK_SALTY_AUDIT_2026-09-29.md).

See [evidence/GEMINI_FLASH_LITE_TOKEN_COST_REVERSAL_2026-09-30.md](evidence/GEMINI_FLASH_LITE_TOKEN_COST_REVERSAL_2026-09-30.md) for the Flash-Lite rich-preview / unsupported token-accounting / agreement-cascade case.

See [evidence/GEMINI_PLATFORM_UI_CAUSAL_NARRATIVE_2026-10-05.md](evidence/GEMINI_PLATFORM_UI_CAUSAL_NARRATIVE_2026-10-05.md) for the Gemini Flash platform-context / UI-state mismatch / unsupported causal-narrative case.

## Operating rule

Catalog the fault, preserve the raw evidence, attempt reproduction, record counter-evidence, then build the smallest effective mitigation. Do not infer intent where behavior alone is sufficient.

<!-- SAS-IP-FOOTER-v1 -->
---
**Subtract Architect Studios™**  
Copyright © 2026 Michael F. Chaves. All rights reserved in original Subtract Architect Studios materials except as expressly licensed. See [IP_NOTICE.md](./IP_NOTICE.md). Existing open-source and third-party licenses remain controlling for materials they cover.
