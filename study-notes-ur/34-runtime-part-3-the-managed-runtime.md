# 34. Part 3 — The Managed Runtime

## Aasan Zabaan Mein Samjho
Socho tumhe apna khud ka server nahi chalana, apna khud ka sandbox nahi banana — koi service tumhe seedha ek ready agent, ek safe box, aur ek session de deti hai. Bas! Ye hai managed runtime. Fayda ye hai ke scaling easy hai, isolation milta hai, operational kaam kam hota hai. Nuksan ye hai ke host pe deep control nahi milta, kabhi kabhi exact tool versions bhi tumhare haath mein nahi hote, aur paisa lagta hai.

Course ka concrete example hai Claude Managed Agents (public beta, April 2026). Isme teen cheezein milti hain: ek **agent** (definition — model, prompt, tools, guardrails, matlab tumhari rules file jo service samajh sake), ek **environment** (jahan actions chalte hain — default cloud sandbox, ya agar custody zaroori ho to apna khud ka self-hosted sandbox), aur ek **session** (ek chalta hua kaam, apni memory aur apna cost meter ke saath, jo din-din tak pause-resume ho sakta hai, laptop khula rakhne ki zaroorat nahi).

Yahan pe pehli baar model (jo sochta hai) aur sandbox (jo karta hai) alag alag dikhte hain — pehle ye dono tumhare laptop pe ek hi process mein chhupe hote the, ab service unhe jodti hai.

## Zaroori Concepts

### Agent / Environment / Session
Teen main cheezein jo managed runtime deti hai: **Agent** configured worker hai, **Environment** wo sandbox/container hai jisme wo chalta hai, **Session** ek continuous run hai apni memory aur cost meter ke saath.

### Kya milta hai, kya jaata hai
Milta hai: easy scaling, isolation, kam operational kaam. Jaata hai: host pe deep control, kabhi tool versions ka control bhi. Cost active time se measure hoti hai.

### Self-hosted sandbox option
Agar zyada control chahiye ya compliance rules managed service pura nahi kar sakti, to waisa hi isolated environment khud bhi chala sakte ho.

### ~$0.08 per active session-hour, idle free
Course ke waqt ka concrete number. Zaroori baat ye hai ke paisa "active kaam" ka lagta hai, sirf configuration exist karne ka nahi.

### Kya chhodna padta hai
Teen cheezein, halki se bhaari: **visibility** (machine nahi, service ka event log dikhta hai), **custody** (data tumhare control se bahar chalta hai — kuch regulators ke liye ye deciding factor hai), **portability** (definition vendor ke shape mein likhi hoti hai, chhodna matlab rewrite karna, sirf move nahi).

## Exam Mein Ye Kyun Aayega?
Zyada tar production loops kisi na kisi managed runtime mein hi rehte hain. Trade-offs aur cost model exam mein clear hone chahiye.
