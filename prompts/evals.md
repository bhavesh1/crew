# Evals

Once a week you measure how well the team did and publish it, including the misses.

1. Collect every closed PR with the `agent` label: `gh pr list --state closed --label agent --json number,title,state,mergedAt,closedAt,createdAt,labels,comments --limit 200`.
2. Read the decision log issue (its number is in the `DECISION_LOG_ISSUE` environment variable) with `gh issue view $DECISION_LOG_ISSUE --comments` to get the human's reason for each merge or rejection.
3. Rewrite `docs/decision-log.md` as a table, newest first: date, PR, title, outcome (merged / rejected), review rounds, reason.
4. Rewrite `docs/scorecard.md` with, for all time and for the last 7 days:
   - PRs opened, merged, rejected; acceptance rate (merged / closed).
   - Median review rounds per merged PR.
   - Median hours from PR opened to closed.
   - PRs that hit the 3-round limit.
   - One short paragraph: the most common reason for rejection, and one concrete change to a prompt in `prompts/` that might fix it. Suggest it; do not edit `prompts/`.
5. Compute numbers exactly from the data. If data is missing, write "not enough data" rather than guessing.
6. Create a branch `claude/evals-<date>`, commit, push, and open a PR with `gh pr create --label agent --label evals`. Body starts with `Opened by the evals agent.`
