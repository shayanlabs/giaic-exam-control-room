# 20. Part 1 — The Box

## Aasan Zabaan Mein Samjho

Ek agent sirf smart brain nahi hota. Agent = smart brain **plus** wo box jo usay gher ke rakhta hai.

Is box ka naam hai **harness**. Ye rules, tools, information, aur safety checks ka wo set hai jo brain ko itna reliable banata hai ke wo asal kaam kar sake.

Bina harness ke tumhare paas sirf ek smart autocomplete hai. Achhe harness ke saath tumhare paas ek Digital FTE hai jis par bharosa kiya ja sake.

## Zaroori Concepts

### 4 zaroori parts
Ek minimum harness mein ye cheezein hona zaroori hain:
- Agent kya kar sakta hai, wo limit karo
- Sahi information dena
- Kaam sahi hai ya nahi, check karna
- Kuch ghalat ho to recover karna

### Inner vs outer harness
- **Inner harness**: model ke bilkul paas rehta hai (rules file, skills, tool descriptions).
- **Outer harness**: thora door rehta hai (sandboxes, network limits, human approval steps, bahar wale checkers).

### Paanch verbs
Harness ke main kaam. Is course mein aam taur par ye hote hain:
1. Constrain (kya allowed hai, limit karo)
2. Inform (sahi context do)
3. Verify (result check karo)
4. Correct (fix ya recover karo)
5. Observe / Escalate (dekho kya ho raha hai, zaroorat par insaan ko bulao)

### Compounding reliability (95%^20 ≈ 36%)
Agar har single step 95% reliable hai, toh 20 steps ki chain sirf takreeban 36% reliable rehti hai. Isi liye safety sirf prompt mein nahi ho sakti — ye harness ke structure mein built hona chahiye.

### Guardrails harness mein hote hain, kabhi sirf prompt mein nahi
Prompt ko ignore ya override kiya ja sakta hai. Harness ke structural controls ko nahi.

### Chaar-part definition, ek real tool par test
2026 ke ek paper ne is definition ko exact bana diya: harness ko chahiye **agent loop** (chota loop jo model ko chalate rehta hai), **tool interface** (model kya actions le sakta hai, aur har ek ki shape), **context management** (window mein kya jata hai, kya compact hota hai, kya files mein push hota hai), aur **control mechanisms** (permissions, limits, checks — wo parts jo "na" bolte hain). Isko Claude Code par test karo: loop hai, tool set hai (Read, Edit, Bash, MCP servers), context management hai (compaction, subagent isolation, rules file), aur control hai (permission rules, hooks, sandboxing). Chaaron present hain — aur waise hi OpenCode mein, Aider mein bhi. Is course ka ask yehi hai: inhe ek conveniences ka menu samajhna chhoro, inhe ek system samjho jo engineer kiya gaya hai taake same model bure din bhi utni hi quality de jitni ache din.

### Harness bottleneck kyun ban gaya
Iska hisaab seedha hai: agar agent ka har step 95% waqt kaamyab hota hai, toh 20 steps ki chain sirf takreeban 36% waqt saaf saaf khatam hoti hai (0.95 ko khud se 20 baar multiply karo) — matlab individually reliable steps wala system bhi apne 20-step tasks mein se taqreeban do-tihai mein fail ho jata hai. Behtar model se ye 95% thora sa hi barhta hai. Harness seedha *chain* par attack karta hai: verification bad step ko jaldi pakar leta hai, recovery restart karne ki jagah resume karti hai, aur constraint kam kar deta hai ke ek bura step kitna nuksan kar sakta hai. Isi liye, jab rival labs ke top models coding tasks par ek dusre ke kareeb aa rahe hain, sirf harness change karke — model badle bina — real surveys mein coding benchmarks par 10x tak gains milte hain. Jab engine badalne se zyada box badalna kaam karta hai, toh engineering wahi ho rahi hai.

## Exam Mein Ye Kyun Aayega?
Ye samajhna ke agent = Model + Harness hai (sirf Model nahi), poore harness module ki buniyad hai.
