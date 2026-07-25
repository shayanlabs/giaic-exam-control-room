# 28. Part 2 — The Golden Set

## Simple Explanation (like you're 5)

A golden set is a carefully chosen collection of real cases (especially failures you have already caught) that you run the system against again and again.

It is the closest thing you have to a regression suite for agent behavior.

## Key Concepts Unpacked

### Every caught failure becomes a case
The most valuable cases are the ones that previously broke or embarrassed the system. Turning them into permanent test cases prevents the same failure from coming back unnoticed.

### The case shape and the runner
Each case has a clear structure (input, context, expected properties or rubric) and a runner that executes the agent and scores the result.

### Origin line
Recording where each case came from (which real incident or which synthetic construction) helps you understand what the set actually covers.

### Failures come first
Prioritize real failures over easy synthetic cases. The set should be hard enough to be useful.

### 20–40 cases across difficulty
A practical size: large enough to catch regressions, small enough to run and maintain.

### Errors are not the same as fails
- **Error**: the system crashed or could not finish.
- **Fail**: the system finished but the result was wrong or not good enough.
Both matter, but they are different signals.

### A worked example: what a case actually looks like
A real case is a small JSON file, not an abstract idea. One from the source: `deleted-test-001`, category `false_green`, telling the judge to read the `diff`, with `expected: {verdict: "FAIL", risk: "high"}`, a `must_mention` list, and an `origin` line pointing back at the real incident ("bad night, 2026-06-30"). That `origin` field matters — it is what lets you tell a case that is proven to be reachable (a real caught failure) apart from an invented one that just tests what someone imagined.

### The runner is a loop, not a framework
The source is explicit that you do not need special eval software: the runner is a shell loop that runs each case a few times (three is a common starting point), asks the agent to write its verdict to a file, and uses a tool like `jq` to compare that file against what was expected. One detail worth remembering: errors and fails are counted separately, because "the judge broke protocol and gave no answer" and "the judge answered but was wrong" are different problems with different fixes.

## Why would this be on the exam?
Without a golden set you have no reliable way to know whether the system is getting better or worse. The exam expects you to understand how to build and maintain one.
