# CHANGELOG_POLICY

Status: `IF_APPLICABLE`

## Requirement

User-visible changes have a documented changelog rule and location.

## Acceptance Criteria

- User-visible changes require changelog entry.
- Internal-only/test-only changes may skip with reason.
- Format is documented.

## Automatable Checks

- `CHANGELOG.md` exists for released repos.
- `AGENTS.md` or `CONTRIBUTING.md` mentions changelog policy.

## Example

```md
Update `CHANGELOG.md` for user-visible behavior, config, CLI flags, API shape, migrations, or release changes.
```
