# CHECK_SCRIPT

Status: `REQUIRED`

## Requirement

Primary green gate is named `check` and runs format check, lint/static analysis, typecheck/build, and tests.

## Acceptance Criteria

- Script is named exactly `check`.
- Runs format check, lint/static analysis, typecheck/build, and tests.
- Requires no secrets/live accounts.
- Exits nonzero on failure.

## Automatable Checks

- `package.json#scripts.check` exists for Node repos.
- `check` command references lint/typecheck/test/build equivalents.
- `check` does not reference live-test env vars.

## Example

```json
{
  "scripts": {
    "format:check": "oxfmt --check .",
    "lint": "oxlint --deny-warnings src tests",
    "typecheck": "tsgo --noEmit",
    "test": "vitest run",
    "build": "tsgo -p tsconfig.build.json",
    "check": "pnpm format:check && pnpm lint && pnpm typecheck && pnpm test && pnpm build"
  }
}
```
