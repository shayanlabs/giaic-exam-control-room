# 26. Hooks Appendix

## Aasan Zabaan Mein Samjho

Hooks wo concrete jagahain hain jahan tum apna khud ka control code agent ki zindagi mein daal sakte ho. Socho agent ki poori journey ek movie hai, aur hooks us movie ke wo scenes hain jahan tum pause bana kar apna khud ka checkpoint laga sakte ho — kisi cheez ko rok sakte ho, log kar sakte ho, ya feedback de sakte ho.

Ye appendix ek practical reference hai: paanch important moments, simple exit-code language, aur teen drills taake ye ideas dimaag mein bas jayein.

Sabse zaroori baat ye hai ke ek hi exit code ka matlab har jagah alag hota hai — ye is baat par depend karta hai ke hook kaunse moment se juda hai. Isay samajhna hi is appendix ka core hai.

## Zaroori Concepts

### 5 important moments
- **SessionStart** — jab ek naya session shuru hota hai.
- **PreToolUse** — kisi tool ke chalne se theek pehle (sabse important gate).
- **PostToolUse** — kisi tool ke chalne ke turant baad (feedback aur logging ke liye).
- **Stop** — jab agent kaam khatam karna chahta hai.
- **SubagentStop** — jab koi helper agent apna kaam khatam karta hai.

### Exit-code contract
Ek simple, reliable tareeka jisse hook system ko "success," "failure," ya "is action ko block karo" bata sakta hai (jaise exit code 2 ek hard stop ke tor par).

### 3 drills
Hands-on exercises jo tumhein realistic situations mein hooks likhne aur dekhne par majboor karte hain.

### Exit-code contract, bilkul saaf tareeke se
Hook bas ek command hai jisay event ki details JSON mein milti hain aur jo ek exit code ke sath jawab deta hai — lekin us code ka matlab is baat par depend karta hai ke wo *kaunse* moment se juda hai. Zero hamesha pass karta hai. Do **gate** events par, `PreToolUse` aur `Stop`, exit code `2` khaas hota hai: ye waqai action ko block kar deta hai ya session ko finish nahi hone deta, jab ke koi bhi aur non-zero code sirf ek non-blocking error hai jo kuch nahi rokta. `PostToolUse` par, action pehle hi chal chuka hota hai, is liye exit `2` usay undo nahi kar sakta — iski jagah, hook ne stderr par jo bhi print kiya wo agent ke agle input ke tor par wapas diya jata hai. Yehi asli design surface hai: ek hook jo print karta hai "blocked: tests failing in test/auth — fix those first" wo ek hi waqt mein guardrail bhi hai aur self-healing error message bhi — Parts 2 aur 3 dono ka kaam ek sath karta hai.

### Teen drills, saaf tareeke se
Drill 1 (**stream dekho**) ek hook attach karta hai jo har tool call ke liye `trace.log` mein ek line add karta hai, phir ek normal beat ke baad tumse usay parhwata hai — zyada tar log hairan reh jate hain ke ek beat mein asal mein kitni actions hoti hain, aur yehi observability ka poora point hai. Drill 2 (**jaan-boojh kar block karo**) ek `PreToolUse` check likhta hai jo `curl` wala koi bhi Bash command block karta hai, ek error ke sath jo allowed alternative bataye, taake tum poora cycle dekh sako: blocked, informed, redirected. Drill 3 (**conditional gate**) test-suite wale `Stop` hook ko sirf tab chalata hai jab source files waqai us beat mein change hui hon (`git diff --name-only` se check kiya jata hai), aur yehi tareeka hai ke real harnesses kaafi tez rehti hain taake log slow check ko disable karne ki bajaye use karte rahein.

## Exam Mein Ye Kyun Aayega?
Hooks is course ke tools mein harness control ka main extension point hain. Paanch moments aur exit-code contract se familiarity expected hai.
