# SECURITY_POLICY

Status: `REQUIRED`

## Requirement

`SECURITY.md` defines private vulnerability reporting, supported versions, scope, expectations, and confidentiality.

## Acceptance Criteria

- Private reporting channel.
- Supported versions.
- In-scope/out-of-scope.
- What to include.
- Response expectations.
- Confidentiality.

## Automatable Checks

- `SECURITY.md` exists.
- Contains `Reporting` or `Vulnerability`.
- Contains non-public reporting channel.

## Example

```md
Do not report vulnerabilities through public GitHub issues.
Email security@example.com with description, impact, reproduction steps, affected versions, and suggested fix if known.
```
