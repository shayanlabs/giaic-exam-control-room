# 16. Part 5 — A Complete Loop, Twice

## Aasan Zabaan Mein Samjho

Dekho, loop ke baare mein padhna ek baat hai, aur usay real mein bante hue dekhna bilkul alag baat hai. Ye part wahi karta hai — ek poora loop, do alag tools mein (Claude Code aur OpenCode), shuru se end tak, real files aur real commands ke saath.

Example simple hai: 9am triage loop. Subah subah AI khud uthta hai (matlab chalta hai), dekhta hai raat ko kya hua, decide karta hai kya important hai, khud tickets ya PRs bana deta hai, aur jo cheez risky lage usay insaan ke liye chhod deta hai.

Sabse achi baat? Poori loop ki logic ek hi jagah likhi hoti hai — ek SKILL.md file mein. Isse scheduled prompt sirf ek line ka reh jata hai: "daily-triage skill chalao."

## Zaroori Concepts

### 9am triage loop
Subah ka practical routine — raat ko kya change hua dekho, kya matter karta hai decide karo, tickets/PRs banao ya update karo, aur human ke liye clear status chhodo. Chota hai, samajhna aasan hai, aur kaam ka bhi hai.

### 6-step pseudocode
Loop ka clean, tool-independent version — kisi bhi specific command ke bina six parts dikha deta hai.

### 6 parts real example mein kahan hain
Heartbeat, body ke pieces, checker, spine ke updates, aur human gate — sab kuch actual working code aur files ke andar dikhte hain.

### Worked example — ek asli subah
Loop `progress.md` padhta hai, dekhta hai ek item abhi bhi "in progress" hai. Do CI failures milti hain aur ek naya npm-audit advisory. Pehli CI failure ke liye branch `claude/fix-auth-retry` par fix draft karta hai; reviewer PASS deta hai (tests green, koi API change nahi) — toh PR #142 khulta hai. Dusri failure ka bhi same — PASS, PR #143. Lekin audit fix se library ka output format change ho jata, isliye reviewer FAIL deta hai ("public behaviour change") — loop is item ko `progress.md` mein "Open / needs a human" likh deta hai, koi PR nahi khulta. 9:30 baje tum uthte ho toh do PRs review karne ko milte hain aur ek decision flag hoti hai — aur tumne khud kuch type tak nahi kiya. Yehi hai maker-checker split aur human gate ek saath kaam karte hue, real time mein.

### Shared skill file
Poori loop ki logic `daily-triage` naam ki ek SKILL.md file ke andar hoti hai. Isme paanch steps order se likhe hote hain: pehle progress file padho, phir max 5 candidates ikattha karo (pehle CI failures, phir labeled issues, phir audit advisories), har ek ko isolated checkout mein kaam karo (sakht rule: "one fix per PR"), reviewer ke verdict se decide karo (PASS aur low-risk ho toh PR khol do, FAIL ya risky ho toh "needs a human" mein daal do), aur sabse end mein progress file update karo. "Ek run mein kabhi 5 se zyada PR mat kholo" aur "main ko kabhi direct mat chhero" jaisi safety rules seedha skill file ke andar likhi hoti hain — matlab loop ki safety rules files mein rehti hain, sirf tumhare dimaagh mein nahi.

## Exam Mein Ye Kyun Aayega?
Kisi ek command ko ratta lagane se zyada zaroori hai ke real tools mein complete loop ka shape pehchan sako — exam tumse concepts ko concrete examples pe map karwayega.
