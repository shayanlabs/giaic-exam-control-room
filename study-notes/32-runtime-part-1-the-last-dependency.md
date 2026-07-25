# 32. Part 1 — The Last Dependency

## Simple Explanation (like you're 5)

As long as the loop only runs on your laptop while you are watching, it is still a personal tool.

The moment it needs to run without you, you face the last dependency: where does the work actually happen, and who is in charge of starting it?

## Key Concepts Unpacked

### The 4 homes
The main places a loop can live (your laptop, a cloud schedule, a managed agent service, the customer’s own computers, etc.). Each home has different trade-offs for control, cost, reliability, and rules.

### Control plane vs execution plane
- **Control plane**: decides *what* should run, when, and with what permissions.
- **Execution plane**: the place where the agent process, the tools, and the side-effects actually happen.

The key question is always: who operates the loop, and where does the work actually execute?

### The last single point of failure
The source frames this as the final step in a series: earlier work removed the single unreviewed opinion (the maker–checker split), the single unguarded action (the harness), and the single unchecked checker (evals and baselines). What's left is not your judgment — the human gate rightly stays — it's your *hardware*: your laptop being open, your session logged in, your machine awake and on power and on network. The moment the system is more reliable than the machine it runs on, per the source, is the signal it has outgrown its home.

### The four homes, concretely
The source lays these out as a real table, not just a list: **Home 1 (your session)** — you own the config, runtime, and uptime, right for building but wrong for depending on. **Home 2 (cloud schedule)** — you keep the same rules file and skills, only the clock moves to someone else's computer (a Routine in Claude Code, a scheduled GitHub Actions job). **Home 3 (managed runtime)** — you hand over the agent's definition and a vendor operates the control plane, while the execution plane (the sandbox) can be theirs or, where custody demands it, your own. **Home 4 (your own process)** — the harness becomes a library inside software you write and run yourself, which is the Agent SDK's territory. The source is clear these are four options to choose between per loop, not a ladder everyone must climb.

## Why would this be on the exam?
Leaving the laptop is the moment a personal experiment becomes a real system. The exam expects you to understand the separation of control and execution.
