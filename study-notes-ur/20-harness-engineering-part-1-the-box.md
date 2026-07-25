# 20. Part 1 — The Box

## Aasan Zabaan Mein Samjho

Agent sirf ek smart dimaag nahi hota. Agent = smart brain **plus** wo box jo uske charo taraf hoti hai.

Is box ka naam hai **harness**. Ye rules, tools, information, aur safety checks ka wo set hai jo brain ko itna reliable banata hai ke wo real kaam kar sake.

Socho ek bohot talented driver hai lekin us ke paas seatbelt, brakes, aur traffic rules nahi hain — wo bohot khatarnak driver banega, chahe wo kitna hi skilled kyun na ho. Harness ke bagair agent ek clever autocomplete hai. Ek achi harness ke sath wo ek Digital FTE ban jata hai jis par bharosa kiya ja sake.

## Zaroori Concepts

### 4 zaroori parts
Minimum harness ke paas ye tareeke hone chahiye:
- Agent kya kar sakta hai wo limit karna
- Sahi information dena
- Kaam achi tarah hua ya nahi check karna
- Kuch ghalat ho jaye to recover karna

### Inner vs outer harness
- **Inner harness**: model ke qareeb rehta hai (rules files, skills, tool descriptions).
- **Outer harness**: aur door rehta hai (sandboxes, network limits, human approval steps, bahar ke checkers).

### Panch verbs
Harness ke main kaam. Is course mein aam tor par ye samjhe jate hain:
1. Constrain (kya allowed hai wo limit karo)
2. Inform (sahi context do)
3. Verify (result check karo)
4. Correct (fix ya recover karo)
5. Observe / Escalate (dekho kya ho raha hai aur zarurat par insaan ko bulao)

### Compounding reliability (95%^20 ≈ 36%)
Agar har ek step 95% reliable hai, to 20 steps ki chain sirf takreeban 36% reliable hoti hai. Isi liye safety sirf prompt mein nahi ho sakti — ye harness ke structure mein built-in honi chahiye.

### Guardrails harness mein rehte hain, kabhi sirf prompt mein nahi
Prompt ko ignore ya override kiya ja sakta hai. Lekin harness ke structural controls ko nahi kiya ja sakta.

### Four-part definition — ek real tool par test kiya gaya
2026 ke ek paper ne is definition ko bilkul exact bana diya: ek harness ko chahiye **an agent loop** (chota loop jo model ko kaam mein rakhta hai), **a tool interface** (jo actions model le sakta hai, aur har ek ki shape), **context management** (window mein kya jata hai, kya compact hota hai, kya files mein push hota hai), aur **control mechanisms** (permissions, limits, checks — jo "na" bolne wale parts hain). Isko Claude Code par test karo: is mein loop hai, tool set hai (Read, Edit, Bash, MCP servers), context management hai (compaction, subagent isolation, rules file), aur control hai (permission rules, hooks, sandboxing). Sab chaaron present hain — OpenCode aur Aider mein bhi. Course ka ye shift chahta hai: inhe conveniences ke menu ki tarah mat dekho, inhe ek engineered system ki tarah dekho jo same model se achi quality nikalta hai, chahe din acha ho ya bura.

### Harness bottleneck kyun bana
Iske peeche ka arithmetic ye hai: agar agent ka har step 95% waqt succeed karta hai, to 20 steps ki chain sirf takreeban 36% waqt cleanly finish hoti hai (0.95 ko khud se 20 baar multiply karo) — matlab aisa system jiske individual steps reliable hain, wo phir bhi apne 20-step tasks mein se taqreeban do-tehai fail karta hai. Ek behtar model us 95% ko thoda sa hi upar dhakel sakta hai. Harness *chain* par khud attack karti hai: verification kisi bad step ko jaldi pakad leti hai, recovery restart ki bajaye resume karti hai, aur constraint kisi bad step ke nuksaan ko chota kar deti hai. Isi liye, jab rival labs ke top models coding tasks mein ek dusre ke qareeb aa rahe hain, to sirf harness change karne se — koi model swap kiye baghair — real surveys mein coding benchmarks par 10x tak gains dekhe gaye hain. Jab box change karna engine change karne se behtar result de, to engineering asal mein box mein hi hoti hai.

## Exam Mein Ye Kyun Aayega?
Ye samajhna ke agent = Model + Harness hai (sirf Model nahi), pure harness module ki bunyad hai.
