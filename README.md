# Cloud Cost Anomaly Lab

CLI for detecting unusual cloud-service daily spend using trailing historical baselines.

## Quick start

Requires Python 3.10+; standard library only. Run from this repository's root.

```bash
python -m app.cli examples/costs.csv --window 3 --threshold 1.6
```

## Tests

```bash
python -m unittest discover -s tests -v
```

## Architecture

- `app/`: CLI and core analysis logic.
- `examples/`: safe, synthetic example inputs.
- `tests/`: repeatable unit tests.
- `.github/workflows/tests.yml`: CI tests on push and pull requests.

## Engineering decisions

- Read-only analysis: the tool does not modify its input files.
- Machine-readable JSON output facilitates automation and regression testing.
- No third-party dependencies; quick to run and review.

## Current scope and limitations

For each service, the baseline is the mean of the previous N recorded observations (not necessarily consecutive calendar days). A minimum historical baseline is required. This is a simple heuristic, not a billing or production forecasting system.

## Good Claude Code evaluation tasks

1. Ask Claude Code to inspect the implementation and report specific risks without making changes.
2. Add one regression test for a realistic edge case, then request a minimal fix.
3. Review its diff, run the test suite, check failure behavior, and document what you accepted or rejected.

## Attribution

This repository was initially created with AI assistance. Describe subsequent changes and test results accurately when presenting it as a portfolio project.

## License

MIT. See [LICENSE](LICENSE).
