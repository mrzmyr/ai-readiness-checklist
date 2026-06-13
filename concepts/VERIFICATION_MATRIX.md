# VERIFICATION_MATRIX

Status: `REQUIRED`

## Requirement

`AGENTS.md` maps change type to required proof and exact commands.

## Acceptance Criteria

- Maps change type to exact proof.
- Covers docs, logic, API, worker, DB, auth/security, generated code, release.

## Automatable Checks

- `AGENTS.md` contains a Markdown table under `Verification`.
- Table contains `pnpm check` or equivalent.

## Example

```md
| Change | Required proof |
|---|---|
| API route | Focused integration test + `pnpm check` |
| DB schema | Migration check + repository test + `pnpm check` |
| Auth/security | Stubbed tests only unless live approval is explicit |
```
