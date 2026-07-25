# 33. Part 2 — Headless Is the Bridge

## Simple Explanation (like you're 5)

“Headless” means the loop can run without a human watching the screen.

Cloud scheduling is the practical bridge between “runs while I watch” and “runs while I sleep.”

## Key Concepts Unpacked

### Home 2 (cloud schedule)
One of the four homes: the loop is started by a cloud clock and runs in an environment that does not need your laptop to be open.

### The minimum unattended kit
Six controls you should have before you trust a loop to run without you:
1. **Idempotency** — running twice does not create double effects.
2. **Missed-run detection** — you know when a scheduled run failed to start.
3. **Concurrency lock** — two runs cannot step on each other.
4. **Credentials** — secrets are available safely.
5. **Time limits** — the run cannot go forever.
6. **Cost limits** — the run cannot spend unlimited money.

### Headless is something you already built
The source points out you crossed this bridge earlier without being told: the eval runner's `claude -p` and `opencode run` calls are the agent running as a command, not a conversation — no open window, just a prompt in, work happens, output comes out. That's the whole idea Home 2 depends on: anything that can run a command (a shell script, a cron job, a CI runner, a cloud scheduler) can now run your agent. One rule the source adds for this mode: headless runs must fail loudly, because an exit code nobody checks is a beat that silently didn't happen.

### A worked example: Ayesha's invoicing loop
The source uses a concrete case to show why Home 2 is usually enough before reaching for Home 3: Ayesha in Lahore runs a freelance-invoicing loop, and load-shedding cuts her power most evenings just as a client starts expecting daily 6pm invoices. Her problem is exactly and only the clock — the loop already works — so moving the schedule to a cloud runner (Home 2) solves it. The source is honest that even schedulers only promise *around* a time, not *at* it, which is exactly why the minimum unattended kit (missed-run detection, safe retries, an alarm if nothing ran by 6:30) is what actually delivers "without fail," not the scheduler alone.

## Why would this be on the exam?
Headless is the practical bridge most students will cross first. The six controls are the minimum safety net.
