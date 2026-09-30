---
name: verify-remediation-closure
description: Use when a vulnerability ticket is marked fixed, mitigated, closed, decommissioned, or not applicable but exposure closure, runtime state, recurrence, durability, or audit evidence still needs verification.
---

# Verify Remediation Closure

## Purpose

Prove that the exposure is closed and stays closed. Workflow closure, patch installation, image rebuild, or disappearing assets are claims to verify, not closure evidence by themselves.

## Define Closure First

Write observable closure criteria before testing. Choose the relevant evidence planes:

- Build: vulnerable source, dependency, package, image, or artifact is removed, corrected, or demonstrably not applicable.
- Deployment: the intended release, digest, configuration, restart, or reboot reached every in-scope environment.
- Runtime: the vulnerable component or behaviour is absent, unreachable, or controlled in the running service.
- External: DNS, gateways, load balancers, routes, and exposed endpoints no longer provide the vulnerable path.
- Identity and data: excessive privileges, tokens, secrets, or downstream access are removed or reduced as intended.
- Governance: ticket, exception, approval, and evidence records match the verified technical state.

## Verification Workflow

1. Confirm scope using canonical service, artifact, workload, and owner identifiers.
2. Reproduce the original condition or use an equally direct safe test.
3. Verify the changed control and the resulting secure behaviour.
4. Check sibling environments, regions, namespaces, identities, images, or routes that share the same source.
5. Test durability after the normal event most likely to restore the issue: restart, reboot, redeploy, autoscaling, image rebuild, pipeline run, configuration reconciliation, or credential rotation.
6. Compare fresh results with the original evidence and record method, timestamp, and limitations.

Do not close solely because a scanner is green, a host disappeared, a ticket changed state, or an owner attested that work was completed.

## Reopened Findings

Classify the cause before treating a reopened finding as noise:

- remediation never reached runtime;
- old artifact or base image returned;
- source or IaC restored the weakness;
- service did not restart or reboot;
- another asset shares the vulnerable source;
- asset identity changed;
- scanner logic or collection method changed;
- prior closure evidence was wrong or stale.

Fix the shared source when recurrence crosses assets. Suppress only when current evidence supports a documented reason and review date.

## Closure Record

Output `Finding`, `Scope`, `Original evidence`, `Change`, `Retest method`, `Results by evidence plane`, `Durability event`, `Residual risk`, `Evidence links`, `Reviewer`, `Timestamp`, and `Disposition`.

Use only these dispositions: `closed`, `mitigated`, `not applicable`, `reopened`, or `unresolved`.

## Final Check

Closure requires fresh, reproducible evidence for the current runtime and exposure path. If durability was not tested, state that limitation and do not claim the issue will remain closed.
