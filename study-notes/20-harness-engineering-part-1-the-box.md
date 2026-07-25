# 20. Part 1 — The Box

## Simple Explanation (like you're 5)

An agent is not just a smart brain.
An agent = the smart brain **plus** the box that surrounds it.

The box is called the **harness**. It is the set of rules, tools, information, and safety checks that make the brain reliable enough to do real work.

Without a harness you have a clever autocomplete.
With a good harness you have a Digital FTE you can trust.

## Key Concepts Unpacked

### 4 necessary parts
A minimum harness needs ways to:
- Limit what the agent can do
- Give it the right information
- Check that the work is good
- Recover when something goes wrong

### Inner vs outer harness
- **Inner harness**: lives close to the model (rules files, skills, tool descriptions).
- **Outer harness**: lives further out (sandboxes, network limits, human approval steps, outside checkers).

### The five verbs
The main jobs a harness does. In this course they are usually understood as:
1. Constrain (limit what is allowed)
2. Inform (give the right context)
3. Verify (check the result)
4. Correct (fix or recover)
5. Observe / Escalate (watch what happens and call a human when needed)

### Compounding reliability (95%^20 ≈ 36%)
If each single step is 95% reliable, a chain of 20 steps is only about 36% reliable. That is why safety cannot live only in the prompt. It must be built into the structure of the harness.

### Guardrails live in the harness, never only in the prompt
A prompt can be ignored or overridden. Structural controls in the harness cannot.

### The four-part definition, tested on a real tool
A 2026 paper made the definition exact: a harness needs **an agent loop** (the small loop that keeps the model working), **a tool interface** (the actions the model can take, and the shape of each one), **context management** (what goes in the window, what gets compacted, what gets pushed to files), and **control mechanisms** (permissions, limits, checks — the parts that say no). Test it on Claude Code: it has the loop, a tool set (Read, Edit, Bash, MCP servers), context management (compaction, subagent isolation, the rules file), and control (permission rules, hooks, sandboxing). All four present — so is OpenCode, so is Aider. The shift this course asks for: stop treating these as a menu of conveniences to browse, and start treating them as one system engineered to make the same model produce the same quality on a bad day as on a good one.

### Why the harness became the bottleneck
Here's the arithmetic behind it: if each step in an agent's work succeeds 95% of the time, a chain of 20 steps finishes cleanly only about 36% of the time (0.95 multiplied by itself 20 times) — a system whose steps are individually reliable still fails nearly two-thirds of its 20-step tasks. A better model only nudges that 95% a little higher. The harness attacks the *chain* itself: verification catches a bad step early, recovery resumes instead of restarting, and constraint shrinks what a bad step can cost. This is why, as top models from rival labs score closer to each other on many coding tasks, harness-only changes — no model swap at all — have produced up to 10x gains on coding benchmarks in real surveys. When changing the box beats changing the engine, the box is where the engineering lives.

## Why would this be on the exam?
Understanding that an agent is Model + Harness (not just Model) is the foundation of the whole harness module.
