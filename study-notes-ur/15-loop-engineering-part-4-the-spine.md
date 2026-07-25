# 15. Part 4 — The Spine

## Aasan Zabaan Mein Samjho

Spine wo memory hai jo loop ke ek run ko agle run se jorti hai.

Spine na ho to loop ko amnesia ho jata hai. Har subah usay woh sab kuch dobara seekhna padta hai jo wo kal jaanta tha. Isse time aur paisa dono zaya hota hai, aur wahi ghaltiyan baar baar hoti hain.

## Zaroori Concepts

### Spine nahi to loop nahi
Ye seedha saaf rule hai. Agar state ek run se doosre run tak zinda nahi rehti, tumhare paas real loop nahi — bas alag alag prompts ki line hai.

### `progress.md` repo mein rehta hai
Ek simple aur practical pattern: project ke andar ek Markdown file jo likhti hai kya ho chuka, kya baaki hai, aur koi zaroori decisions kya rahe. Agle runs isay parh kar update karte hain.

### Spine ek cost lever bhi hai
Achhi memory ka matlab hai agent ko baar baar history dobara parhni ya wahi facts dobara dhoondni nahi parti — kam tokens lagte hain. Missing ya messy memory paisa jaldi udane ka sab se fast tareeqa hai.

### Runs ke darmiyan memory aur "dreaming" pass
Kuch designs mein ek chupka sa "dreaming" ya cleanup pass hota hai jo summarize karta hai, organize karta hai, ya kam-value details bhool jata hai — taake project barhne ke saath spine bhi useful rahe.

### Intern wali diary
Ek naye intern ko train karna socho: tum usay ek diary do, jisme do standing instructions hain. Pehli: jab bhi usay feedback mile, wo lesson diary ke **aage** likhe aur har subah dobara parhe — "ye pattern use mat karo," "ye team commits squash karti hai." Doosri: ghar jaane se pehle, diary ke **peeche** likhe usne kya khatam kiya aur kahan roka, taake kal wahin se shuru ho jahan aaj chhoda tha. Diary ka agla hissa tumhara **rules file** hai (`CLAUDE.md`/`AGENTS.md`) — pakke lessons, har run mein parhe jaate hain. Peechla hissa **progress file** hai — checkpoints, har run mein update hote hain. Diary ke bagair intern wahi corrections baar baar seekhega aur kal ka kaam dobara karega — aur loop bhi bilkul yahi karta hai, kyunke model ki memory har run ke beech mit jati hai, jabke intern ki memory kam se kam dheere dheere fade hoti hai.

### Dreaming: improvement loop khud ek product ban jata hai
Rules file mein lesson likh dena taake har agla run behtar chale — iska ek naam hai: **hill-climbing loop**, kabhi kabhi "dreaming" bhi kehte hain — ek alag loop, apna heartbeat (usually weekly, daily nahi), jo run transcripts ka ek batch parhta hai, sessions mein baar baar hone wali ghaltiyan dhoondta hai, aur memory store mein changes propose karta hai — hamesha ek PR ki tarah, cited evidence ke saath, kabhi direct edit nahi. Claude Code ka research-preview **Auto Dream** feature isi ka halka version khud-ba-khud karta hai: duplicate notes merge karta hai, jo baatein naye kaam ne ghalat prove kar di hon unhe delete karta hai — lekin ye sirf memory files ko chhoo sakta hai, code ko kabhi nahi. Do real risks isi liye human gate ko zaroori banate hain: **memory poisoning** (ek run ke input mein plant ki gayi instruction memory mein likhi jaye aur har agle run ko galat raste par le jaye) aur **brevity bias / context collapse** (ek detailed playbook baar baar summarize hote hote ek dhundle se paragraph mein simat jaye). Isi liye koi public model tumhari sessions se apne weights khud nahi badalta — jo behtar hota hai wo sab kuch model ke **ird-gird** hai, aur wo permanent tabhi banta hai jab koi insaan PR merge kare.

## Exam Mein Ye Kyun Aayega?
Runs ke darmiyan state bhool jana — real loops ke fail hone ka sab se aam tareeqa hai. Exam spine ko design ka ek first-class hissa maanta hai, koi afterthought nahi.
