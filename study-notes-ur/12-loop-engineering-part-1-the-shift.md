# 12. Part 1 — The Shift

## Aasan Zabaan Mein Samjho

Kuch saal tak coding agents use karne ka tareeqa simple tha: tum instruction type karte, agent ek cheez karta, tum agli instruction type karte. Har turn par tum hi boss thay.

**Loop** ye cheez badal deta hai. Tum ek chota sa system banate ho jo khud kaam shuru kar sake, result check kare, likh de kya hua, aur decide kare aage kya karna hai. System khud agent ko prompt karta hai — tumhare bajaye.

Tumhara kaam khatam nahi hota, wo un do cheezon mein shift ho jata hai jo loop kabhi khud nahi kar sakta: 1) clearly batana tum kya chahte ho (intent), aur 2) jo ship hota hai uski zimmedari lena (accountability).

## Zaroori Concepts

### Prompting vs looping
Prompting matlab tum har turn par driving seat par ho. Looping matlab tum gaadi hi is tarah design karte ho ke wo road ke lambe hisson mein khud chal sake.

### Loop ke 6 parts
Complete loop mein chhe pieces hote hain. Chaar working layers banate hain: prompt, context, harness, aur khud loop. Paanchwa hai body of work. Chhata hai **spine** — wo memory jo ek run ko agle run se jodta hai.

### Do raaste
Ek hi loop shape banane ke do main tareeqe hain. Claude Code tumhe loop machinery zyada tar ready-made deta hai. OpenCode sirf worker deta hai aur baaki tum khud jodte ho. Shape wohi rehta hai.

### Small loop vs big loop
Small loop tight aur fast hota hai (aksar ek session ke andar). Big loop lamba chalta hai, bohot saare sessions ya schedule par, aur usko zyada strong memory (spine) chahiye hoti hai.

### Spine hi 6ta part hai
Aisi memory ke bagair jo ek run se agle run tak zinda rahe, tumhare paas asal loop nahi hota — sirf alag alag prompts ki ek series hoti hai jo baar baar bhool jati hai kya ho chuka hai.

### Chaar-layer stack, aur tumhara prompt ab kam kyun matter karta hai
Industry chaar layers se guzri, har layer takriban ek saal ke faasle par: pehle **prompt engineering** (tum kya alfaaz bhejte ho), phir **context engineering** (model ek turn mein kya kya dekhta hai), phir **harness engineering** (model ke ird gird ka code jo tools chalata aur errors handle karta hai — yahin small loop rehta hai), aur ab **loop engineering** (bahar wala cycle: system kis par kaam karta hai, kab shuru hota hai, khatam hone ka kaise pata chalta hai). Har layer pichli ko andar lapetti hai, jaise nested boxes, aur har layer ek alag tarah ki failure rokti hai — behtar prompt sirf prompt theek karta hai, koi prompt missing context, missing checker, ya schedule jo abhi bhi tum ho, usay theek nahi kar sakta. Isi liye akela acha prompt ab poora system nahi chala sakta — wo bas ek input hai bade stack ka.

### Small loop ki blind spot
Har agent ke andar ek chota "small loop" baitha hota hai: model ko context bhejo, jo tools mange wo chalao, results wapas do, dobara karo — code mein ye `while True: reply = model(context); if not reply.tool_calls: break` se zyada kuch nahi. Us `break` line ko dekho — small loop rukta hai jab **model khud faisla kare ke kaam khatam hai**. Koi cheez check nahi karti ke model sahi hai ya nahi. Ek aam failure ye hai ke agent file edit kar ke "Done! Sab theek ho gaya" likh de aur ruk jaye — bina tests chalaye. Isi liye loop engineering **outside stops** par zor deti hai jo model ki apni raye par depend nahi karte: koi checked condition (real test), koi limit (max tries), no-progress check, ya alag checker agent.

## Exam Mein Ye Kyun Aayega?

"Main prompt karta hoon" se "main wo system design karta hoon jo prompt karta hai" — ye shift poore course ki sabse badi skill change hai, aage ka sab kuch isi shift par khada hai.
