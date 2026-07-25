# 13. Part 2 — The Heartbeat

## Aasan Zabaan Mein Samjho

Heartbeat wo cheez hai jo loop ko jagati hai aur naya run shuru karti hai.

Heartbeat na ho to loop kabhi shuru hi nahi hota. Kharab heartbeat ho to ya to kabhi rukta nahi, ya bina wajah paisa kharch karta rehta hai.

## Zaroori Concepts

### Heartbeat ki chaar qisam
- **In-session**: chalta hai jab tak tum dekh rahe ho. Jab tum abhi build aur test kar rahe ho tab useful hai.
- **Conditional** (`/goal` wala style): tab tak chalta hai jab tak success condition sach na ho jaye.
- **Scheduled** (Routines): clock par fire hota hai — har subah, har ghante, waghera.
- **Event-driven**: bahar kuch hone par fire hota hai (naya pull request, naya ticket, webhook).

### Teen stop conditions
Achhe loop ko rukne ke saaf tareeqe chahiye:
1. **Success** — goal poora ho gaya.
2. **Limit** — max steps, max time, ya max paisa khatam ho gaya.
3. **No-progress check** — chakkar kaat raha hai, koi real progress nahi ho rahi.

### Ralph loop
Ek named pattern hai kuch khaas persistent, goal-seeking loops ke liye jo tab tak kaam karte rehte hain jab tak goal sach mein poora na ho jaye.

### Doom loop
Ye khatarnak pattern hai jahan loop chalta rehta hai, tokens kharch karta rehta hai, aur ya to kuch useful nahi karta ya cheezein aur bigar deta hai. No-progress check hi iska main defense hai.

### Timer kahan rehta hai
Loop kabhi ek single action nahi hota — ye hai "ye karo, ruko, phir karo" — is liye kuch cheez beats ke darmiyan jagi rehni chahiye. **In-session heartbeat** (jaise Claude Code ka `/loop`) apna timer tumhare khule terminal session ke andar rakhta hai; session band karo, timer khatam ho jata hai, kyunke tumhara kuch bhi chalta hua nahi bacha. **Scheduled task ya Routine** timer ko session se bahar ek aise scheduler par shift kar deta hai jo kabhi soti nahi (khud ka machine ka cron, ya cloud Routine ke liye Anthropic ke servers) — har tick par ek bilkul naya, chota run launch hota hai, khatam hota hai, band ho jata hai. Yehi asal farq hai "main hoon to dekh lo" aur "main so raha hoon tab bhi chalao" mein.

### Sahi heartbeat kaise chuno: khatam hota hai ya repeat hota hai?
Koi bhi heartbeat pakarne se pehle apne task se ek sawal poocho. Agar task **khatam** hota hai aur koi command "end" prove kar sakta hai (jaise "tests pass"), conditional loop use karo — abhi shuru hota hai aur khatam hone tak chalta hai. Agar task **repeat** hota hai, schedule ya event use karo. Agar task **sirf ek dafa** hona hai, to loop banao hi mat — ek normal one-turn session zyada tar kaam ke liye sahi tool hai. Ek concrete misal: Claude Code Routines ke launch-time daily caps taqreeban 5 runs Pro par, 15 Max par, aur 25 Team/Enterprise par the, aur default mein wo sirf `claude/*` naam ki branches par push karte hain — kabhi seedha `main` par nahi — taake bina dekhe chalne wala kaam bhi din 1 se safe rahe.

## Exam Mein Ye Kyun Aayega?
Bharosemand heartbeat aur clear stop conditions ke bagair loop ya to soya rehta hai ya khatarnak ban jata hai. Exam mein options aur failure modes dono pata hone chahiye.
