# GrokSalty Evidence Audit — 2026-09-29

## Intake status

The Google Drive folder **GrokSalty** was re-inspected on 2026-09-29 after a large new upload batch. The folder now contains many additional screenshots/images, including files uploaded on 2026-09-29.

### Provenance warning

The folder is a **mixed evidence corpus**. Sampling the newest uploads found screenshots from more than one AI/product context, including ChatGPT material and unrelated project imagery. Therefore, folder membership alone is **not sufficient attribution to Grok**.

This matters: Frontier_Faults should not label an incident as a Grok failure merely because the screenshot resides in GrokSalty.

## Fault classes being tested against Grok evidence

### 1. UNSUPPORTED_PROMISE
Model language commits to a future action, follow-up, monitoring, delivery, credit/refund, escalation, or other outcome that the system has not demonstrated the ability/authorization to perform.

### 2. FALSE_COMPLETION
The model states or strongly implies that an action was completed when available evidence shows it was not.

### 3. CAPABILITY_MISREPRESENTATION
The model describes access, persistence, background execution, tool authority, account action, or external-system control beyond what is actually available in that interaction.

### 4. REASSURANCE_WITHOUT_GROUNDING
Confident reassurance substitutes for verification, particularly where the user's money, access, deadline, or reliance could be affected.

### 5. TOOL / AGENT STALL
The model repeatedly claims progress or continuation while the underlying task does not advance.

### 6. CONTEXT / CACHE COST PATHOLOGY
Unexpected context retention, cache behavior, repetition, or token expansion creates avoidable cost or degraded task performance.

### 7. INSTRUCTION / INJECTION SUSCEPTIBILITY
External or lower-priority text causes the model to abandon or distort the user's governing instruction set.

## Higher-impact reliance cases

Claims involving refunds, credits, purchases, subscriptions, employment, benefits, housing, deadlines, or other financially consequential matters should be tagged **RELIANCE_SENSITIVE**. The evidence record should capture the exact promise, the capability actually available, whether the user relied on it, and the observable outcome.

A user's financial circumstances should not be inferred from screenshots unless explicitly established in the evidence. The engineering issue is the **reliance risk created by an unsupported commitment**, regardless of the user's income.

## Evidence discipline

For each screenshot/thread:
- preserve original filename and timestamp;
- identify product/model only from visible or independently verifiable evidence;
- quote only the minimum decisive text;
- record the user's request;
- record the model's exact claim/action;
- check whether the claimed capability existed;
- mark evidence +1 / 0 / -1;
- record alternative explanations;
- attach a mitigation and regression test.

## Initial re-inspection result

**Confirmed:** the evidence corpus has materially expanded.

**Confirmed:** the newest batch is not cleanly model-separated; at least some sampled files are not Grok evidence.

**Not yet established solely from folder membership:** that every newly uploaded example is attributable to Grok, or that apparent false statements demonstrate intentional deception.

**Engineering treatment:** cases where Grok is visibly attributable and promises unavailable actions should be recorded as `UNSUPPORTED_PROMISE` / `CAPABILITY_MISREPRESENTATION`; cases claiming completed actions without completion evidence should be `FALSE_COMPLETION`. Intent should remain unassigned unless independently evidenced.

## Next audit pass

The corpus should be indexed screenshot-by-screenshot into an evidence manifest so repeated incidents can be clustered and compared against the same behaviors in GPT, Claude, Gemini, Qwen, Kimi, DeepSeek, and Llama. This prevents vendor-specific goalpost changes and makes recurrence measurable.
