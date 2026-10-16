# crew

**A team of AI agents that ships software in public. Agents propose; a human merges.**

crew runs five Claude-powered agents on GitHub Actions. They triage issues, write code, review each other, write release notes, and score their own work. I hold the only merge key. Every outcome, merged or rejected, is logged in public.

## How work flows

```
new issue ──► triager ──► (I add `ready`) ──► builder ──► PR ──► reviewer
                                                 ▲                 │
                                                 └─ changes-requested
                                                                   │ looks good
                                                                   ▼
                     decision log ◄──── I merge or reject (with a reason)
                          │
                          ▼
                   evals (weekly scorecard)        release & docs (weekly changelog PR)
```

| Role | Triggered by | Can touch | Cannot touch |
| --- | --- | --- | --- |
| Triager | New issue | Labels, issue comments | Code |
| Builder | `ready` label on an issue, `changes-requested` on its PR | A `claude/` branch and its PR | `main`, workflows, secrets |
| Reviewer | Agent PR opened or updated | PR comments, labels, test runs | Approving, merging |
| Release & docs | Weekly, or on demand | `CHANGELOG.md`, `README.md` via PR | Source code |
| Evals | Weekly, or on demand | `docs/scorecard.md`, `docs/decision-log.md` via PR | Everything else |

Each role's instructions live in [`prompts/`](prompts/). Shared rules for every agent live in [`CLAUDE.md`](CLAUDE.md).

## Guardrails

1. **Only a human merges.** Branch protection on `main` requires a PR and one approving review. No agent can approve.
2. **Agents are credited.** Every agent PR carries the `agent` label and says so in its description.
3. **Bounded loops.** The builder gets at most three review rounds per PR, then hands off with `needs-human`.
4. **Least privilege.** Each workflow lists exactly which tools its agent may use.
5. **Misses are published.** Rejected PRs and the reason go into the decision log, and they count in the scorecard.

## Results

See the [scorecard](docs/scorecard.md) for acceptance rate, review rounds and time to merge, updated weekly.

## Use it on your own repo

1. Copy `.github/workflows/`, `prompts/` and `CLAUDE.md`.
2. Install the [Claude GitHub app](https://github.com/apps/claude) on the repo.
3. Add a `CLAUDE_CODE_OAUTH_TOKEN` (from `claude setup-token`) or `ANTHROPIC_API_KEY` secret.
4. Create the labels listed in `setup.sh` and protect `main`.

## License

MIT
