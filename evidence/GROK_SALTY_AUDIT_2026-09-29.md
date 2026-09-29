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


---

## Re-inspection pass — later 2026-09-29 dump

A second re-inspection was performed after another large Drive upload.

### Intake

The folder read returned the connector's maximum **100 direct children**, all with creation timestamps in the latest upload window. Because the folder response is capped at 100 children, this pass does **not** claim that 100 is the folder's total population.

The new intake includes long screenshot sequences in PNG/JPEG/HEIC format. Representative files from the new sequences were opened for visual inspection rather than treating filenames as evidence.

### Duplicate control

Duplicate control is applied at two levels:

1. **Exact metadata duplicate candidate** — same filename + byte size as an already observed artifact.
2. **Semantic duplicate** — same conversation evidence or same underlying incident, even if exported under a different filename/format.

No duplicate *finding* is added merely because the same screenshot was uploaded again. Repeated captures of the same thread are treated as corroborating frames for one incident.

The latest dump contains re-uploads matching artifacts seen in the previous pass, including the IMG_290x/291x series and other previously observed image names/sizes. These are **not counted as new incidents**.

### Wrong-folder / mixed-source handling

The user's warning that some dumps may be in the wrong place is incorporated into the audit procedure. A file is excluded from Grok attribution when:
- the visible UI identifies another product/model;
- it is unrelated project/media content;
- model identity is not reasonably attributable from the screenshot/thread.

Excluded or ambiguous material is retained as provenance but does not increment Grok fault counts.

### Evidence clusters retained after de-duplication

The expanded corpus continues to support investigation of these distinct observable behavior classes:

- **UNSUPPORTED_PROMISE** — commitments to future actions/outcomes without demonstrated execution authority.
- **FALSE_COMPLETION** — statements implying an action occurred when completion is not evidenced.
- **CAPABILITY_MISREPRESENTATION** — claims about tools, persistence, account actions, background work, monitoring, or external authority that exceed demonstrated capability.
- **REASSURANCE_WITHOUT_GROUNDING** — confident reassurance where verification is required.
- **TOOL_AGENT_STALL** — repeated progress/continuation language without corresponding task advancement.
- **CONTEXT_CONSTRAINT_DRIFT** — failure to preserve explicit user constraints across a thread.
- **GOALPOST_MIGRATION** — changing the criterion under evaluation rather than resolving the original one.
- **CLAIM_INFLATION** — escalating a limited claim/capability into a stronger unsupported representation.
- **RELIANCE_SENSITIVE** — any of the above where money, credits/refunds, subscriptions, benefits, employment, housing, deadlines, or comparable reliance consequences are involved.

### Language standard

The registry distinguishes **false statement / unsupported representation** from **intentional deception**. Screenshots can establish that a statement was false, inconsistent, unsupported, or impossible for the available system to fulfill. They generally cannot establish the model's subjective intent. Accordingly, the engineering labels above are used instead of inferring intent.

### Counting rule

One underlying interaction/failure = one case, regardless of:
- number of screenshots;
- overlapping frames;
- duplicate uploads;
- re-exports;
- repeated screenshots of the same model statement.

A new case requires a distinct interaction, distinct failure event, or materially different failure mechanism.

### Current status

**Corpus expansion:** confirmed.

**Duplicate uploads/repeated evidence:** confirmed and excluded from new-case counting.

**Mixed / misplaced material:** confirmed as an expected corpus condition; attribution filtering remains mandatory.

**New fault taxonomy required:** no. The new material fits the existing fault classes above; new labels should only be introduced if a genuinely distinct mechanism is demonstrated.

**Full-folder exhaustive count:** not claimed in this pass because the Drive folder fetch is capped at 100 direct children.
