# 14. Part 3 — The Body

## Aasan Zabaan Mein Samjho

Body wo hissa hai jo loop ke ek run ke andar asal kaam karta hai.

Heartbeat agar alarm clock hai, to body wo insaan hai jo utha kar ghar ka kaam karta hai.

## Zaroori Concepts

### Worktrees
Alag folders aur branches, taake do agents (ya do runs) ek doosre ki files par pair na maren aur mess na banaye.

### Skills
Save ki hui instructions ke packets jo agent dobara use kar sake. Ye knowledge aur pasandida kaam karne ke tareeqe pack karti hain.

### Connectors
Wo pipes jo agent ko bahar ke systems (GitHub, Slack, databases waghera) tak pohanchate hain.

### Maker–checker
Ek agent (ya process) kaam banata hai. Doosra agent ya command usay check karta hai. Ye sab se important reliability patterns mein se ek hai. Jab stakes high ho, kabhi bhi ek hi process ko apna kaam khud pura approve mat karne do.

### Checker ladder
Checks ka ek set jo dheere dheere strong aur mehnga hota jata hai. Pehle sasty/fast checks se shuru karo. Mehnge, thorough checks tab hi use karo jab zaroorat ho.

### Dynamic workflows ek beat ki body hain, loop nahi
Ek single run ke andar ka fancy multi-step workflow bhi sirf body hai. Loop wo cheez hai jo baad mein ek aur run shuru karne ka faisla karta hai.

### Verification skills 4 ghar mein
Checking logic tool ke hisab se alag jagah reh sakti hai: rules files, skills, hooks, ya bahar ke checkers.

### Connectors ko loop mein khaas rules kyun chahiye
Connector (MCP par bana hua) hi wo cheez hai jo loop ko sirf baat karne ki bajaye kaam karne deta hai — PR khol dena, ticket update karna, Slack par post karna. Lekin loop retry karta hai aur bina kisi ke dekhe tools choose karta hai, is liye teen rules aisi matter karti hain jo haath se kaam karte waqt utni matter nahi karti: **kam, focused tools zyada overlapping tools se behtar hain** (tool choice har beat par nayi banti hai, bina kisi check ke — agar ek human engineer confidently na bata sake konsa tool sahi hai, to agent bhi nahi bata sakta); **writes repeat hone ke liye safe hone chahiye** ("create customer" wala retry call agar doosra customer bana de, matlab double billing — is liye blind create ki bajaye update-or-create behtar hai); aur **error messages agla step batayen**, kyunke loop mein error message hi agle beat ka input banta hai — "Permission denied: repo scope maango" khud retry par fix ho jata hai, jabke "Error 403" sirf ek beat zaya karta hai.

### Verification skill ke 4 ghar
Jo check tum manually har change ke baad chalate ho, wo 4 ghar mein reh sakta hai, har ek ka apna heartbeat: **standalone** (tum khud jaan boojh kar chalate ho — tum abhi bhi heartbeat ho), **embedded** (kaam karne wali skill ke aakhir mein jur jata hai, khud fire hota hai — sirf un skills par kaam karta hai jo tum edit kar sakte ho, built-in ya plugin skills chupke se overwrite ho jati hain), **chained** (ek skill apne end par doosri ko call karti hai — "main hamesha baad mein check chalata hoon" se "skill khud hamesha check chalati hai" ban jata hai), aur **har PR par** (wahi check event heartbeat se fire hota hai, taake teammate ka change bhi wahi gate paar kare jo tumhara kiya tha). Graduation rule: seedha "har PR par" mat kudo — har ghar ko pehle wale ghar mein khud ko sahi prove karna parta hai, wahi "unattended se pehle watched" wala usool jo loops par bhi laagu hota hai.

## Exam Mein Ye Kyun Aayega?
Loops banane ka zyada tar concrete engineering kaam body mein hi hota hai. Exam mein main pieces, khaas kar maker-checker idea, pata hona chahiye.
