# AGENTS

Status: `General`

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

## References

- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/RepoBar` AGENTS.md](https://github.com/steipete/RepoBar/blob/main/AGENTS.md)
- [`steipete/Trimmy` AGENTS.md](https://github.com/steipete/Trimmy/blob/main/AGENTS.md)
- [`steipete/oracle` AGENTS.md](https://github.com/steipete/oracle/blob/main/AGENTS.md)
