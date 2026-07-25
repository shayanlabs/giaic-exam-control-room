# 17. Part 6 — Keeping Human Control

## Aasan Zabaan Mein Samjho

Aisa loop jo khud chalta rahe, wo bohot powerful cheez hai. Lekin agar wahi loop bina kisi insaani control ke chalta rahe, to wo khatarnak ban jata hai. Ye part isi baat par hai — kaise feedback loops, paison ki asliyat, aur design ke faisle mil kar ye yaqeeni banate hain ke jab computer tumhare sote waqt kaam kar raha ho, tab bhi control insaan ke haath mein rahe.

Socho tum ek car cruise control par chala rahe ho — car khud speed maintain karti hai, lekin steering wheel abhi bhi tumhare haath mein hai. Yehi soch loop engineering mein bhi honi chahiye: automation chale, lekin steering insaan ke paas rahe.

Cost ka pehlu bhi bohot important hai — loop kitni martaba chalta hai, ye seedha paise par asar dalta hai. Same design mahine ka $20 bhi ho sakti hai aur $1,800 bhi, sirf is baat par ke wo kitni baar jaagti hai aur har baar kitna context load karti hai.

## Zaroori Concepts

### Teen feedback loops
Insaan ki involvement ke different levels jo system ko honest aur sahi goals ki taraf rakhte hain.

### Token cost aur cadence
Loop jitni baar chalta hai, cost utni hi zyada badhti hai. Wakeup frequency aur context load dono milkar mahine ka bill decide karte hain.

### Human in / on / out of the loop
- **In the loop**: har important step par insaan zaroori hai.
- **On the loop**: insaan goals set karta hai aur results review karta hai, lekin har turn khud nahi chalata.
- **Out of the loop**: system ke paas standing permissions hain aur sirf exceptions par insaan ko bulata hai.

### AI gravity
Ek successful system ka natural pull hota hai ke wo zyada se zyada kaam apne upar le le. Jab tum ye jaan-boojh kar choose karo to acha hai, lekin agar ye bina kisi decision ke apne aap badhta jaye to khatarnak hai.

### Ng ka context advantage
Andrew Ng ka observation ke jis side ke paas behtar context ho (data, process knowledge, evaluation), uska advantage lambe waqt tak rehta hai. Achi spines aur standing permissions isi idea ko practice mein laane ka tareeka hain.

### Standing permissions
Wo actions jo loop bina baar baar poochhe kar sakta hai — pre-approved hain. Inhe soch samajh kar choose karna chahiye aur waqt waqt par review karna chahiye.

### Teen loops, teen speeds — worked example
Socho tum agent ko ek bache ke liye chota typing game banane ko kehte ho. **Coding loop** minutes mein ghoomta hai: agent game likhta hai, test karta hai, bugs fix karta hai jab tak tumhari instructions match na ho jaye — yehi wo loop hai jo iss course ke six parts se banaya. **Feedback loop** ghanton mein ghoomta hai: tum game khol kar khelte ho, decide karte ho buttons bade hone chahiye ya costumes unlock honi chahiye, instructions update karte ho, agent dobara banata hai. **Outside loop** din mein ghoomta hai: real log — dost, bacha — game istemal karte hain, aur unka react karna tumhein batata hai age kya fix karna hai. Ye teeno loops ek dusre ke andar nested hain, tez loop khud chalta hai jab ke do slow loops tumhein chahiye — kyunki Andrew Ng ke alfaaz mein, tumhare paas **context advantage** hai: tum jaante ho ye kaun use karega aur "acha" kaisa lagta hai, agent ko ye nahi pata.

### In, on, ya out of the loop — industry ke exact alfaaz
Is course ke "human gate" se hat kar, bahar ki duniya (AI safety papers, EU AI Act, bank compliance teams) isi idea ke liye teen fixed terms use karti hai jo regulator ya buyer bilkul precisely use karega: **human in the loop** matlab har action lagu hone se pehle insaan approve karta hai (zyada control, dheema — ye turn-by-turn prompting ya khud human gate hai); **human on the loop** matlab system khud kaam karta hai jab ke insaan dekh raha hai aur beech mein rok sakta hai (koi Routine `claude/` branches par push kar rahi hai jab tum roz subah review karte ho); **human out of the loop** matlab koi bhi dekh nahi raha aur koi intervene bhi nahi kar sakta — ye kabhi bhi ek valid third option ke tor par nahi dikhaya jata, ye failure mode hai. Ek acha loop har action ke hisaab se in cheezon ko mix karta hai — morning-triage loop safe fixes ke liye on-the-loop chalta hai aur risky cheezon ke liye wapas in-the-loop chala jata hai, jaise reviewer ka FAIL ya `main` mein final merge.

## Exam Mein Ye Kyun Aayega?
Exam sirf ye nahi dekhta ke loop chal raha hai ya nahi — ye dekhta hai ke loop safe, affordable, aur insaan ke control mein hai ya nahi.
