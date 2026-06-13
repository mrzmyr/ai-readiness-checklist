# ISSUE_INTAKE

Status: `OSS`

## Requirement

Issue templates require exact repro, version, platform, expected vs actual, and redacted logs.

## Acceptance Criteria

- Exact repro.
- Expected vs actual.
- Version.
- Platform.
- Logs with redaction reminder.

## Automatable Checks

- `.github/ISSUE_TEMPLATE/` exists.
- Bug template contains repro/version/platform/logs fields.

## Example

```yaml
- type: textarea
  id: repro
  attributes:
    label: Steps to reproduce
    description: Include exact commands.
```
