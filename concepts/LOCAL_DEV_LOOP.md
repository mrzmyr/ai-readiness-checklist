# LOCAL_DEV_LOOP

Status: `SERVICE`

## Requirement

Docs define commands to start dependencies, run server/worker, stop services, and verify health.

## Acceptance Criteria

- Start dependency services.
- Apply migrations.
- Start API.
- Start worker if needed.
- Stop dependencies.
- Health check command.

## Automatable Checks

- `README.md`, `AGENTS.md`, or `docs/development.md` contains dev server command.
- Service repos document a health check command.

## Example

```md
- Start deps: `pnpm dev:deps`
- Migrate: `pnpm db:migrate`
- Start API: `pnpm dev:api`
- Start worker: `pnpm dev:worker`
- Health: `curl -fsS http://127.0.0.1:3000/healthz`
- Stop deps: `pnpm dev:deps:down`
```
