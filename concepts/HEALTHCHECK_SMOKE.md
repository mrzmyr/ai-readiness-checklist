# HEALTHCHECK_SMOKE

Status: `SERVICE`

## Requirement

Deployed or local services expose health/readiness smoke commands suitable for CI or handoff proof.

## Acceptance Criteria

- Local health command exists.
- Deployed health command exists if service deploys.
- Critical route smoke is documented.

## Automatable Checks

- Docs contain `health`, `healthz`, `ready`, or smoke command.
- CI or release docs run at least one smoke command for deployed services.

## Example

```md
- Local: `curl -fsS http://127.0.0.1:3000/healthz`
- Staging: `curl -fsS https://staging.example.com/healthz`
- Webhook smoke: `pnpm smoke:webhook -- --base-url http://127.0.0.1:3000`
```
