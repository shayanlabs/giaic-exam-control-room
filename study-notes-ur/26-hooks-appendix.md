# 26. Hooks appendix

## Aasan Zabaan Mein Samjho

Hooks wo concrete jagahein hain jahan tum agent ki zindagi ke andar apna khud ka control code daal sakte ho.

Ye appendix ek practical reference hai: paanch important moments, simple exit-code language, aur teen drills taake ye ideas dimaagh mein basmein.

## Zaroori Concepts

### 5 moments jo matter karte hain
- **SessionStart** — jab naya session shuru hota hai.
- **PreToolUse** — tool chalne se bilkul pehle (sabse important gate).
- **PostToolUse** — tool chalne ke bilkul baad (feedback aur logging ke liye).
- **Stop** — jab agent finish karna chahta hai.
- **SubagentStop** — jab koi helper agent finish karta hai.

### Exit-code contract
Ek simple, reliable tareeqa jisse hook system ko "success," "failure," ya "is action ko block karo" bata sakta hai (misaal ke taur par, exit code 2 hard stop ke liye).

### 3 drills
Hands-on exercises jo tumhe hooks likhne aur real situations mein observe karne par majboor karte hain.

### Exit-code contract, poori tarah se
Hook bas ek command hai jo event ke details JSON mein leta hai aur exit code se jawab deta hai — lekin us code ka matlab depend karta hai ke wo *kaunse* moment se attach hai. Zero hamesha pass hota hai. Do **gate** events par, `PreToolUse` aur `Stop`, exit code `2` khaas hota hai: ye action ko actually block kar deta hai ya session ko finish hi nahi hone deta, jabke koi bhi doosra non-zero code sirf ek non-blocking error hai jo kuch nahi rokta. `PostToolUse` par, action pehle hi chal chuka hota hai, isliye exit `2` usay undo nahi kar sakta — iski jagah, hook ne stderr par jo bhi print kiya, wo agent ke bilkul agle input ki tarah wapas de diya jata hai. Yehi asal design surface hai: ek hook jo print kare "blocked: tests failing in test/auth — pehle unhe fix karo" — ye ek saath guardrail bhi hai aur self-healing error message bhi, Part 2 aur Part 3 dono ka kaam ek saath kar raha hai.

### Teen drills, concrete tareeqe se
Drill 1 (**stream dekho**) ek hook attach karta hai jo har tool call ki ek line `trace.log` mein likhta hai, phir tumse ek normal beat ke baad usay padhwata hai — zyada tar log surprise ho jate hain ke ek akela beat asal mein kitne actions leta hai, aur yehi observability ka poora point hai. Drill 2 (**jaan bujh kar block karo**) ek `PreToolUse` check likhta hai jo kisi bhi Bash command ko block kare jisme `curl` ho, aur error mein allowed alternative naam bhi de — taake tum poora cycle dekho: blocked, informed, redirected. Drill 3 (**conditional gate**) test-suite ke `Stop` hook ko sirf tab chalata hai jab source files us beat mein actually change hui hon (`git diff --name-only` se check karke) — real harness aisi hi teiz rehti hain, taake log slow check ko disable karne ki bajaye use karte rahen.

## Exam Mein Ye Kyun Aayega?
Hooks is course ke tools mein harness control ka main extension point hain. Paanch moments aur exit-code contract se familiarity zaroori hai.
