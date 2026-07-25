# 15. Part 4 — The Spine

## Aasan Zabaan Mein Samjho

Spine wo memory hai jo loop ke ek run ko agle run se jodti hai. Spine ke bagair loop ko amnesia ho jata hai — har subah wo utha kar wo sab kuch dobara seekhta hai jo kal pehle se jaanta tha. Ye time aur paisa dono zaya karta hai aur wahi ghaltiyan baar baar hoti hain.

## Zaroori Concepts

### No spine, no loop
Ye seedha saaf rule hai. Agar state runs ke darmiyan zinda nahi rehti, tumhare paas asal loop hai hi nahi — bas alag alag prompts ki ek series hai.

### `progress.md` repo ke andar rehta hai
Ek simple aur practical pattern: project ke andar ek Markdown file jo likh kar rakhti hai kya ho chuka hai, kya baaki hai, aur koi zaroori decisions. Baad ke runs isay parhte aur update karte hain.

### Spine cost lever bhi hai
Achi memory ka matlab hai agent kam tokens kharch karta hai history dobara parhne ya wohi facts dobara dhoondhne mein. Missing ya messy memory paisa jalane ke sabse fast tareeqon mein se ek hai.

### Runs ke darmiyan memory aur "dreaming" pass
Kuch designs mein ek khamosh "dreaming" ya cleanup pass shamil hota hai jo summarize karta hai, organize karta hai, ya kam-value details bhool jata hai taake project badhne ke saath spine useful reh sake.

### Intern ki diary
Ek naye intern ko train karna socho: tum unhe ek diary dete ho do standing instructions ke saath. Pehli, jab bhi unhe feedback mile, wo diary ke **agle** page par lesson likhein aur har subah usay dobara parhein — "wo pattern use mat karo," "ye team commits squash karti hai." Doosri, ghar jane se pehle wo diary ke **peeche** likhein kya khatam kiya aur kahan ruke, taake kal wahin se shuru ho jahan aaj chhoda. Diary ka agla hissa tumhara **rules file** hai (`CLAUDE.md`/`AGENTS.md`): durable lessons, har run parhi jati hain. Peeche wala hissa **progress file** hai: checkpoints, har run update hote hain. Diary ke bagair intern wahi corrections baar baar seekhega aur kal ka kaam dobara karega — aur loop bhi wahi karta hai, kyunke model ki memory runs ke darmiyan poori tarah saaf ho jati hai, jabke intern ki kam se kam dheere dheere dhundhli hoti hai.

### Dreaming: improvement loop bhi ek product hai
Rules file mein ek lesson likhna taake aage har run behtar behave kare, iska naam hai **hill-climbing loop**, kabhi kabhi "dreaming" kaha jata hai — ek alag loop, apni heartbeat ke saath (aam taur par weekly, daily nahi), jo run transcripts ka ek batch parhta hai, wo galtiyan dhoondta hai jo sessions mein baar baar hoti hain, aur memory store mein changes propose karta hai — hamesha ek PR ke taur par cited evidence ke saath, kabhi direct edit nahi. Claude Code ka research-preview **Auto Dream** feature isi ka halka version automatically karta hai: duplicate notes merge kar deta hai aur wo notes delete kar deta hai jinko naye kaam ne ghalat saabit kar diya, magar ye sirf memory files ko chhoo sakta hai, code ko kabhi nahi. Do real risks isi liye human gate ko non-negotiable banate hain: **memory poisoning** (ek run ke input mein daali gayi instruction memory mein likhi jati hai aur aage har run ko steer karti hai) aur **brevity bias/context collapse** (ek detailed playbook baar baar summarize hote hote ek dhundhle paragraph mein rah jati hai). Isi liye koi public model tumhare sessions se apne weights khud nahi badalta — jo behtar hota hai wo sab model ke **ird gird** hai, aur sirf ek insaan ka PR merge karna hi us improvement ko permanent banata hai.

## Exam Mein Ye Kyun Aayega?

Runs ke darmiyan state bhool jana asal loops ke fail hone ka sabse aam tareeqa hai — exam spine ko design ka first-class hissa maanta hai, afterthought nahi.
