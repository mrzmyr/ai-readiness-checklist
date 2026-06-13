# CI_CHECK

Status: `REQUIRED`

## Requirement

CI runs the same `check` command or a documented strict superset.

## Acceptance Criteria

- CI installs same package manager/runtime.
- CI runs `pnpm check` or a documented strict superset.
- CI has no local absolute paths.
- Live tests are separate.

## Automatable Checks

- `.github/workflows/*.yml` exists.
- At least one workflow runs `pnpm check`, `npm run check`, `make check`, or equivalent.
- Workflow does not require repo secrets for normal PR checks.

## Example

```yaml
- uses: pnpm/action-setup@v4
  with:
    version: 10
- uses: actions/setup-node@v4
  with:
    node-version: 24
    cache: pnpm
- run: pnpm install --frozen-lockfile
- run: pnpm check
```
