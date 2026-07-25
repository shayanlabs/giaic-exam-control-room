# 17. Part 6 — Keeping Human Control

## Aasan Zabaan Mein Samjho

Khud chalne wala loop powerful hota hai — but bina kisi control ke khud chalne wala loop seedha khatarnak hai. Socho computer raat bhar kaam kar raha hai aur tum so rahe ho — control kaun rakhega?

Ye part isi ki baat karta hai: feedback loops, paison ka asli hisaab, aur wo design choices jo insaan ko charge mein rakhti hain, chahe computer background mein akela kaam kar raha ho.

## Zaroori Concepts

### Teen feedback loops
Insaan ki involvement ke alag levels — ye system ko honest rakhte hain aur sahi goal ki taraf pointed rakhte hain.

### Token cost aur cadence
Loop kitni martaba chalta hai, iska cost par bohot bada asar padta hai. Same design $20/month bhi ban sakti hai aur $1,800/month bhi — depend karta hai loop kitni baar wake hota hai aur har baar kitna context load karta hai.

### Human in / on / out of the loop
- **In the loop**: har important step pe insaan ki zaroorat.
- **On the loop**: insaan goals set karta hai, results review karta hai, lekin har turn khud drive nahi karta.
- **Out of the loop**: system standing permissions ke saath chalta hai, sirf exceptions ke liye insaan ko bulaya jata hai.

### AI gravity
Ek successful system ka natural pull hota hai ke wo zyada se zyada kaam apne upar le le. Jaan bujh kar choose karo toh mast baat hai, lekin bina kisi decision ke apne aap phailta jaye toh khatra hai.

### Ng ka context advantage
Andrew Ng ka observation hai — jis taraf better context ho (data, process knowledge, evaluation), uska lasting advantage hota hai. Achi spines aur standing permissions isi idea ko amal mein laane ke tareeqe hain.

### Standing permissions
Wo actions jo loop har baar poochhe bina kar sakta hai, pehle se approved. Inhe carefully chuno aur time time pe review karte raho.

### Teen loops, teen speeds — worked example
Socho tumne agent ko bola ek bachay ke liye chota typing game bana do. **Coding loop** minutes mein ghoomta hai — agent game likhta hai, test karta hai, bugs fix karta hai jab tak tumhari instructions match na ho jayein — yehi wo loop hai jo is course ke six parts se banta hai. **Feedback loop** ghanton mein ghoomta hai — tum game khol ke try karte ho, decide karte ho buttons bade hone chahiye ya costumes unlock honi chahiye, phir instructions update karke agent se dobara banwate ho. **Outside loop** dinon mein ghoomta hai — asli log, dost, bachay, game actually use karte hain, aur unka react karna batata hai age kya theek karna hai. Ye teeno loops ek dusre ke andar baithe hote hain — fast loop khud chalta rehta hai, jabke dono slow loops ko tumhari zaroorat hoti hai, kyunke jaise Andrew Ng kehte hain, tumhare paas **context advantage** hai: tumhe pata hai ye kaun use karega aur "achha" kaisa lagta hai — agent ko ye nahi pata.

### In, on, ya out of the loop — industry ke exact words
Is course ke "human gate" se hat kar, poori duniya (AI safety papers, EU AI Act, bank compliance teams) isi idea ke liye teen fixed terms use karti hai, aur koi regulator ya buyer inhi exact words mein baat karega: **human in the loop** matlab har action se pehle insaan approve karta hai (zyada control, thora slow — ye turn-by-turn prompting ya khud human gate hai); **human on the loop** matlab system khud chalta hai jabke insaan dekhta rehta hai aur zaroorat par rok sakta hai (jaise ek Routine jo `claude/` branches par push karti hai jabke tum roz subah review karte ho); **human out of the loop** matlab koi dekh hi nahi raha, koi rok bhi nahi sakta — ye kabhi ek valid option ki tarah present nahi hota, ye seedha failure mode hai. Ek achi loop in teeno ko action ke hisaab se mix karti hai — subah wali triage loop safe fixes ke liye on-the-loop chalti hai, aur kisi risky cheez (jaise reviewer ka FAIL ya `main` mein final merge) ke waqt wapas in-the-loop mein aa jati hai.

## Exam Mein Ye Kyun Aayega?
Exam sirf ye nahi dekhega ke loop chalti hai ya nahi — ye bhi dekhega ke loop safe, affordable, aur human control mein rehti hai ya nahi.
