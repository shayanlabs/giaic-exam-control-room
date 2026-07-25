# 16. Part 5 — A Complete Loop, Twice

## Aasan Zabaan Mein Samjho

Ab tak humne loop ke parts alag alag parhe — heartbeat, body, spine, checker, sab kuch theory mein. Lekin asli maza tab aata hai jab ye saara maal ek sath, ek real scene mein chalta hua dekho. Is part mein ek "9am triage loop" ka pura live example diya gaya hai — dono Claude Code aur OpenCode mein — taake tumhein pata chale ye cheezein sirf kitaabi baatein nahi, real files aur commands mein bhi hoti hain.

Socho ek chota sa subah ka kaam: raat bhar kya hua, uska jaiza lena, jo zaroori hai us par kaam karna, aur phir insaan ke liye ek saaf report chhod dena. Itna chota kaam hai ke pura samajh aa jaye, lekin itna real bhi hai ke kaam ka ho.

Is example ka sabse important sabak ye hai: agar tum ye ek scenario poori tarah samajh lo — reviewer ka PASS/FAIL, PR banna, aur risky cheez ka insaan tak jaana — to tumhein loop engineering ka pura chakkar samajh aa jayega.

## Zaroori Concepts

### 9am triage loop
Ye ek practical subah ki routine hai — raat mein jo tabdeeliyan hui unko dekhna, kya important hai decide karna, tickets ya PRs banana/update karna, aur end mein insaan ke liye clear status chhodna.

### 6-step pseudocode
Loop ka ek tool-independent, saaf description jisme koi specific command ka shor nahi — sirf six steps saaf saaf dikhte hain.

### Har ek 6 loop parts ka real jaga
Heartbeat, body ke pieces, checker, spine ki updates, aur human gate — sab kuch actual working code aur files ke andar dikhte hain.

### Ek worked example: ek asli subah
Loop `progress.md` parhta hai, dekhta hai ek item abhi "in progress" hai. Do overnight CI failures aur ek naya npm-audit advisory milta hai. Pehli CI failure ke liye branch `claude/fix-auth-retry` par fix banata hai, reviewer PASS deta hai (tests green, koi API change nahi), to PR #142 khulta hai. Dusri failure par bhi wahi hota hai — PR #143. Lekin audit wali fix library ka output format badal degi, is liye reviewer FAIL deta hai ("public behaviour change"), aur wo item "Open / needs a human" mein `progress.md` mein likh diya jata hai, koi PR nahi khulta. Subah 9:30 baje tum uthte ho aur do PRs review karne ko hain aur ek flagged decision — tumne kuch nahi tapa. Yehi maker-checker split aur human gate ka milap ek asli run mein.

### Shared skill file
Poore loop ki logic ek hi `SKILL.md` file (`daily-triage`) mein rehti hai, is liye scheduled prompt sirf ek line ka hota hai ("run the daily-triage skill"). Skill ke andar five ordered steps likhe hote hain: pehle progress file parho, phir max 5 candidates jama karo (CI failures, phir labeled issues, phir audit advisories), har ek par isolated checkout mein kaam karo strict "one fix per PR" rule ke saath, reviewer ke verdict se decide karo (PASS aur low-risk to PR khulta hai; FAIL ya risky to "needs a human"), aur akhir mein progress file update karo. Rules jaise "ek run mein kabhi 5 se zyada PR mat kholna" aur "kabhi `main` seedha mat badalna" khud skill ke andar likhe hote hain — ye proof hai ke loop ke safety rules files mein rehte hain, sirf tumhare dimaag mein nahi.

## Exam Mein Ye Kyun Aayega?
Real tools mein complete loop ki shape pehchanna kisi ek command ratne se zyada zaroori hai. Exam tumse concepts ko concrete examples par map karwayega.
