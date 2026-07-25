# 16. Part 5 — A Complete Loop, Twice

## Simple Explanation (like you're 5)

Reading about loops is useful. Seeing one complete loop built for real, in two different tools, is better.

This part walks through a concrete morning example — the 9am triage loop — from start to finish in both Claude Code and OpenCode. You can point to each of the six parts in real files and real commands.

## Key Concepts Unpacked

### The 9am triage loop
A practical morning routine: look at what changed overnight, decide what matters, create or update tickets or pull requests, and leave a clear status for the human. It is small enough to understand completely and realistic enough to be useful.

### The 6-step pseudocode
A clean, tool-independent description of the loop. It makes the six parts visible without the noise of specific commands.

### Where each of the 6 loop parts sits in a real example
You can see the heartbeat, the body pieces, the checker, the spine updates, and the human gate inside actual working code and files.

### A worked example: one real morning
Picture the 9am triage loop actually firing. It reads `progress.md` and sees one item still "in progress." It finds two overnight CI failures and one new npm-audit advisory. For the first CI failure, it drafts a fix on branch `claude/fix-auth-retry`; the reviewer replies PASS (tests green, no API change), so it opens PR #142. Same for the second failure — PASS, PR #143. But the audit fix would change the library's output format, so the reviewer replies FAIL ("public behaviour change"); the loop writes that item to "Open / needs a human" in `progress.md` and opens no PR. At 9:30 you wake up to two PRs to review and one flagged decision — you typed nothing. That's the maker–checker split and the human gate working together in one concrete run.

### The shared skill file
The whole loop's logic lives in one `SKILL.md` file (`daily-triage`) so the scheduled prompt itself can stay a single line ("run the daily-triage skill"). Inside, the skill spells out five ordered steps: read the progress file first, gather at most 5 candidates (CI failures, then labeled issues, then audit advisories), work each one in an isolated checkout with a strict "one fix per PR" rule, decide from the reviewer's verdict (PASS and low-risk opens a PR; FAIL or risky goes to "needs a human"), and update the progress file last. The rule "never open more than 5 pull requests in one run" and "never change `main` directly" are written right into the skill — proof that a loop's safety rules live in files the loop reads, not just in your head.

## Why would this be on the exam?
Recognizing the shape of a complete loop in real tools is more important than memorizing any single command. The exam will expect you to map the concepts onto concrete examples.
