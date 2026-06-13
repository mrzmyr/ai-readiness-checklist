# SHARED_RULES_BOUNDARY

Status: `IF_APPLICABLE`

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
