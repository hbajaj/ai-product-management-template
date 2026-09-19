# Juno PM

Juno is a P0 triage copilot that synthesizes noisy Slack threads and incident tickets into the top three grounded risk signals so on-call PMs can decide whether to roll back, hold, or ship within five minutes.

Himanshu Bajaj · AI Product Management Certification, 2026 Cohort · ai-product-management-sep05-26-weekend

This repo is my final project for the **AI Product Management Certification**. Each module's artefact lives in its own folder; this README is the dashboard and the pitch.

**How to use this template:** click **Use this template → Create a new repository**, name it `juno-pm`, and commit one module's artefact per session. Assemble this dashboard with the **Final Project Deliverables Builder** (paste its `README.md` output over this file).

---

## Module artefacts

### M1 · Prompting
- **System prompt** — [`01-prompting/system-prompt.md`](01-prompting/system-prompt.md)
- **Lovable prototype** — https://evidence-powered-prd.lovable.app/

### M2 · Strategy
- **Decision matrix** — [`02-strategy/decision-matrix.md`](02-strategy/decision-matrix.md)
- **AI Strategy one-pager** — [`02-strategy/strategy-one-pager.md`](02-strategy/strategy-one-pager.md)

### M3 · RAG / AI PRD
- **AI PRD** — [`03-rag-prd/prd.md`](03-rag-prd/prd.md)

### M4 · AI-Native UX
- **AI user flow** — [`04-ai-ux/user-flow.md`](04-ai-ux/user-flow.md)
- **Trust-gap mitigations** — [`04-ai-ux/trust-gaps.md`](04-ai-ux/trust-gaps.md)

### M5 · Agentic Workflows
- **Agent Workflow Spec (AWSpec)** — [`05-agentic-workflows/awspec.md`](05-agentic-workflows/awspec.md)
- **Agent Control Panel** — [`05-agentic-workflows/agent-control-panel.md`](05-agentic-workflows/agent-control-panel.md)

### M6 · Evals & Guardrails
- **Eval stack** — [`06-evals/eval-stack.md`](06-evals/eval-stack.md)
- **Human evaluation rubric** — [`06-evals/human-rubric.md`](06-evals/human-rubric.md)

---

## PM Execution Plan

### Where Juno is today
Juno is pre-pilot and specification-complete. The product scope, system prompt, retrieval requirements, AI-native user flow, trust mitigations, agent boundaries, human rubric, and three-layer evaluation stack are defined. The initial use case is deliberately narrow: read incident evidence from Slack and tickets, identify and rank the top three P0 risks, cite the supporting messages, communicate confidence, and recommend a next action and owner. Juno supports the incident decision; it does not make or execute the rollback / hold / ship decision.

### What ships next (next 2 sprints)
Sprint 1 · Build the trustworthy core
Connect read-only Slack and ticket sources with stable message and ticket indexes.
Implement the structured top-three output: risk, evidence citation, confidence bucket, recommended action, and suggested owner.
Add PII redaction, legal/contract escalation, human hand-off, and audit logging.
Build the binary citation-validity gate and seed a versioned regression set with at least 100 representative P0 cases

Sprint 2 · Shadow pilot and release decision
Run Juno in shadow mode with on-call PMs, SRE, and support; no autonomous operational actions.
Capture Useful / Not useful feedback and time from result display to the PM's recorded decision.
Grade 50 stratified P0 runs using 06-evals/human-rubric.md, including every hand-off case.
Review misses, add validated failures to the regression set, and make the pilot go / no-go decision against the numeric release gates.

### What I watch (dashboards)

User value: Useful rate and median time to rollback / hold / ship decision
Decision quality: Weekly Accuracy and Safety scores from the human-evaluation sample
Grounding: Citation-validity pass rate and unresolved-citation count
Trust: Confidence distribution, low-confidence hand-off rate, and grader disagreement rate
Safety: Critical safety failures, PII redaction failures, and legal/contract escalation rate
Operations: Volume by P0 type, incomplete-source rate, and corrective actions by owner and due date

### Red lines (what blocks shipping — numbers, not feelings)

Citation validity below 100%: one unresolved or fabricated citation blocks release.
Any critical safety failure: any Safety score of 1 blocks release.
Human Accuracy or Safety below 4.0/5 mean: the weekly batch fails.
Useful rate below 80%: expansion pauses until the failure pattern is corrected and retested.
Median decision time above 5 minutes: the core value proposition is not met.
Grader disagreement at or above 15% on any dimension: recalibrate the rubric before using the scores for a release decision.
Any attempted autonomous rollback, hold, ship, external message, or ticket mutation: stop the pilot and review authorization controls.

### Governance

Compliance: Minimize retained incident data, redact PII, preserve source-level access controls, and log retrievals, outputs, hand-offs, and grader decisions. Contractual or legal content is routed to an authorized human.
Safety: Juno remains read-only during the pilot. Low-confidence, conflicting, incomplete, or sensitive evidence triggers a hand-off rather than a forced recommendation.
Reliability: Every risk must resolve to included source evidence. Missing sources, tool failures, or invalid citations fail closed and display a clear fallback to manual triage.
Reputation: Juno separates evidence from inference, shows calibrated confidence, and never presents itself as the incident decision-maker. The accountable PM retains the final rollback / hold / ship decision.

---

## Build Insights

- **Friction point.**
Compressing a fast-moving, contradictory incident thread into exactly three risks without losing a critical signal or creating false certainty.
- **Key learning.**
A polished summary is not enough for P0 response. Trust comes from traceable citations, calibrated confidence, explicit hand-offs, and a concrete next action with an owner.
- **Aha moment.** None Yet

---

## Repo structure

```
juno-pm/
├── README.md                          ← this dashboard + pitch
├── 01-prompting/
│   ├── system-prompt.md               ← M1: Juno's system prompt
│   └── lovable-prototype.md           ← M1: prototype link + debrief
├── 02-strategy/
│   ├── decision-matrix.md             ← M2: build / buy / fine-tune / partner call
│   └── strategy-one-pager.md          ← M2: AI strategy one-pager
├── 03-rag-prd/
│   └── prd.md                         ← M3: AI PRD with retrieval requirements
├── 04-ai-ux/
│   ├── user-flow.md                   ← M4: AI-native user flow
│   └── trust-gaps.md                  ← M4: trust-gap mitigations
├── 05-agentic-workflows/
│   ├── awspec.md                      ← M5: Agent Workflow Spec
│   └── agent-control-panel.md         ← M5: Agent Control Panel
└── 06-evals/
    ├── eval-stack.md                  ← M6: layered eval stack
    └── human-rubric.md                ← M6: human evaluation rubric
```

---

_Certification submission — AI Product Management Certification._
