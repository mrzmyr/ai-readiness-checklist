# AGENT_ENTRYPOINT

Status: `REQUIRED`

## Requirement

Root `AGENTS.md` defines exact agent operating rules, repo map, commands, verification, and safety caveats.

## Acceptance Criteria

- Project purpose in one sentence.
- Repo map with real paths.
- Runtime/package manager.
- Exact commands.
- Verification matrix.
- Security/live-system rules.
- Generated-file rules if applicable.

## Automatable Checks

- `AGENTS.md` exists at repo root.
- Contains `Commands`.
- Contains `Verification` or `Verification Matrix`.
- Contains `Security` or `Secrets`.

## Example

```md
## Commands

- Install: `pnpm install --frozen-lockfile`
- Green gate: `pnpm check`
- Focused webhook test: `pnpm vitest run tests/integration/webhooks.test.ts`
```
