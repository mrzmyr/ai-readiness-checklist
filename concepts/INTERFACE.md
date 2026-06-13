# INTERFACE

Status: `Conditional`

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

## References

- [`steipete/RepoBar` README](https://github.com/steipete/RepoBar/blob/main/README.md)
- [`steipete/Trimmy` README](https://github.com/steipete/Trimmy/blob/main/README.md)
- [`steipete/oracle` README](https://github.com/steipete/oracle/blob/main/README.md)
