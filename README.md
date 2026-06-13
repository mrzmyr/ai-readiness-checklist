# AI Readiness Checklist

Date: 2026-06-13

Basis: original top 30 public `steipete` repos by stars, plus expanded scan of active public repos for newer agent, CI, SECURITY, PR, and service patterns. The extraction notes and top-30 evidence table live in [`research/steipete-top30.md`](research/steipete-top30.md).

Goal: one canonical checklist that can later become an automated repo-readiness test. Detailed examples live in linked Markdown files, not in this checklist.

## Checklist

### General

Applies to every active repo.

| Concept | Requirement | Details |
|---|---|---|
| `REPO_PURPOSE` | `README.md` defines product purpose, install path, user-facing usage, and dev quick start. | [Details](concepts/REPO_PURPOSE.md) |
| `FILE_CONTRACT` | Repo has one documented place for each concern: agent rules, contributing, security, testing, release, generated files. | [Details](concepts/FILE_CONTRACT.md) |
| `AGENT_ENTRYPOINT` | root `AGENTS.md` defines exact agent operating rules, repo map, commands, verification, and safety caveats. | [Details](concepts/AGENT_ENTRYPOINT.md) |
| `RUNTIME_TOOLING` | repo pins or documents runtime, package manager, install command, and lockfile policy. | [Details](concepts/RUNTIME_TOOLING.md) |
| `CHECK_SCRIPT` | primary green gate is named `check` and runs format check, lint/static analysis, typecheck/build, and tests. | [Details](concepts/CHECK_SCRIPT.md) |
| `CI_CHECK` | CI runs the same `check` command or a documented strict superset. | [Details](concepts/CI_CHECK.md) |
| `FOCUSED_COMMANDS` | docs list focused commands for common change surfaces, but still require `check` before handoff. | [Details](concepts/FOCUSED_COMMANDS.md) |
| `VERIFICATION_MATRIX` | `AGENTS.md` maps change type to required proof and exact commands. | [Details](concepts/VERIFICATION_MATRIX.md) |
| `TEST_STRATEGY` | `docs/testing.md` or `AGENTS.md` defines test types, fixture locations, naming pattern, and live-test gates. | [Details](concepts/TEST_STRATEGY.md) |
| `SECURITY_POLICY` | `SECURITY.md` defines private vulnerability reporting, supported versions, scope, expectations, and confidentiality. | [Details](concepts/SECURITY_POLICY.md) |
| `SECRET_HANDLING` | agent rules forbid secret logging, broad env dumps, unredacted auth headers, cookies, and private payloads. | [Details](concepts/SECRET_HANDLING.md) |
| `LIVE_SYSTEM_GATES` | normal checks avoid live accounts; live tests require explicit opt-in env vars and user approval. | [Details](concepts/LIVE_SYSTEM_GATES.md) |

### Service

Applies to web servers, TypeScript backends, workers, APIs, or deployed services.

| Concept | Requirement | Details |
|---|---|---|
| `SERVICE_BOUNDARIES` | backend layout separates routes/controllers, services, repositories, clients, workers, and generated code. | [Details](concepts/SERVICE_BOUNDARIES.md) |
| `LOCAL_DEV_LOOP` | docs define commands to start dependencies, run server/worker, stop services, and verify health. | [Details](concepts/LOCAL_DEV_LOOP.md) |
| `CONFIG_ENV_CONTRACT` | docs define required env vars, `.env.example`, config defaults, secret sources, and local-vs-production behavior. | [Details](concepts/CONFIG_ENV_CONTRACT.md) |
| `HEALTHCHECK_SMOKE` | deployed or local services expose health/readiness smoke commands suitable for CI or handoff proof. | [Details](concepts/HEALTHCHECK_SMOKE.md) |

### Open Source

Applies to public or open-contribution repos.

| Concept | Requirement | Details |
|---|---|---|
| `PR_PROOF` | PR template requires what changed, why, exact verification commands, docs/changelog decision, and reviewer notes. | [Details](concepts/PR_PROOF.md) |
| `ISSUE_INTAKE` | issue templates require exact repro, version, platform, expected vs actual, and redacted logs. | [Details](concepts/ISSUE_INTAKE.md) |

### Conditional

Applies only when the repo has the matching surface.

| Concept | Requirement | Details |
|---|---|---|
| `SHARED_RULES_BOUNDARY` | shared rules are in a clearly delimited generated block; repo-local rules stay outside that block. | [Details](concepts/SHARED_RULES_BOUNDARY.md) |
| `MAINTENANCE_STATE` | archived or maintenance-only repos state support status, accepted change types, and replacement project. | [Details](concepts/MAINTENANCE_STATE.md) |
| `DATABASE_MIGRATIONS` | schema changes have migration commands, validation commands, rollback/forward policy, and test database guidance. | [Details](concepts/DATABASE_MIGRATIONS.md) |
| `MACHINE_INTERFACE` | CLIs and service tools expose stable `--json`, `--plain`, status, exit codes, or health endpoints. | [Details](concepts/MACHINE_INTERFACE.md) |
| `AI_PROVIDER_PREFLIGHT` | paid or external AI/provider calls have dry-run/preflight/doctor commands and redacted diagnostics. | [Details](concepts/AI_PROVIDER_PREFLIGHT.md) |
| `GENERATED_ARTIFACTS` | generated files are listed with source-of-truth inputs, regeneration command, and "do not hand edit" rule. | [Details](concepts/GENERATED_ARTIFACTS.md) |
| `RELEASE_DELIVERY` | release docs define version bumps, artifact/package publish, deploy, smoke proof, and failure handling. | [Details](concepts/RELEASE_DELIVERY.md) |
| `CHANGELOG_POLICY` | user-visible changes have a documented changelog rule and location. | [Details](concepts/CHANGELOG_POLICY.md) |

### Mature

Useful for larger, high-risk, or heavily maintained repos.

| Concept | Requirement | Details |
|---|---|---|
| `DEPENDENCY_GOVERNANCE` | dependency update policy and Dependabot config define ecosystems, cadence, grouping, and PR limits. | [Details](concepts/DEPENDENCY_GOVERNANCE.md) |
| `CODEOWNERS` | active public repos define default review ownership. | [Details](concepts/CODEOWNERS.md) |
| `SECOND_OPINION` | risky changes define when to ask another model/tool, how to dry-run context, and how to cite results. | [Details](concepts/SECOND_OPINION.md) |

## Minimal Baseline

For an active TypeScript backend/service, the non-negotiable subset is:

- `REPO_PURPOSE`
- `FILE_CONTRACT`
- `AGENT_ENTRYPOINT`
- `RUNTIME_TOOLING`
- `CHECK_SCRIPT`
- `CI_CHECK`
- `FOCUSED_COMMANDS`
- `VERIFICATION_MATRIX`
- `TEST_STRATEGY`
- `SERVICE_BOUNDARIES`
- `LOCAL_DEV_LOOP`
- `CONFIG_ENV_CONTRACT`
- `HEALTHCHECK_SMOKE`
- `SECURITY_POLICY`
- `SECRET_HANDLING`
- `LIVE_SYSTEM_GATES`

## Automation Target

This checklist should become a linter that can fail CI. The linter should check file existence, required scripts, CI command parity, required headings, forbidden vague phrases, and explicit live-test gates. Human review remains needed for quality of prose, but structure should be machine-testable.
