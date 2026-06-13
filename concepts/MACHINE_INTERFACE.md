# MACHINE_INTERFACE

Status: `IF_APPLICABLE`

## Requirement

CLIs and service tools expose stable `--json`, `--plain`, status, exit codes, or health endpoints.

## Acceptance Criteria

- CLI supports `--json` or `--plain`.
- Exit codes are documented.
- Service exposes health/status endpoint.
- Long-running commands print job/session id.

## Automatable Checks

- CLI docs mention `--json`, `--plain`, exit codes, or status.
- Service docs mention health/status endpoint.

## Example

```md
Exit codes: `0` success, `1` input error, `2` no-op, `3` external dependency unavailable.
```
