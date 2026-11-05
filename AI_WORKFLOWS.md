# AI workflows — from prompts to reliable software

**Kenzo Fujimoto · [Portfolio](https://kenzofujimoto.com)**

This is a **sanitized, portfolio-safe showcase** of how I use coding agents, MCP tools and security guardrails. It demonstrates my approach, not an automated claim that every sample command has run in production.

> **Principle:** AI accelerates delivery; the engineer owns correctness, authorization, security and outcomes.

## The workflow I follow

```text
Discover problem → scope + acceptance criteria
                 → bounded agent plan (human checkpoint)
                 → implementation + tests
                 → security / data-boundary review
                 → preview + human approval
                 → deploy and observe
                 → record learnings / handoff
```

These examples draw on my own practices and configuration patterns from a personal Claude Code kit, where I adapted existing open-source templates for product, test and security workflows. **I did not author every base agent, skill or upstream framework.**

## 1. Structured prompt: from a problem to a reviewable PR

```text
ROLE: Full-stack engineer with product and security responsibilities.
GOAL: Solve [problem] for [user group] with measurable acceptance criteria.
CONTEXT: [current architecture], [repositories], [known constraints].
BOUNDARIES: Do not access production credentials or customer data.
          Do not expand scope, change permissions, or deploy without approval.
STEP 1: Read existing code and document assumptions.
STEP 2: Propose minimal architecture, trade-offs, risks and test strategy.
STOP: Request human approval before editing.
STEP 3: Write an initially failing test for each key acceptance criterion.
STEP 4: Implement the smallest safe solution; run checks.
STEP 5: Report changed files, tests, security concerns and rollback plan.
OUTPUT: Short technical plan, code diff, test evidence and reviewer checklist.
```

**Why this works:** constrained inputs, explicit stop conditions, verifiable acceptance and handoff artifacts. Prompting is a process design skill, not a collection of magic phrases.

## 2. Security review before shipping AI-generated code

```text
Review this change as a skeptical AppSec engineer.
Scope: [PR diff and relevant call paths].
Threat model: untrusted inputs, identities, tenant boundaries and secrets.
Check:
- Authentication vs authorization and least privilege
- Cross-tenant access; database Row-Level Security (when applicable)
- Injection, SSRF, XSS and unsafe deserialization
- Secrets, sensitive data in logs, privacy/LGPD risks
- Dependency changes, tests and failure paths
For every finding, return: severity, exact code location, exploit path,
recommended fix and a regression test.
Do not assert that a vulnerability is fixed until the test verifies it.
Block deployment on unresolved critical findings.
```

**Demonstrated in:** KlinikSys security checks and K-Ops read-only design; these are examples of safeguards, not a certification that any product is vulnerability-free.

## 3. MCP-based commercial research: research ≠ permission to send

```text
GOAL: Find relevant business prospects for [approved product/segment].
Use only authorized sources and available MCP connectors.
For each prospect, record organization, evidence source, relevance,
relevant contact route, and confidence.
Check for duplicates against the existing approved pipeline.
Generate a personalized draft; label factual claims vs assumptions.
STOP: Do not send email, create a paid application, or mutate the sales
pipeline without explicit user approval.
On approval only, execute the authorized action and log its result.
If an integration fails, report the error; never claim successful delivery.
```

**Applied context:** EcoCrachá's separate prospecting and outreach workflow. The public showcase omits targets, addresses, credentials, account data, message histories and operational playbooks.

## 4. Handoffs and multi-agent collaboration

A useful agent session produces artifacts another engineer can verify:

- **Planning agent:** problem definition, requirements, non-goals, trade-offs and open questions.
- **Implementation agent:** small, testable changes with reproducible commands.
- **Security reviewer:** independent threat review with evidence and severity.
- **Verification agent:** tests, preview, regression checks and gaps.
- **Human owner:** chooses if the work is acceptable for merge or release.

A `HANDOFF.md` captures what changed, what was validated, what is unfinished and the exact next action, without copying secrets.

## 5. Caveman and efficient context engineering

I study **[Caveman](https://github.com/JuliusBrussee/caveman)** as a third-party approach to reducing unnecessary agent output and large tool-result context. The right objective is **reduce cost without losing critical evidence**: preserve raw outputs where needed, keep security-relevant details, and measure before claiming savings.

I do **not** claim to have created Caveman, reproduced its benchmarks or measured token reductions in my projects.

## 6. Selected open-source references

| Reference | What I learn from it | Ownership |
| --- | --- | --- |
| [Antigravity Kit](https://github.com/vudovn/antigravity-kit) | Agent roles, slash commands, workflow structure | Upstream project; my private kit contains adaptations |
| [Caveman](https://github.com/JuliusBrussee/caveman) | Compact tool results and context efficiency | Third party |
| [Matt Pocock's skills](https://github.com/mattpocock/skills) | Domain vocabulary, TDD, diagnostics, specs and architectural feedback loops | Third-party reference, not bundled |
| [Superpowers by obra](https://github.com/obra/superpowers) | Brainstorming, plan-first development, worktrees, subagents and verification | Third-party reference, not bundled |
| [My agent-skills](https://github.com/kenzofujimoto/agent-skills) | Published skill packaging, validation and docs | My maintained repository; includes credited upstream material |

## Portfolio mapping

- **[KlinikSys](https://kliniksys.com):** offline-first constraints, automated testing, security boundaries.
- **[Mackenzo](https://www.mackenzo.com/):** RAG, document ingestion and answer grounding.
- **[EcoCrachá](https://www.ecocracha.com/):** multilingual product, 3D customization, MCP-assisted prospecting.
- **K-Ops (private):** least-privilege, read-only operational integrations.
- **[OpenEMS](https://github.com/kenzofujimoto/openems-server):** open-source endpoint-management design and implementation.

*Last curated for portfolio presentation: November 2026. Follow each upstream project's license and current documentation.*
