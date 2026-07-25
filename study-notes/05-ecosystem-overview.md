# 5. Ecosystem overview

## Simple Explanation (like you're 5)

Imagine one master cookbook that everyone trusts.

From that single cookbook you open three different doors:
- One door for people who want to learn
- One door for people who want to build
- One door for people who want to write new books from the same recipes

Behind the doors sit four boxes of tools that everyone shares. Everything is saved in two places: a Git folder (the master text) and one database (so computers can search it fast).

Because each person brings their own AI brain, the people who run the system almost never pay for AI. That is why the cost stays near zero.

## Key Concepts Unpacked

### One source, three gateways
- **Source**: the book itself, turned into a trusted System of Record.
- **Three gateways** (the doors):
  1. Learners open Claude (or similar) and meet Zia Tutor AI.
  2. Builders open Claude Code or OpenCode and meet Zia Developer AI.
  3. Authors use a publishing pipeline to make new versions of the book.

### Four packages (the shared tool boxes)
- **content** — the trusted knowledge
- **learning** — remembers where each student left off
- **pedagogy** — the teaching moves (how to explain, when to quiz)
- **builder** — the templates and recipes for building agents

### Git + Postgres
Git holds the master text. Postgres (with a special search tool called pgvector) holds the fast searchable version. Change the book once; everything else updates.

### Near-zero AI cost
The platform does not pay for the AI brain. Each user uses their own AI subscription. The platform only serves the knowledge and the thin doors. That is why it can reach many people without a huge bill.

## Why would this be on the exam?
This is the real product built from the FDE AF Model. Later topics assume you understand how the pieces are wired and why the cost is so low.
