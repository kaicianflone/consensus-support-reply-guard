---
name: consensus-support-reply-guard
description: Risk-aware support response governance with persona-weighted consensus. Detects legal/sensitive/confidentiality issues, applies hard-block policy checks, and writes auditable decision artifacts for customer-facing automation.
homepage: https://github.com/kaicianflone/consensus-support-reply-guard
source: https://github.com/kaicianflone/consensus-support-reply-guard
---

# consensus-support-reply-guard

`consensus-support-reply-guard` is a customer-trust guard for support workflows.

## What this skill does

- evaluates support drafts before sending
- detects high-risk claim patterns
- blocks or rewrites responses when policy violations appear
- updates persona reputations based on final decision alignment
- preserves decision history in board artifacts

## Why this matters

Support replies are high-frequency and brand-critical. This skill prevents overconfident legal/PII mistakes at scale.

## Ecosystem role

Composes with persona generation + consensus board state so support quality improves through persistent decision memory.

## Ideal scenarios

- automated ticket triage replies
- L1/L2 AI response review gates
- regulated or enterprise support channels

## Quick start

```bash
node --import tsx run.js --input ./examples/input.json
```

## Tool-call integration

This skill is wired to the consensus-interact contract boundary (via shared consensus-guard-core wrappers where applicable):
- readBoardPolicy
- getLatestPersonaSet / getPersonaSet
- writeArtifact / writeDecision
- idempotent decision lookup

This keeps board orchestration standardized across skills.

## Invoke Contract

This skill exposes a canonical entrypoint:

- `invoke(input, opts?) -> Promise<OutputJson | ErrorJson>`

`invoke()` starts the guard flow, which then executes persona evaluation and consensus-interact-contract board operations (via shared guard-core wrappers where applicable).
