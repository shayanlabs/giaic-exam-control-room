# 13. Part 2 — The Heartbeat

## Aasan Zabaan Mein Samjho

Heartbeat wo cheez hai jo loop ko jagati hai aur naya run shuru karti hai. Heartbeat ke bagair loop kabhi shuru hi nahi hota. Kharab heartbeat ke saath wo ya to kabhi rukta hi nahi ya bina wajah paisa kharch karta rehta hai.

## Zaroori Concepts

### Heartbeat ki chaar qisamein
**In-session**: tumhare dekhte dekhte chalta hai, jab tum abhi build aur test kar rahe ho tab useful hota hai. **Conditional** (`/goal` style): tab tak chalta hai jab tak success condition sach na ho jaye. **Scheduled** (Routines): clock par fire hota hai — har subah, har ghante. **Event-driven**: jab bahar kuch ho jaye tab fire hota hai (naya pull request, naya ticket, webhook).

### Teen stop conditions
Achhe loop ko rukne ke saaf tareeqe chahiye: 1) **Success** — goal poora ho gaya. 2) **Limit** — max steps, max time, ya max paisa khatam. 3) **No-progress check** — loop chakkar laga raha hai aur koi asal progress nahi ho rahi.

### Ralph loop
Ek naam diya gaya pattern hai kuch persistent, goal-seeking loops ke liye jo tab tak chalte hain jab tak goal sach mein poora na ho.

### Doom loop
Khatarnak pattern jahan loop chalta rehta hai, tokens kharch karta hai, aur ya to kuch useful nahi karta ya cheezein aur bigaad deta hai. No-progress check hi iske khilaf sabse badi defense hai.

### Timer kahan rehta hai
Loop kabhi ek hi action nahi hota — ye "ye karo, ruko, dobara karo" hota hai, is liye kuch beats ke darmiyan jaaga rehna chahiye. **In-session heartbeat** (jaise Claude Code ka `/loop`) apna timer tumhare khule terminal session ke andar rakhta hai — session band karo to timer bhi khatam, kyunke tumhara kuch bhi chalta nahi rehta. **Scheduled task ya Routine** timer ko session se **bahar** ek scheduler par le jata hai jo kabhi nahi sota (tumhare apne machine par cron, ya cloud Routine ke liye Anthropic ke servers) — har tick par ek bilkul naya short-lived run start hota hai, poora hota hai, aur band ho jata hai. Yehi asal farq hai "mere hote hue ye dekho" aur "mere sote hue ye chalao" mein.

### Sahi heartbeat chunna: khatam hota hai ya dohrata hai?
Koi bhi heartbeat pakadne se pehle task ke baare mein ek sawal poochho. Agar task **khatam hota hai** aur koi command us khatme ko prove kar sakti hai (jaise "tests pass"), conditional loop use karo — wo abhi shuru hota hai aur khatam hone tak chalta hai. Agar task **dohrata hai**, schedule ya event use karo. Agar task **sirf ek dafa hota hai**, loop bilkul mat banao — zyada tar kaam ke liye ek normal one-turn session hi sahi tool hai. Scheduled option ki ek concrete misal: Claude Code Routines ke launch-time daily caps takriban 5 runs Pro par, 15 Max par, aur 25 Team/Enterprise par thay, aur default se ye sirf `claude/*` naam ki branches par push kar sakte hain — kabhi seedha `main` par nahi — taake bina attend kiya kaam din ek se hi safe rahe.

## Exam Mein Ye Kyun Aayega?

Reliable heartbeat aur saaf stop conditions ke bagair loop ya to so raha hota hai ya khatarnak hota hai — exam mein options aur failure modes dono poochhe jayenge.
