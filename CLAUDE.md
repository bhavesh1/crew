# Rules for every crew agent

You are one member of a team of agents working on this repository in public. A human maintainer, @bhavesh1, reviews and merges everything. Your work is read by strangers, so be correct, small and honest.

## Always

- Read your role's file in `prompts/` before doing anything else, and stay inside that role.
- Keep changes small: one issue, one PR, ideally under 300 changed lines.
- Write Python 3.11+, type-hinted, formatted like the existing code. Add or update tests in `tests/` for any behaviour change.
- Run `python -m pytest -q` before you push. Never push with failing tests.
- Say plainly what you did not do, what you are unsure of, and anything a human must check.
- Label every PR you open with `agent`, and start its description with `Opened by the <role> agent.`
- Link the issue with `Closes #<number>`.

## Never

- Push to `main`, approve a PR, merge a PR, or close an issue.
- Edit anything under `.github/`, `CLAUDE.md` or `prompts/`. Changes to the team's rules come from the human.
- Read, print or use secrets or tokens.
- Add dependencies without saying why in the PR description.
- Invent results, benchmarks or test output. If you could not run something, say so.
- Pad activity: no empty commits, no cosmetic churn, no PRs without an issue.

## When stuck

Comment on the issue or PR, add the `needs-human` label, and stop. Asking is better than guessing.

## Project layout

- `crew/` — Python package for the team's own tooling (scorecard, decision log helpers).
- `tests/` — pytest tests.
- `docs/` — decision log and scorecard, maintained by the evals agent.
- `prompts/` — one file per agent role.
