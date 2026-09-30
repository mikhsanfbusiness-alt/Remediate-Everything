---
name: remediate-everything
description: Use when a vulnerability remediation request spans multiple audiences or stages, or when the user needs a general workflow before choosing a specialized validation, prioritization, pitching, planning, governance, acceptance, or closure skill.
---

# Remediate Everything

## Purpose

Turn uncertain security findings into defensible decisions, owned actions, and verified exposure reduction. Use this skill for mixed or general requests and route focused work to one specialized skill.

## Shared Rules

- Separate `Observed`, `Inferred`, and `Unknown`.
- Treat scanner output as an assertion with confidence, not proof.
- Use CVSS and tool severity as inputs, not business priority.
- Never invent exploitation, impact, costs, deadlines, compliance duties, or certainty.
- Request only the minimum safe proof needed. Do not weaponize a finding.
- Name constraints, owners, and decision authorities without shaming teams.
- Distinguish workflow closure from exposure closure.

## Routing

| Primary need | Use |
|---|---|
| Applicability, false positives, conflicting tools, runtime, identity, API, or AI evidence | `validate-vulnerability-exposure` |
| Remediation approval, funding, scheduling, ownership, or executive escalation | `pitch-vulnerability-remediation` |
| Executable engineering, product, platform, cloud, IAM, operations, or vendor plan | `plan-vulnerability-remediation` |
| SLA, evidence, exception inventory, audit, metrics, or cross-business-unit governance | `govern-vulnerability-risk` |
| Runtime retest, durable closure, recurrence, or reopened findings | `verify-remediation-closure` |
| Ranking by threat, sensitivity, confirmed volume, exposure, blast radius, and controls | `prioritize-vulnerability-remediation` |
| Accept, reject, condition, or escalate residual-risk decisions | `accept-vulnerability-risk` |

Use only the specialized skills required by the requested deliverables. Keep this skill as the shared context when several jobs interact.

## General Workflow

1. Validate the exposure, scope, evidence confidence, owner, and important unknowns.
2. Prioritize using threat, sensitivity, exposure, confirmed affected volume, identity blast radius, business criticality, and controls.
3. Translate the technical condition into the affected business process and the exact decision required.
4. Present a permanent fix, a time-limited mitigation, and risk acceptance only when each is feasible.
5. Record the action, owner, decision authority, dependencies, due date, interim control, rollback, and retest.
6. Verify the result across relevant build, deployment, runtime, external, identity, and governance evidence.
7. Test durability after restart, reboot, redeployment, rebuild, or configuration reconciliation when applicable.

## General Output

Produce a remediation brief with `Decision required`, `Observed evidence`, `Inferences`, `Unknowns`, `Priority rationale`, `Options`, `Recommended action`, `Owner`, `Decision authority`, `Dependencies`, `Interim control`, `Due date`, `Retest`, and `Residual risk`.

If the request names an audience, adapt vocabulary and detail without changing the underlying evidence. Executives need a decision; engineers need an implementation contract; GRC and audit need provenance; risk owners need residual-risk terms.

## Final Check

Every claim needs evidence or an explicit unknown. Every action needs an owner and validation method. Every temporary control or acceptance needs an expiry. Do not claim remediation until the exposure has been retested.

