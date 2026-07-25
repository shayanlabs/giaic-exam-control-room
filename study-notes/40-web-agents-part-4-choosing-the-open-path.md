# 40. Part 4 — Choosing + the Open Path

## Simple Explanation (like you're 5)

You choose a web home based on what the work touches (especially data sensitivity and compliance).

There is also an open path that does not depend on any single vendor’s cloud.

## Key Concepts Unpacked

### Pick a home by what the work touches
If the work involves regulated data, internal credentials, or high-stakes actions, the compliance and control requirements dominate the choice.

### Regulated data needs compliance in writing first
Do not put regulated data into a vendor surface until you have written confirmation of the compliance posture. Verbal assurances are not enough.

### A vendor sells you a spine
Most commercial web-agent products give you a convenient, pre-built spine and harness. That is valuable, but it is also a form of lock-in.

### The open path makes you build one
The open path requires more work up front (you build the spine and harness yourself) but keeps ownership and the ability to switch.

### What the open path actually looks like
Two real doors exist without a vendor cloud. **OpenWork** is the open-source desktop co-worker that can connect to a worker running somewhere other than your laptop — a self-hosted worker you reach by URL and access token, or your organization's shared cloud workers. The machine doing the work still isn't the machine you're looking at, but now it runs on infrastructure you or your org control. **OpenCode**, for repo-attached work, answers the scheduling question with a scheduler you own: cron on a machine you run, or a scheduled GitHub Actions job — no vendor cloud, no plan tiers, no staged rollout.

### The honest trade, stated plainly
In exchange for the extra setup work, the open path buys you two things no vendor sells: **custody** (your data on machines you control) and **choice** (which model sees your prompts, and the freedom to switch). Neither side of the trade is automatically the right one — a solo consultant shipping briefs by Friday may want the working spine a vendor hands over on day one, while an NGO whose data policy forbids donor records on third-party consumer platforms has no choice but the open path, even with no engineer on staff. In that case the honest sentence to say out loud is: this path trades a subscription fee for an operator — someone has to own the setup, the updates, and the morning it breaks. Custody is not free; it is paid for in operations.

## Why would this be on the exam?
The course prefers the vendor-neutral, ownership-preserving path when the work justifies the extra effort. The exam expects you to know when each choice is appropriate.
