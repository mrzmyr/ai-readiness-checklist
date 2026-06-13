# REPO_PURPOSE

Status: `REQUIRED`

## Requirement

`README.md` defines product purpose, install path, user-facing usage, and dev quick start.

## Acceptance Criteria

- First screen explains what the project does and who uses it.
- Install or run command is present.
- Dev quick start is present.
- For services, local URL or API entrypoint is present.

## Automatable Checks

- `README.md` exists.
- `README.md` contains install/run/dev heading or command.
- `README.md` mentions a local command or URL for service repos.

## Example

```md
# Event API

Event API receives partner webhooks, validates them, normalizes payloads, and stores events in Postgres for downstream workers.

## Development

pnpm install
pnpm dev:deps
pnpm dev
curl -fsS http://127.0.0.1:3000/healthz
```
