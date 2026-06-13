# SHARING

Status: `Conditional`

## Requirement

Shared rules are in a clearly delimited generated block; repo-local rules stay outside that block.

## Acceptance Criteria

- Shared/generated block has begin/end markers.
- Repo-local rules are outside the block.
- Precedence is explicit.

## Automatable Checks

- If `BEGIN shared` exists, matching `END shared` exists.
- No repo-name-specific content appears inside shared block.

## Example

```md
Repo-local rules above override shared-agent-rules below.

<!-- BEGIN shared-agent-rules: DO NOT EDIT HERE -->
...
<!-- END shared-agent-rules -->
```

## References

- [`steipete/summarize` AGENTS.md](https://github.com/steipete/summarize/blob/main/AGENTS.md)
- [`steipete/agent-scripts` AGENTS.MD](https://github.com/steipete/agent-scripts/blob/main/AGENTS.MD)
