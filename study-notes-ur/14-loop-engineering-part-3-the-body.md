# 14. Part 3 — The Body

## Aasan Zabaan Mein Samjho

Body wo hissa hai jo loop ke ek run ke andar actually kaam karta hai. Agar heartbeat alarm clock hai to body wo insaan hai jo utha kar chores karta hai.

## Zaroori Concepts

### Worktrees
Alag folders aur branches taake do agents (ya do runs) ek doosre ki files par pair na rakhein aur gadbad na banayein.

### Skills
Instructions ke saved packets jinhe agent dobara use kar sakta hai — ye knowledge aur pasandida tareeqon ko package karte hain.

### Connectors
Wo pipes jinse agent bahar ke systems tak pahonch sakta hai (GitHub, Slack, databases, waghera).

### Maker–checker
Ek agent (ya process) kaam banata hai, ek doosra agent ya command usay check karta hai. Ye sabse zaroori reliability patterns mein se ek hai — jab stakes bade hon to kabhi bhi ek hi process ko apna kaam khud banane aur khud poori tarah approve karne mat do.

### Checker ladder
Checks ka ek set jo dheere dheere strong aur mehnga hota jata hai. Sasti/fast checks se shuru karo, mehngi/thorough checks sirf zaroorat par use karo.

### Dynamic workflows body hain, loop nahi
Ek fancy multi-step workflow bhi jo ek hi run ke andar chale, phir bhi bas body hi hai. Loop wo cheez hai jo baad mein doosra run shuru karne ka faisla karta hai.

### Verification skills ke 4 ghar
Checking logic tool ke hisab se alag jagah reh sakti hai: rules files, skills, hooks, ya bahar ke checkers.

### Loop mein connectors ke liye khaas rules kyun
Connector (jo MCP par bana hota hai) loop ko sirf baat karne ke bajaye **act karne** deta hai — PR khol na, ticket update karna, Slack par post karna. Magar chunke loop retry karta hai aur tools khud chunta hai bina kisi ke dekhe, teen rules khaas ahmiyat rakhte hain jo haath se kaam karte waqt utne zaroori nahi hote: **kam, focused tools bohot saari overlapping tools se behtar hain** (tool choose karna har beat par nayi decision hai, koi check nahi karta — agar ek human engineer yaqeen se nahi bata sakta konsa tool sahi hai, to agent bhi nahi bata sakta), **writes repeat hone par bhi safe honi chahiye** (retry hua "create customer" call agar dobara customer bana de to duplicate billing ho jati hai, is liye blind creates se behtar hai update-or-create), aur **error messages ko batana chahiye aage kya karna hai**, kyunke loop mein error message hi agle beat ka input hota hai — "Permission denied: request the `repo` scope" khud retry par theek ho jata hai, jabke "Error 403" sirf ek beat zaya karta hai.

### Verification skill ke chaar ghar
Ek check jo tum har change ke baad haath se chalate rehte ho ("kya maine logs se request body nikaal di?") chaar gharon mein se kisi ek mein reh sakta hai, har ghar ek alag heartbeat hai: **standalone** (tum khud jaan boojh kar chalate ho — tum abhi bhi heartbeat ho), **embedded** (us skill ke aakhir mein jod diya jo kaam karti hai, taake khud fire ho — magar sirf un skills par kaam karta hai jinhe tum edit kar sakte ho, kyunke built-in ya plugin skills chupke se overwrite ho jati hain), **chained** (ek skill apne aakhir mein doosri ko call karti hai, "main hamesha check chalata hoon baad mein" ko "skill hamesha check chalati hai" bana deti hai), aur **har PR par** (wahi check event heartbeat se fire hoti hai, taake teammate ka change bhi wahi gate paar kare jo tumhara). Graduation rule: seedha "har PR par" par mat kudo — har ghar ne pichle ghar mein khud ko sahi saabit karna hota hai, wahi "unattended se pehle watched" discipline jo loops par khud lagti hai.

## Exam Mein Ye Kyun Aayega?

Loops banane ka zyada tar concrete engineering kaam body ke andar hota hai — exam expect karta hai tumhe main pieces pata hon, khaas kar maker–checker idea.
