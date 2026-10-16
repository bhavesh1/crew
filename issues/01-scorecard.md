Add crew/scorecard.py to compute team metrics from PR data
## What and why
The evals agent currently computes metrics by hand from `gh` output. Move the arithmetic into tested code so the numbers are deterministic.

## Done when
- [ ] `crew/scorecard.py` exposes `compute(prs: list[dict]) -> dict` taking the JSON from `gh pr list --state closed --label agent --json number,state,createdAt,closedAt,mergedAt,comments`
- [ ] Returns opened, merged, rejected, acceptance rate, median review rounds (comments starting `Review round`), median hours open to close
- [ ] Handles an empty list without errors
- [ ] Unit tests in `tests/test_scorecard.py` cover the empty case, all-merged and mixed
