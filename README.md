# AI Readiness Checklist

Date: 2026-06-13

Basis: original top 30 public `steipete` repos by stars, plus expanded scan of active public repos for newer agent, CI, SECURITY, PR, and service patterns. The extraction notes and top-30 evidence table live in [`research/steipete-top30.md`](research/steipete-top30.md).

Goal: one canonical checklist that can later become an automated repo-readiness test. Detailed examples live in linked Markdown files, not in this checklist.

Status labels:

- `REQUIRED`: every active repo.
- `SERVICE`: web server, TypeScript backend, worker, API, or deployed service.
- `OSS`: public/open-contribution repo.
- `IF_APPLICABLE`: required only when that surface exists.
- `MATURE`: useful for larger or high-risk repos, not baseline.

## Checklist

| Done | Concept | Status | Requirement | Details |
|---|---|---|---|---|
| [ ] | `REPO_PURPOSE` | `REQUIRED` | `README.md` defines product purpose, install path, user-facing usage, and dev quick start. | [Details](concepts/REPO_PURPOSE.md) |
| [ ] | `FILE_CONTRACT` | `REQUIRED` | Repo has one documented place for each concern: agent rules, contributing, security, testing, release, generated files. | [Details](concepts/FILE_CONTRACT.md) |
| [ ] | `AGENT_ENTRYPOINT` | `REQUIRED` | root `AGENTS.md` defines exact agent operating rules, repo map, commands, verification, and safety caveats. | [Details](concepts/AGENT_ENTRYPOINT.md) |
| [ ] | `SHARED_RULES_BOUNDARY` | `IF_APPLICABLE` | shared rules are in a clearly delimited generated block; repo-local rules stay outside that block. | [Details](concepts/SHARED_RULES_BOUNDARY.md) |
| [ ] | `MAINTENANCE_STATE` | `IF_APPLICABLE` | archived or maintenance-only repos state support status, accepted change types, and replacement project. | [Details](concepts/MAINTENANCE_STATE.md) |
| [ ] | `RUNTIME_TOOLING` | `REQUIRED` | repo pins or documents runtime, package manager, install command, and lockfile policy. | [Details](concepts/RUNTIME_TOOLING.md) |
| [ ] | `CHECK_SCRIPT` | `REQUIRED` | primary green gate is named `check` and runs format check, lint/static analysis, typecheck/build, and tests. | [Details](concepts/CHECK_SCRIPT.md) |
| [ ] | `CI_CHECK` | `REQUIRED` | CI runs the same `check` command or a documented strict superset. | [Details](concepts/CI_CHECK.md) |
| [ ] | `FOCUSED_COMMANDS` | `REQUIRED` | docs list focused commands for common change surfaces, but still require `check` before handoff. | [Details](concepts/FOCUSED_COMMANDS.md) |
| [ ] | `VERIFICATION_MATRIX` | `REQUIRED` | `AGENTS.md` maps change type to required proof and exact commands. | [Details](concepts/VERIFICATION_MATRIX.md) |
| [ ] | `TEST_STRATEGY` | `REQUIRED` | `docs/testing.md` or `AGENTS.md` defines test types, fixture locations, naming pattern, and live-test gates. | [Details](concepts/TEST_STRATEGY.md) |
| [ ] | `SERVICE_BOUNDARIES` | `SERVICE` | backend layout separates routes/controllers, services, repositories, clients, workers, and generated code. | [Details](concepts/SERVICE_BOUNDARIES.md) |
| [ ] | `LOCAL_DEV_LOOP` | `SERVICE` | docs define commands to start dependencies, run server/worker, stop services, and verify health. | [Details](concepts/LOCAL_DEV_LOOP.md) |
| [ ] | `CONFIG_ENV_CONTRACT` | `SERVICE` | docs define required env vars, `.env.example`, config defaults, secret sources, and local-vs-production behavior. | [Details](concepts/CONFIG_ENV_CONTRACT.md) |
| [ ] | `DATABASE_MIGRATIONS` | `SERVICE IF_APPLICABLE` | schema changes have migration commands, validation commands, rollback/forward policy, and test database guidance. | [Details](concepts/DATABASE_MIGRATIONS.md) |
| [ ] | `HEALTHCHECK_SMOKE` | `SERVICE` | deployed or local services expose health/readiness smoke commands suitable for CI or handoff proof. | [Details](concepts/HEALTHCHECK_SMOKE.md) |
| [ ] | `MACHINE_INTERFACE` | `IF_APPLICABLE` | CLIs and service tools expose stable `--json`, `--plain`, status, exit codes, or health endpoints. | [Details](concepts/MACHINE_INTERFACE.md) |
| [ ] | `SECURITY_POLICY` | `REQUIRED` | `SECURITY.md` defines private vulnerability reporting, supported versions, scope, expectations, and confidentiality. | [Details](concepts/SECURITY_POLICY.md) |
| [ ] | `SECRET_HANDLING` | `REQUIRED` | agent rules forbid secret logging, broad env dumps, unredacted auth headers, cookies, and private payloads. | [Details](concepts/SECRET_HANDLING.md) |
| [ ] | `LIVE_SYSTEM_GATES` | `REQUIRED` | normal checks avoid live accounts; live tests require explicit opt-in env vars and user approval. | [Details](concepts/LIVE_SYSTEM_GATES.md) |
| [ ] | `AI_PROVIDER_PREFLIGHT` | `IF_APPLICABLE` | paid or external AI/provider calls have dry-run/preflight/doctor commands and redacted diagnostics. | [Details](concepts/AI_PROVIDER_PREFLIGHT.md) |
| [ ] | `PR_PROOF` | `OSS` | PR template requires what changed, why, exact verification commands, docs/changelog decision, and reviewer notes. | [Details](concepts/PR_PROOF.md) |
| [ ] | `ISSUE_INTAKE` | `OSS` | issue templates require exact repro, version, platform, expected vs actual, and redacted logs. | [Details](concepts/ISSUE_INTAKE.md) |
| [ ] | `DEPENDENCY_GOVERNANCE` | `OSS MATURE` | dependency update policy and Dependabot config define ecosystems, cadence, grouping, and PR limits. | [Details](concepts/DEPENDENCY_GOVERNANCE.md) |
| [ ] | `CODEOWNERS` | `OSS MATURE` | active public repos define default review ownership. | [Details](concepts/CODEOWNERS.md) |
| [ ] | `GENERATED_ARTIFACTS` | `IF_APPLICABLE` | generated files are listed with source-of-truth inputs, regeneration command, and "do not hand edit" rule. | [Details](concepts/GENERATED_ARTIFACTS.md) |
| [ ] | `RELEASE_DELIVERY` | `IF_APPLICABLE` | release docs define version bumps, artifact/package publish, deploy, smoke proof, and failure handling. | [Details](concepts/RELEASE_DELIVERY.md) |
| [ ] | `CHANGELOG_POLICY` | `IF_APPLICABLE` | user-visible changes have a documented changelog rule and location. | [Details](concepts/CHANGELOG_POLICY.md) |
| [ ] | `SECOND_OPINION` | `MATURE` | risky changes define when to ask another model/tool, how to dry-run context, and how to cite results. | [Details](concepts/SECOND_OPINION.md) |

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
