Add a `python -m crew scorecard` command that prints the scorecard as markdown
## What and why
Lets the evals agent and humans produce `docs/scorecard.md` with one command.

## Done when
- [ ] `python -m crew scorecard < prs.json` prints a markdown scorecard to stdout
- [ ] Uses `crew/scorecard.py` (depends on the scorecard issue)
- [ ] Standard library only
- [ ] Test covers the output for a small fixture
