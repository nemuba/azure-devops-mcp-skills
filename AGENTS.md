# AGENTS.md

Guidance for agentic coding assistants working in this repository.

## Repository Snapshot

- Current tracked content is minimal (`README.md` only at the time of writing).
- No build, lint, or test tooling is configured yet.
- No Cursor rules found: `.cursor/rules/` and `.cursorrules` are absent.
- No Copilot instructions found: `.github/copilot-instructions.md` is absent.
- This file acts as the baseline operating contract until project scaffolding is added.

## Project Intent

- This repo is intended to host skills for OpenCode agents using Azure DevOps MCP.
- Prefer one focused skill per domain (work items, repos, pipelines, wiki, test plans, etc.).
- Optimize for correctness first, then token efficiency and predictable tool usage.

## Commands: Current State

### Verified now

- `git status`
- `git diff`
- `git log --oneline -n 20`

### Build/Lint/Test availability today

- Build: not configured.
- Lint: not configured.
- Test: not configured.
- Single test run: not available yet because no test framework exists in repo.

## Commands: Required Contract After Scaffolding

When you add tooling, expose stable root commands so agents do not guess.

### Preferred interface

- `make build` -> build all artifacts
- `make lint` -> run all linters
- `make format` -> auto-format code/docs
- `make test` -> run full test suite
- `make test-one TEST=<id>` -> run one test only

### Python mapping (if Python is introduced)

- `pytest`
- `pytest path/to/test_file.py::test_name -q`
- Optional keyword mode: `pytest -k "keyword" -q`

### Node mapping (if Node is introduced)

- `npm run build`
- `npm run lint`
- `npm test`
- `npm test -- path/to/file.test.ts -t "test name"`

### If polyglot

- Keep `make` as canonical entrypoint.
- Stack-specific commands are implementation details behind `make` targets.

## Directory and File Conventions

- Keep root clean; use explicit top-level folders.
- Suggested layout:
  - `skills/` skill implementations and templates
  - `tests/` unit/integration/regression tests
  - `examples/` usage samples and expected outputs
  - `scripts/` helper scripts
  - `docs/` architecture, design notes, and decisions
- Add a short README inside each skill directory (scope, goals, non-goals).

## Style Rules (Language-Agnostic)

- Prefer clear, direct code over clever abstractions.
- Keep units small and single-purpose.
- Avoid speculative architecture and unused indirection.
- Keep side effects explicit at module boundaries.
- Write comments only for non-obvious intent.
- Do not leave TODO/FIXME without linked issue or next action.

## Imports and Dependency Hygiene

- Group imports: standard library, third-party, local.
- Sort imports consistently (automated sorter preferred).
- Never use wildcard imports.
- Remove unused imports promptly.
- Import only what is used.
- Keep dependencies intentionally constrained/pinned.

## Formatting

- Use UTF-8 and LF.
- Prefer max line length around 100 unless formatter enforces another value.
- Enforce formatting through one canonical command (`make format`).
- Keep markdown readable in raw form (concise headings and short paragraphs).
- Avoid trailing whitespace and inconsistent indentation.

## Types and Contracts

- Add explicit types at public interfaces.
- Model MCP payloads with typed structures where possible.
- Distinguish required and optional fields explicitly.
- Avoid `any`/untyped escapes except for narrow, documented boundaries.
- Validate external tool inputs and responses before consuming.

## Naming

- Use domain-oriented names (what the concept means, not how it is stored).
- Boolean names should read like predicates (`is_`, `has_`, `can_`).
- Use singular names for single objects and plural for collections.
- Keep acronyms readable (`work_item_id`, not cryptic shorthand).
- Follow language idioms (snake_case for Python, camelCase for TS/JS).

## Error Handling

- Fail fast on invalid inputs.
- Return actionable errors with operation context.
- Never swallow exceptions silently.
- Separate user-fixable errors from system failures.
- Add retry/backoff only for known transient failure paths.
- Never leak secrets/tokens in logs, error messages, or snapshots.

## Testing Expectations

- Prefer deterministic, table-driven tests for parameterized tool behavior.
- Cover happy path, invalid input, and edge cases.
- Add regression coverage for every bug fix.
- Mark network-dependent tests explicitly as integration tests.
- For each new skill, include at least:
  - one successful flow
  - one validation failure
  - one ambiguity-resolution flow

## Agent Operating Rules in This Repo

- Read local instruction files before editing.
- Prefer specialized file tools over shell text manipulation.
- Keep context focused; gather only information needed for current task.
- Before running any command that creates, updates, or deletes files/resources, ask for explicit user confirmation.
- Treat `create`/`update`/`delete` operations as gated actions: explain what will change, then wait for user approval.
- If approval is not explicit, do not execute write/destructive commands.
- Avoid destructive actions unless explicitly requested and safe.
- Never run destructive database commands (drop/reset/purge/truncate style operations).
- Keep diffs scoped to the requested objective.

## Commit and PR Guidance

- Keep commits small and coherent.
- Explain why in commit messages, not just what changed.
- Include validation commands in PR descriptions.
- Link related work items/issues when available.
- Call out deliberate follow-up work.

## Skill Authoring Guidance (Project-Specific)

- Build skills around concrete operator jobs (view/create/update/link/search/triage).
- Prefer concise decision trees and playbooks over long narrative text.
- Include copy-pasteable examples for common operations.
- Document required parameters, optional parameters, and frequent pitfalls.
- Add a "when not to use this skill" section.
- Include token-saving guidance (batch retrieval, field filtering, targeted queries).

## Rule File Integration Policy

If Cursor/Copilot rule files are added later:

- Merge their actionable constraints into this file.
- Document precedence where rules conflict.
- Keep this file as the quick-start source for agent behavior.

## Definition of Done for Future Changes

- Build/lint/test commands exist and are documented here.
- Single-test command is documented with a real repo example.
- New behavior ships with tests.
- Lint/format/tests pass locally.
- Docs describe actual behavior, not planned behavior.

