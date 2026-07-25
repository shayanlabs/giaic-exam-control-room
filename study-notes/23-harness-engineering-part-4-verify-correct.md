# 23. Part 4 — Verify & Correct

## Simple Explanation (like you're 5)

Limiting the agent and giving it information is not enough. You also need to check that the work is actually correct and to have a plan when it is not.

This is the “Verify & Correct” job of the harness.

## Key Concepts Unpacked

### Hooks
Special moments in the agent’s life where you can run your own code: before a tool is used, after a tool is used, when the agent wants to stop, etc.

### Typed output
Forcing the agent to produce structured answers (not free-form text) so a computer can check them reliably.

### Recovery
What happens after a failure. Good harnesses have deliberate recovery paths instead of just stopping or blindly trying again.

### The ratchet
A pattern that only allows the measured quality of the system to stay the same or get better — never silently get worse.

### Four failure classes
A useful way to group problems:
- Context failure (the agent did not know something it needed)
- Constraint failure (the agent did something it should not have been able to do)
- Verification failure (the check itself was wrong or missing)
- Planning failure (the high-level plan was bad)

### PreToolUse / Stop gate (exit code 2)
A hard-stop mechanism. Returning a special exit code can block a tool call or stop the agent completely.

### PostToolUse feeds back
After a tool runs, the result (or a summary) is given back so both the agent and the harness can decide what to do next.

### Typed output: a verdict you can actually parse
A checker that replies "PASS" or "FAIL" in free text breaks the night it replies "This mostly passes, though I have some doubts about..." — the loop either misreads it or stalls. The fix: demand a fixed JSON shape and validate every field with code before trusting it, for example `{"verdict": "PASS", "reasons": [], "risk": "low"}`, checked against its *allowed values* with a tool like `jq` — not just checked for presence. A lazy validator that only confirms `.verdict` exists would happily accept `{"verdict": "MAYBE"}`; a real validator rejects it even though the JSON is perfectly well-formed, because `MAYBE` isn't `PASS` or `FAIL`. When the verdict can't be validated, the loop doesn't retry forever or guess — it **escalates**, writing "reviewer output unparseable: needs a human" and moving on. This is the checker ladder from loop engineering, with its weakest rung reinforced: "a rubric with a bar" becomes "a rubric with a bar, in a shape a program can read."

### The ratchet: four failure classes, four homes
The core correction discipline: when the agent makes a mistake, don't just fix the work — change the harness so that mistake becomes impossible, then never think about it again. Every failure fits one of four classes, each with its own fix surface: a **context failure** ("it didn't know") gets fixed in the rules file, a skill, or a tool description; a **constraint failure** ("it did something it should never have been able to do") gets fixed with a permission rule, sandbox, or branch fence; a **verification failure** ("bad work got called done") gets fixed with a hook, required CI check, or typed output; and a **planning failure** ("right pieces, wrong order") gets fixed one level up, in the loop's structure — smaller tasks, subagent splits, step caps. The practice is a five-minute review after every failure: name the class, write the fix into that class's own surface. Two failures with the same shape should be impossible — if you see a repeat, you classified the first one wrong.

## Why would this be on the exam?
Verification is what turns “it looked good” into “we know it is good.” Without it you cannot trust the output of any non-trivial loop.
