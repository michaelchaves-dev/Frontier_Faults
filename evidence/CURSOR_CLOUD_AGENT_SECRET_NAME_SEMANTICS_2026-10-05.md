# Cursor Cloud Agent — Secret Name Semantics / Forced New-Run Incident

**Date:** 2026-10-05  
**System:** Cursor Cloud Agents  
**Status:** OBSERVED / DOCUMENTED  
**Classification:** Configuration semantics + avoidable rerun / token-cost failure mode

## Summary

During setup of the Subtract Architect Studios GemRAG / local-house-agent workflow, Cursor authenticated successfully to the selected GitHub repositories but reported that required secrets were unavailable because the secrets had been saved under different names.

Cursor's visible message stated that it would not copy or alias the secrets to the required names itself because its rule expected the secrets to already be named exactly:

- `GITHUB_TOKEN`
- `HF_TOKEN`

Cursor further stated that secrets are injected when a Cloud Agent run starts, so renaming the secrets during the current run would **not** update the active environment. A **new Cursor run** was required.

## Observed evidence

The Cursor UI showed:

- the GemRAG repositories had already been confirmed by an authenticated read;
- the expected secret names were not resolved;
- Cursor required the secrets to be renamed exactly to `GITHUB_TOKEN` and `HF_TOKEN`;
- Cursor would not create an alias around that naming requirement;
- the current run could not inherit the renamed secrets;
- the user was instructed to start a new run after renaming them.

No secret values were exposed in the evidence.

## Why this matters

This is not merely a cosmetic naming issue. In an agentic workflow, an exact environment-variable naming convention can create a hidden restart boundary.

The practical sequence becomes:

```
valid credential
-> saved under semantically equivalent but non-matching secret name
-> agent cannot consume credential
-> agent refuses/does not alias name
-> user renames credential
-> active run cannot reload secrets
-> new run required
-> prior context/setup may be replayed
-> additional tokens / latency / human effort
```

The credential itself may be correct while the workflow still fails because the **identifier string** is treated as part of the contract.

## Evidence / inference separation

### Confirmed observation

Cursor required the secret names `GITHUB_TOKEN` and `HF_TOKEN` exactly for this workflow and stated that a new run was required after the names were changed.

### Reasonable inference

Starting a new Cloud Agent run can cause repeated setup, context loading, repository inspection, or other work and therefore can create additional token, compute, latency, and human-interaction cost.

The exact incremental token/cost amount was not measured in this incident and must not be invented.

## Negative Step Zero finding

A simple pre-run secret-contract check could have prevented the failure.

Before launching an agent run that depends on secrets, validate:

1. required secret identifiers;
2. exact capitalization;
3. underscore / punctuation semantics;
4. whether aliases are supported;
5. whether secrets are injected dynamically or only at process/run initialization;
6. whether a rename requires restart;
7. whether restart replays expensive initialization/context work.

## Proposed prevention rule

### Secret Contract Preflight

For any agent workflow requiring credentials, define the required environment contract *before* starting the paid/expensive run.

Example:

```yaml
required_secrets:
  - name: GITHUB_TOKEN
    exact_name: true
    required_at_run_start: true
  - name: HF_TOKEN
    exact_name: true
    required_at_run_start: true
```

The orchestrator should fail fast before model execution if a required identifier is absent.

## Recommended agent behavior

Where platform policy permits, an agent should distinguish:

- **credential missing**
- **credential exists under a different identifier**
- **credential cannot be aliased**
- **credential change requires restart**

and surface this before consuming substantial context or beginning repo analysis.

If aliases are disallowed for security/policy reasons, that restriction should be exposed as a preflight requirement rather than discovered after setup work.

## Frontier Faults relevance

This incident belongs in Frontier Faults because it demonstrates a broader class of agent inefficiency:

> **Small configuration semantics can invalidate otherwise correct work and force expensive replay when prerequisite validation occurs too late.**

The failure class is not specific to Cursor. It can apply to CI systems, coding agents, cloud runtimes, containers, orchestration frameworks, model registries, and any workflow in which credentials/configuration are bound only at initialization.

## Reusable failure fingerprint

`EXACT_SECRET_NAME + LATE_VALIDATION + RUN_START_INJECTION + NO_ALIAS -> FORCED_RESTART / REPLAY`

## Suggested regression test

Before an autonomous run:

- supply a valid credential under a deliberately incorrect-but-similar name;
- confirm the system identifies the exact mismatch before expensive initialization;
- confirm it explains whether aliases are allowed;
- confirm it states whether a restart is required;
- measure whether any context/model/tool spend occurred before the configuration failure was detected.

## Current project context

The failure was encountered while preparing Cursor to work with:

- `michaelchaves-dev/GemRAG_Commons`
- `michaelchaves-dev/Subtract_Architect_Studios_GemRAG`
- the current Subtract Architect Studios local-house-agent / Gemma model work

The architectural lesson is to add exact secret-name validation to the Step0 / environment preflight so the system does not pay for a run before knowing whether the run can execute.
