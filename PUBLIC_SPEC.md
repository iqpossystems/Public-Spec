# Telemetry Pilot — Public Spec (Non‑Sensitive)

This document is a **public-safe blueprint** for the P1‑S1 pilot.
It is intentionally written to avoid disclosing any private keys, internal endpoints, proprietary agent code, or sensitive operational details.

## Scope
This spec covers only:
- Dashboard + workflow structure (Notion control room).
- Pilot phases (W1/W2/W3) and what “done” means.
- Evidence/audit bundle shape (what must be recorded), in a sanitized form.

This spec does NOT include:
- Any real secrets (keys, tokens, seed phrases).
- Real infrastructure coordinates (IPs, hostnames, cloud accounts).
- Detailed redteam exploit code or bypass instructions.
- Full internal P1‑S1 master spec.

## Core Principles (Public)
- Keep the “engine” private; publish only the “blueprint”.
- Everything recorded as evidence should be shareable at a chosen sanitization level (Public / Partner / Private).
- Runs should be reproducible from parameters + sanitized outputs.

## Pilot Timeline (3 weeks)
### W1 — Telemetry calibration (fusion + drift)
Goal: establish a stable baseline for “normal”, and calibrate alert/escalation thresholds under simulated drift.
Deliverables:
- Telemetry schema contract (events, required fields, signing placeholder).
- Monte‑Carlo drift simulation plan (inputs, ranges, seeds policy).
- Baseline dashboards: latency, error rate, integrity signals, drift indicators.
- One Evidence Bundle per major calibration run.

### W2 — Redteam simulations (provenance + sybil)
Goal: test whether provenance tampering and sybil-style stressors are detected and handled in the workflow.
Deliverables:
- Provenance injection test cases (sanitized descriptions).
- Sybil simulation plan focused on “anchor-like” trust sources (no real anchor details).
- Canary gating checklist (what must pass before “promoted”).
- Findings logged with severity + remediation tasks.

### W3 — Rekey + rollback drills (game-days)
Goal: demonstrate operational readiness under routine rotation and injected failures.
Deliverables:
- Rekey cadence policy (e.g., quarterly) as a schedule + checklist.
- Fault injection scenarios (including simulated orbital/remote-anchor unavailability).
- Rollback game-day procedure with clear abort/continue criteria.
- Drill evidence bundles + sign-off notes.

## Evidence Bundles (Public-safe shape)
Every major run produces a compact “Evidence Bundle” containing only:
- Spec identifier (version string) + public digest identifiers (no secrets).
- Run metadata: run-id, date, environment label, parameters summary.
- Canary report summary (pass/fail + reasons, sanitized).
- Attestation placeholders (e.g., “multisig verified” / “HSM attested”) without exposing keys.
- Rollback / replay check summary (what was checked + outcome).

Suggested sanitization levels:
- Public: aggregated metrics + outcomes only.
- Partner: adds more technical detail, still no secrets.
- Private: raw traces/logs only inside private vault.

## Notion Control Room (Minimum required)
Databases required:
1. Canonical Spec (single source for the public blueprint + link to private repo)
2. Pilot Backlog (tasks by week/workstream/status)
3. Sim Runs (each execution instance + outcome)
4. Evidence Bundles (one per run)
5. Incidents & Findings (issues + severity + fix links)

Required relations:
- Backlog ↔ Runs
- Runs ↔ Evidence Bundles
- Findings ↔ Runs + Evidence Bundles + Fix Tasks

Required views:
- Backlog board by Status
- Backlog filtered by Week (W1/W2/W3)
- Runs timeline
- “Failures only” Runs view
- Evidence filtered to “Public”

## Operating Rules
- Never paste secrets into Notion or this file.
- Never commit secrets to GitHub (even in a private repo).
- Only share sanitized evidence outside the private vault.
