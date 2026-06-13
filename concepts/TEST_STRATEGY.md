# TEST_STRATEGY

Status: `REQUIRED`

## Requirement

`docs/testing.md` or `AGENTS.md` defines test types, fixture locations, naming pattern, and live-test gates.

## Acceptance Criteria

- Test folders are named.
- Fixtures are named.
- Live tests are env-gated.
- Test naming pattern is stated.
- Regression-test expectation is stated.

## Automatable Checks

- `tests/` or equivalent exists.
- `AGENTS.md` or `docs/testing.md` mentions fixtures or test folder.
- Live test env vars are documented if `tests/live` exists.

## Example

```md
- `tests/integration/**`: HTTP routes with test server.
- `tests/services/**`: service tests with mocked clients.
- `tests/db/**`: repository tests with test database.
- `tests/live/**`: skipped unless `PROVIDER_LIVE_TEST=1`.
```
