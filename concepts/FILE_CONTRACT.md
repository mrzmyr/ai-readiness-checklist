# FILE_CONTRACT

Status: `REQUIRED`

## Requirement

Repo has one documented place for each concern: agent rules, contributing, security, testing, release, generated files.

## Acceptance Criteria

- `README.md`: product and user/dev quick start.
- `AGENTS.md`: agent instructions.
- `SECURITY.md`: vulnerability reporting.
- `.github/workflows/ci.yml`: green gate.
- `.github/PULL_REQUEST_TEMPLATE.md`: proof requirements.
- `docs/testing.md`: deeper test strategy when tests are non-trivial.
- `docs/release.md`: release/deploy flow when repo ships.

## Automatable Checks

- Required files exist for active repos.
- Optional files are required only when matching surfaces exist, e.g. release workflow -> release docs.

## Notes

Do not put everything in `AGENTS.md`. Keep `AGENTS.md` operational and link deeper docs.
