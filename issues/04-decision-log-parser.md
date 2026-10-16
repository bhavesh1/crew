Parse decision log issue comments into structured records
## What and why
The decision-log workflow posts one comment per closed agent PR. The evals agent needs them as data.

## Done when
- [ ] `crew/decisionlog.py` exposes `parse(comment_body: str) -> dict | None` returning pr number, title, outcome, review rounds, reason
- [ ] Returns `None` for comments that don't match the format
- [ ] Tests use real examples of the format written by `.github/workflows/decision-log.yml`
