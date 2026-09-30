# Remediate Everything

Vulnerability management after the scanner stops helping.

Finding a vulnerability is often the easiest part. Then the real work begins: prove that it matters, map it to the running environment, find the owner, explain it to management, negotiate a change window, handle the exception, and verify that the exposure is actually gone.

When that work stalls and an incident happens, people still ask the security team why the issue was not fixed.

Assessing a vulnerability is difficult. Turning it into a decision that management and engineering can act on is a challenge of its own. Some days, it is frustrating. So I built this with AI: a small collection of skills for the work between detection and verified remediation.

## What This Repository Contains

Eight AI skills cover different remediation cases and audiences. Use the general skill when the request spans several stages. Use a specialist when the job is clear.

| Skill | Use it when |
|---|---|
| [`remediate-everything`](./remediate-everything/SKILL.md) | You need a general workflow or help routing a mixed remediation request. |
| [`validate-vulnerability-exposure`](./validate-vulnerability-exposure/SKILL.md) | A finding is disputed, incomplete, duplicated, or missing applicability and runtime evidence. |
| [`prioritize-vulnerability-remediation`](./prioritize-vulnerability-remediation/SKILL.md) | You need a defensible remediation order based on threat, sensitivity, confirmed volume, exposure, blast radius, controls, and evidence confidence. |
| [`pitch-vulnerability-remediation`](./pitch-vulnerability-remediation/SKILL.md) | A manager, executive, CISO, budget owner, or change authority must make a decision. |
| [`plan-vulnerability-remediation`](./plan-vulnerability-remediation/SKILL.md) | Engineering, product, platform, cloud, IAM, operations, or a vendor needs an executable fix plan. |
| [`govern-vulnerability-risk`](./govern-vulnerability-risk/SKILL.md) | GRC, audit, or vulnerability management needs SLA, evidence, exception, or reporting governance. |
| [`accept-vulnerability-risk`](./accept-vulnerability-risk/SKILL.md) | An accountable business owner must accept, reject, condition, or escalate residual risk. |
| [`verify-remediation-closure`](./verify-remediation-closure/SKILL.md) | A fix needs runtime validation, durable closure, or investigation after the finding returns. |

## The Principles Behind the Skills

- Separate what is observed, inferred, and unknown.
- Treat scanner output as an assertion that needs context and evidence.
- Use CVSS and tool severity as inputs, not the final business priority.
- Consider sensitivity, confirmed affected volume, exposure, identity, business criticality, and control effectiveness.
- Keep workflow closure separate from exposure closure.
- Give every action an owner and every temporary decision an expiry.
- Retest the exposure after the fix, including normal restart, rebuild, and redeployment paths when relevant.
- Let security provide evidence and options while the accountable owner makes the business decision.

## Install in Codex

The easiest option is to paste this into Codex:

```text
Use $skill-installer to install all eight skills from
https://github.com/mikhsanfbusiness-alt/Remediate-Everything.

Install these paths:
- remediate-everything
- validate-vulnerability-exposure
- prioritize-vulnerability-remediation
- pitch-vulnerability-remediation
- plan-vulnerability-remediation
- govern-vulnerability-risk
- accept-vulnerability-risk
- verify-remediation-closure
```

Codex installs the skills in `$CODEX_HOME/skills/`, or `~/.codex/skills/` when `CODEX_HOME` is not set. Send a new message after installation so Codex reloads its available skills.

To verify the setup, try:

```text
Use $remediate-everything to route a vulnerability finding from validation through verified closure. Tell me which specialist skill should handle each stage.
```

Codex can discover a relevant skill automatically from your request, but explicit `$skill-name` invocation is useful when you want predictable routing.

## Manual Installation

Each folder is a standalone skill containing a `SKILL.md` file. Download or clone the repository, then copy the eight skill folders into one of these locations:

- Codex: `$CODEX_HOME/skills/` or `~/.codex/skills/`
- Cross-runtime agents: `~/.agents/skills/`

Copy all eight folders for the complete workflow, or install only the specialists you need. Keep `remediate-everything` when you want the general router.

## Example Requests

If your agent supports `$skill-name` invocation:

```text
Use $remediate-everything to turn this finding into an owned remediation brief.

Use $validate-vulnerability-exposure to determine whether this SCA finding is present, loaded, reachable, and relevant in production.

Use $prioritize-vulnerability-remediation to rank these findings. Include data sensitivity, confirmed affected hosts with the estate denominator, and external exposure.

Use $pitch-vulnerability-remediation to create a six-slide decision deck for the engineering manager.

Use $plan-vulnerability-remediation to turn this confirmed exposure into an engineering ticket with rollout, rollback, interim control, and retest criteria.

Use $accept-vulnerability-risk to review this exception request and identify missing approval, expiry, controls, or revalidation.

Use $verify-remediation-closure to confirm the fix survived a restart and the next deployment.
```

## Repository Layout

```text
.
|-- README.md
|-- remediate-everything/
|   `-- SKILL.md
|-- validate-vulnerability-exposure/
|   `-- SKILL.md
|-- prioritize-vulnerability-remediation/
|   `-- SKILL.md
|-- pitch-vulnerability-remediation/
|   `-- SKILL.md
|-- plan-vulnerability-remediation/
|   `-- SKILL.md
|-- govern-vulnerability-risk/
|   `-- SKILL.md
|-- accept-vulnerability-risk/
|   `-- SKILL.md
`-- verify-remediation-closure/
    `-- SKILL.md
```

## Boundaries

These skills organize evidence, decisions, remediation work, and verification. They do not replace authorized scanning, technical testing, company policy, legal advice, or an accountable risk owner. They do not justify unsupported exploitation claims or indefinite exceptions.

Review every generated decision against the source evidence before using it in production, audit, regulatory, or executive contexts.

## Why I Made This

I used to imagine vulnerability management as a short workflow: find the problem, tell the owner, fix it, close the ticket. That was optimistic.

In practice, every remediation request arrives with side quests. I have to prove the finding, explain why the score is not the whole story, find someone who can approve the work, negotiate downtime, chase the exception, and retest the fix. Sometimes the same exposure comes back wearing a different hostname, and the ticket gets a second season.

Somewhere in the middle, the security team becomes the translator, project manager, evidence librarian, calendar reminder, and professional sender of “just following up” messages. If an incident happens, the awkward question still arrives: “Why wasn't this fixed?”

Assessing the vulnerability is hard. Getting management and engineering to agree on what it means, who owns the decision, and what happens next is a separate job.

After enough rounds of this, I decided my AI should help carry the checklist. I made Remediate Everything to turn that frustration into something reusable: clearer evidence, named owners, practical plans, and closure that means more than changing a ticket status.

## Contributing

Issues and pull requests are welcome. A useful contribution includes the remediation situation, the audience, the current failure, and the behaviour the skill should produce instead.
