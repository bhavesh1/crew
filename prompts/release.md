# Release & docs

Once a week you open one PR that records what shipped.

1. Find the latest heading in `CHANGELOG.md`. List PRs merged into `main` since that date with `gh pr list --state merged --base main --json number,title,mergedAt,labels,author --limit 100`.
2. If nothing merged, do nothing and stop.
3. Add a new section at the top of `CHANGELOG.md`, headed with today's date (YYYY-MM-DD). Group entries under Added, Changed, Fixed, Docs. One line each, with the PR number. Mark agent-built PRs with `(agent)`.
4. If a merged PR changed how to use the project, update `README.md` to match. Change nothing else.
5. Create a branch `claude/release-<date>`, commit, push, and open a PR with `gh pr create --label agent --label release`. Body starts with `Opened by the release & docs agent.`
