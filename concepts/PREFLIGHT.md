# PREFLIGHT

Status: `Conditional`

## Requirement

Paid or external AI/provider calls have dry-run/preflight/doctor commands and redacted diagnostics.

## Acceptance Criteria

- Paid/provider calls have dry-run or doctor command.
- Route/config diagnostics are redacted.
- File/context report exists for model calls.
- Session or output path is recorded.

## Automatable Checks

- AI/provider tooling docs mention `dry-run`, `preflight`, `doctor`, or equivalent.
- Live provider tests are opt-in.

## Example

```md
- Preview: `oracle --dry-run summary --files-report -p "<task>" --file "src/**/*.ts"`
- Redacted readiness: `oracle doctor --providers`
- Route only: `oracle --route --model gpt-5.5-pro`
```

## References

- [`steipete/oracle` README](https://github.com/steipete/oracle/blob/main/README.md)
- [`steipete/oracle` coding-agent docs](https://github.com/steipete/oracle/blob/main/docs/agents.md)
- [`steipete/oracle` OpenAI endpoint docs](https://github.com/steipete/oracle/blob/main/docs/openai-endpoints.md)
