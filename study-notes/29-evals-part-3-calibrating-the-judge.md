# 29. Part 3 — Calibrating the Judge

## Simple Explanation (like you're 5)

If the judge itself is unreliable, the whole evaluation system is just theater.

Calibration is the work of making the judge’s scores match reality as closely as possible.

## Key Concepts Unpacked

### Anchored rubrics
Rubrics that include concrete examples of what “good,” “acceptable,” and “bad” look like. Anchors reduce subjectivity a lot.

### The bar as a decision
The pass/fail line is not a natural fact. It is a decision about how much risk you are willing to accept. Make that decision explicit.

### Grading the grader
You must periodically check the judge against human ground truth. Treat the judge as a system that itself needs evaluation.

### The 4-cell table
True Pass / False Pass / True Fail / False Fail.
The cell that usually matters most is the **false pass** — cases the judge said were fine that were actually bad.

### Fix the rubric before the judge
When scores look wrong, the first place to look is usually the rubric and the anchors, not the model behind the judge.

### The grade-the-grader protocol, step by step
The source lays out a concrete one-afternoon protocol called "grade the grader": sample twenty graded items on purpose (a real mix of FAILs and borderline cases, not easy PASSes, since agreement on all-obvious items is high by chance and hides the truth); grade them blind, before peeking at the judge's verdicts; compare and sort the disagreements into the 4-cell table; then fix the rubric before touching the model. A rough guide from the source: above 9-in-10 overall agreement, with zero false passes on high-severity items, means the judge has earned its place — any false pass on an "obvious" case means you stop trusting the number until it's fixed.

### A worked example: catching surface bias in the act
Picture a judge and a human disagreeing on 6 of 20 items, and five of those six are cases where the judge passed long, confident, well-formatted work that the human failed. That pattern has a name — surface bias, the judge grading the costume instead of the work — and per the source the first fix is never to swap the model. It's to rewrite the rubric so it asks fact-checkable questions ("does the diff remove a test?") instead of impression questions ("is this good?"), then re-run the calibration before considering a model swap.

## Why would this be on the exam?
An uncalibrated judge is worse than no judge because it creates false confidence. The exam expects you to know the calibration discipline.
