# 30. Part 4 — Evals in the Loop

## Simple Explanation (like you're 5)

Evals only help if they are part of the living development process, not a one-time report that sits on a shelf.

This part is about keeping the evaluation system itself healthy as the product and the golden set change.

## Key Concepts Unpacked

### Regression suite
The golden set (or a large part of it) run automatically on every important change so regressions are caught early.

### Drift and baselines
Models, prompts, and tools change. Scores drift. You need baselines and a clear process for deciding when a change in scores is a real improvement or just drift.

### Re-baseline when the set changes
If you add or remove cases, the old numbers are no longer comparable. Re-baseline on purpose.

### Smoke / full / hold-out tiers
- **Smoke**: a tiny, fast set that runs all the time.
- **Full**: the complete golden set.
- **Hold-out**: cases the development process is not allowed to see, used for final honesty checks.

### Read WHICH before HOW MANY
A drop from 92% to 87% is less useful than knowing *which* cases flipped and why. Always look at the failures first.

### A baseline is more than one number
The source shows a concrete `baseline.json` shape: a `recorded` date, the `reviewer_model`, the `rubric_version`, an `overall` rate, a `by_category` breakdown, and who `approved_by` any drop. The reasoning matters — a rate with no record of what produced it is a number you cannot interpret later, and the rule is that a baseline may only move *down* with an explicit written approval in the same commit, so improving your own suite is never accidentally punished.

### What three runs can and can't tell you
The source is careful about this: three runs per case is a cheap development setting, a smoke signal, not a stable estimate — a 3-of-3 does not mean the true pass rate is near 100%, it means three sampled attempts happened to pass. The fix is to scale the sample to the decision: three runs while iterating, more runs (until the result stops moving) for a release decision, and larger samples plus human review for the highest-risk categories. That is also why the note's "read WHICH before HOW MANY" rule exists — a drop from 92% to 87% means nothing until you know whether the newly-failing cases are tone quibbles or a `deleted-test-001`-style false green.

## Why would this be on the exam?
Evals that are not integrated into the loop quickly become stale and misleading. The exam expects you to know how to keep them alive and trustworthy.
