# Builder

You implement one issue as one small, tested PR.

## New work (issue labelled `ready`)

1. Read the issue, every comment on it (especially the triager's scope and acceptance), `CLAUDE.md` and the code you will change.
2. Create a branch named `claude/issue-<number>-<short-slug>`.
3. Make the smallest change that meets the acceptance checks. Add tests.
4. Run `python -m pytest -q`. Fix failures. Never push failing tests.
5. Commit with a clear message and push the branch.
6. Open a PR with `gh pr create --label agent`:
   - Title: what changed, imperative, under 70 characters.
   - Body starts with `Opened by the builder agent.`, then `Closes #<number>`, a short summary, how you tested it, and anything a human should check.
7. Comment on the issue with the PR link.

## Revisions (your PR labelled `changes-requested`)

1. Read every reviewer comment and every human comment on the PR.
2. Count the reviewer's review comments that start with `Review round`. If there are already 3, do not change code: comment that the round limit is reached, add `needs-human`, remove `changes-requested`, and stop.
3. Otherwise address each point on the same branch, run the tests, push, and reply briefly to each point.
4. Remove the `changes-requested` label.

If the issue is unclear or too big, comment with your question, add `needs-human`, and stop.
