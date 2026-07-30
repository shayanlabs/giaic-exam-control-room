# 9. FDE AF Model I — the five layers

## Simple Explanation (like you're 5)

The big picture in one sentence: build the expensive stuff once at the bottom, let it be reused endlessly, and let individual people build and earn money at the top, on customer-specific work.

## Key Concepts Unpacked

### Layer 0 — the equipment factory (built once, never rebuilt)
Four real pieces of already-installed, already-running software:

- **Markdown + Docusaurus** — write plain text, it auto-becomes a website
- **Postgres + pgvector** — a database that can search by meaning, not just exact words
- **MCP** — the standard way an AI agent asks for and receives information
- **Better Auth** — checks who's allowed to see what

Pizza version: the oven, fridge, and POS machine are already installed and wired. Nobody rebuilds these for each new restaurant.

Produces raw technical machinery. Consumed by Layer 1 builders. Contains zero actual content or subject matter.

### Layer 1 — the recipe management system (the reusable kernel)
Those four tools get assembled into one working, reusable system capable of taking any Markdown content and turning it into something searchable and trustworthy. This is the **kernel** — there's only one kernel design.

Anyone can then pour their own content into it, creating an **instance**: this book's content is one instance, someone's accounting rulebook is another, a client's manual is another.

Pizza version: a fully wired, working kitchen (the kernel) with no menu decided yet. Load in Pizza Hut's menu and you get one instance; load in Domino's menu and you get a different instance. Same kitchen, different content.

Produces the kernel plus generic instances. Consumed by Layer 2 builders, Layer 3 verticals, and any client wanting their own trustworthy content system.

### System of Record — three scopes, not one
"System of Record" gets used loosely, so keep these separate:

- **Machinery** — the raw tools (Layer 0)
- **Kernel** — the one assembled, reusable system (Layer 1)
- **Instance** — one specific content-filled copy (this book's version, an accounting version, a client's manual)

One kernel, many instances — never many kernels.

### Layer 2 — the culinary school and kitchen consultants
Reusable teaching and building tools, packaged into two products: **Zia Tutor AI** teaches the whole method, and **Zia Developer AI** helps you actually build things.

Pizza version: one culinary school with the same curriculum, whether you'll cook pizza or burgers later.

Produces generic learning and building components. Consumed by learners today, and by Layer 3 tomorrow, which reuses these components rather than modifying them.

### Layer 3 — the actual franchise brand (for example "Pizza Hut")
Profession-specific. For one profession — accounting, healthcare, and so on — you build the trio:

1. **Domain System of Record** — that profession's actual rules (tax law, medical protocol) loaded into the Layer 1 kernel
2. **Domain expert twin** — an AI tutor teaching in that specific expert's voice
3. **Domain builder** — the tool used to manufacture that profession's AI workers, with compliance built in

Inside the domain SoR, knowledge splits into three forms:

- **Corpus** — things the AI must find and cite as proof (a specific regulation)
- **Map** — a short guide telling the AI what exists and when to check it (never skip KYC before onboarding)
- **Reflexes** — a complete procedure handed over whole, not searched in pieces (a fixed monthly-closing checklist)

One domain builder per profession, shared by every company in that field, never forked per customer. This is the **promotion law** in action: if the same fix repeats across clients, it gets folded back into the shared builder so everyone benefits, instead of every consultant maintaining their own diverging version forever.

Produces the trio, per vertical. Consumed by professionals in that field and the FDEs deploying for them.

### Layer 4 — one actual restaurant, in one city, run by one owner
Real work, for one paying company, with proof it actually worked. Two fixed points are agreed before building starts:

- **Contract of success** — baseline (current performance, for example "4 hrs per file") plus target ("40 min per file") plus acceptance criteria ("95% correct on first pass")
- **Proof in production** — business KPIs improved, people actually adopted it, and agent evaluations pass — all three needed, not just one

Two separate roles do this: the **Outcome Architect** owns the business problem, workflow, and outcome; the **FDE** owns the technical build, integration, and evaluation. On small jobs, one person can be both.

Produces a proven business outcome for one company. Consumed by that company's actual human and AI teams.

### The full order things happen in (often tested)
Expert commits, then a thin slice is built (one outcome, done completely), then a sponsor is found, then the baseline is measured, then the contract of success is signed, then the engagement is built and deployed, then proof is shown, then the System of Record grows thicker.

Notice: it does not start with a customer. It starts with an expert and one complete slice of work, which is what creates the sponsor conversation.

### Ayesha's path
Layer 0 is already running when she starts. Layer 1: she loads her aunt's accounting manual into a searchable system. Layer 2: she trains via Zia Tutor AI and Zia Developer AI. Layer 3: she partners with her aunt, the real expert, to build the accounting trio. Layer 4: she finds a Chicago sponsor, agrees "4 hrs to 40 min" as the contract, builds the Digital FTE, and proves the result in production.

## Why would this be on the exam?
This is the big picture of both the technology and the business. Almost every other topic is a detail inside one of these layers.
