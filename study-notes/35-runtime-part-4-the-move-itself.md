# 35. Part 4 — The Move Itself

## Simple Explanation (like you're 5)

Moving a working loop from one home to another is harder than it looks.

The good ideas and the discipline travel with you. The concrete mechanics usually have to be rebuilt. Trust is earned again in the new place; it is not automatically transferred.

## Key Concepts Unpacked

### The suitcase test
What actually has to come with you when you move: the specifications, the skills, the evaluation suite, the spine format, the success criteria. Everything else is luggage that may need to be replaced.

### Trust is re-earned, not transferred
Just because the loop was safe on your laptop does not mean it is safe in the new runtime. You must re-validate.

### Discipline travels but mechanics get rebuilt
The maker–checker idea, the spine concept, and the stop conditions travel. The exact hooks, file paths, and credential injection usually have to be re-implemented.

### The arrival protocol
A deliberate sequence for arriving in a new home:
- Full rule set, organized by category.
- Hold the quality bars (do not lower standards “just for the move”).
- Probation period with extra monitoring before full trust.

### What travels vs. what gets rebuilt, concretely
The source's packing list for what goes in the suitcase: the spec (what the job is and what "done" means), the rubric with its anchors, the golden set with every case's `origin` line and its baselines, the ratchet log of caught failures, the maker–checker split, and the human gate. What stays behind: CLI flags and output formats, file paths, session state, code written against one runtime's API, and cost assumptions from the old home. The source's one-sentence rule for staying movable: the repo holds the truth, and every home is configured from it — every rule that only lives in a vendor-side setting is weight quietly leaving the suitcase.

### A worked example: a "regression" that was really a suitcase bug
The source walks through a case where a move to Home 2 drops the score from 35/36 to 33/36: one case flaked (passed on re-run, so it's noise), but the other miss reproduces every time and turns out to be a fixture reading a file by an absolute path left over from the old laptop. That's not a real regression of the agent — it's a suitcase error, mechanics that traveled by accident — so the fix is to repair the fixture (make the path relative) and re-baseline in the same commit, exactly as the evals course's own rule requires when the *set* itself changes.

## Why would this be on the exam?
Many systems quietly break during a move. The exam expects you to know that the move itself is a first-class engineering problem.
