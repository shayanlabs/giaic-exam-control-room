# 15. Part 4 — The Spine

## Simple Explanation (like you're 5)

The spine is the memory that connects one run of the loop to the next run.

Without a spine the loop has amnesia. Every morning it wakes up and has to re-learn everything it already knew yesterday. That wastes time and money and causes repeated mistakes.

## Key Concepts Unpacked

### No spine, no loop
This is the blunt rule. If state does not survive between runs, you do not have a real loop. You have a series of separate prompts.

### `progress.md` lives in the repo
A simple and practical pattern: a Markdown file inside the project that records what has already been done, what is left, and any important decisions. Later runs read it and update it.

### The spine is also a cost lever
Good memory means the agent spends fewer tokens re-reading history or re-discovering the same facts. Missing or messy memory is one of the fastest ways to burn money.

### Memory between runs and the dreaming pass
Some designs include a quiet “dreaming” or cleanup pass that summarizes, organizes, or forgets low-value details so the spine stays useful as the project grows.

### The intern's diary
Picture training a new intern: you hand them a diary with two standing instructions. First, every time they get feedback, they write the lesson in the *front* of the diary and re-read it each morning — "don't use that pattern," "this team squashes commits." Second, before they go home, they write in the *back* what they finished and where they stopped, so tomorrow starts where today ended. The front of the diary is your **rules file** (`CLAUDE.md`/`AGENTS.md`): durable lessons, read every run. The back is your **progress file**: checkpoints, updated every run. An intern without the diary re-learns the same corrections and redoes yesterday's work forever — and so does a loop, because the model's memory is wiped clean between runs while the intern's at least fades slowly.

### Dreaming: the improvement loop as a product
Writing a lesson into the rules file so every future run behaves better has a name: a **hill-climbing loop**, sometimes called "dreaming" — a separate loop, with its own heartbeat (typically weekly, not daily), that reads a batch of run transcripts, looks for mistakes that repeat across sessions, and proposes changes to the memory store, always as a PR with cited evidence, never a direct edit. Claude Code's research-preview **Auto Dream** feature does a lighter version automatically: it merges duplicate notes and deletes ones newer work has proven wrong, but it can only touch memory files, never code. Two real risks make the human gate non-negotiable here: **memory poisoning** (an instruction planted in one run's input gets written into memory and steers every later run) and **brevity bias/context collapse** (a detailed playbook gets rewritten down to a vague paragraph over repeated summarizing passes). This is why no public model changes its own weights from your sessions — what improves is everything *around* it, and only a human merging the PR makes that improvement permanent.

## Why would this be on the exam?
Forgetting state between runs is the most common way real loops fail in practice. The exam treats the spine as a first-class part of the design, not an afterthought.
