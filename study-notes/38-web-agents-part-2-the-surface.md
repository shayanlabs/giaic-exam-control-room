# 38. Part 2 — The Surface

## Simple Explanation (like you're 5)

The web surface has its own rules about accounts, files, connectors, and where finished work lives.

If you do not understand the surface, the agent’s work can disappear or become locked inside the platform.

## Key Concepts Unpacked

### Account spine
The identity and permission structure that ties sessions, files, and connectors together.

### The three file tiers
- **Tier 1 — Scratch**: temporary, can disappear.
- **Tier 2 — Platform**: lives inside the vendor’s system.
- **Tier 3 — Your custody**: exported or stored in a place you fully control.

Finished work should exit the platform into Tier 3.

### Connectors
The links that let the web agent reach outside systems. They are usually more limited and more permissioned than local connectors.

### The gate in your pocket
The approval step that often lives on your phone or in a notification. It is the human control point when the agent wants to take a consequential action while you are away.

### A worked example: Ayesha's invoice, tier by tier
Ayesha runs monthly invoicing for a client. The draft numbers — the agent's scratch math, a temporary CSV — live in Tier 1 and die there, which is correct: nobody audits scratch paper. The invoice *template* she'll reuse next month goes to Tier 2, platform storage, attached to a session she'll reopen in thirty days. The finished invoice PDF goes to Tier 3 twice: saved to the firm's Drive folder, and emailed to the client through the mail connector. Why twice, and why Tier 3 at all? Because one day someone will ask "where is the March invoice?" — an auditor, a partner, or Ayesha herself in November — and the answer must be *the firm's records*, not "somewhere in my agent account." The one-line rule to memorize: **finished work exits the platform, everything else may stay.**

### Why connectors carry double weight on the web
On a desktop agent there's a third trust lever — which local folders the agent may see — but a browser-only session has no local filesystem to scope, so that lever's job splits between the tier decision above and the connector scopes you grant. That means a connector isn't just the agent's reach into your services; it's *also* the main automated exit door for files, since the Tier-3 path mostly runs through the connectors you've allowed. Two specifics matter here: read scope is not send scope (a mail connector that can summarize threads is a different, bigger grant than one that can send), and untrusted content — an inbound email, a vendor PDF — always gets the careful mode, because text someone else wrote can carry hidden instructions the agent might read as commands (prompt injection).

## Why would this be on the exam?
Without clear ownership of files and a reliable gate, web agents become black boxes that produce work you cannot fully trust or recover.
