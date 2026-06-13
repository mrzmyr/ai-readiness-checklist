# PR_PROOF

Status: `OSS`

## Requirement

PR template requires what changed, why, exact verification commands, docs/changelog decision, and reviewer notes.

## Acceptance Criteria

- What changed.
- Why.
- Verification commands.
- Docs/changelog decision.
- Reviewer notes.

## Automatable Checks

- `.github/PULL_REQUEST_TEMPLATE.md` exists.
- Contains `Verification`.
- Contains command checklist or `check`.

## Example

```md
## Verification

- [ ] `pnpm check` passed
- [ ] Focused regression: `<command>`
- [ ] Docs/changelog updated or not needed because: `<reason>`
- [ ] No live secrets/accounts used
```
