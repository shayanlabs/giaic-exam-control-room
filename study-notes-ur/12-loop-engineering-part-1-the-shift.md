# 12. Part 1 — The Shift

## Aasan Zabaan Mein Samjho

Pichle kuch saal coding agents ka tareeqa seedha tha: tum instruction type karo, agent ek cheez kare, tum agli instruction type karo. Har turn par boss tum hi the.

Ab **loop** ye poora pattern badal deta hai. Tum ek chota sa system banate ho jo khud kaam shuru kar sake, result check kare, likhe ke kya hua, aur khud decide kare aage kya karna hai. System khud agent ko prompt karta hai, tumhari jagah.

Tumhara kaam khatam nahi hota — bas do cheezon par shift ho jata hai jo loop kabhi khud nahi kar sakta:
1. Saaf saaf batana tumhe kya chahiye (intent).
2. Jo bhi ship ho, uski zimmedari lena (accountability).

## Zaroori Concepts

### Prompting vs looping
Prompting matlab tum har turn par driving seat par ho. Looping matlab tum aisi gaari design karte ho jo lambe raste khud chal sake.

### Loop ke 6 hisse
Ek poore loop mein 6 parts hote hain. Char parts working layers banate hain: prompt, context, harness, aur loop khud. Panchwa hai kaam ka body. Chatha hai **spine** — wo memory jo ek run ko agle run se jorti hai.

### Do raste
Ek hi shape ka loop banane ke do tareeqe hain. Claude Code loop ki machinery zyada ready-made deta hai. OpenCode sirf worker deta hai, baaki tum khud jorte ho. Shape dono mein wahi rehta hai.

### Chota loop vs bara loop
Chota loop tight aur fast hota hai (aksar ek hi session ke andar). Bara loop lamba chalta hai, kai sessions ya schedule par, aur usay stronger memory (spine) chahiye hoti hai.

### Spine hi 6th part hai
Jab tak memory ek run se doosre run tak zinda nahi rehti, tumhare paas asal loop nahi — sirf alag alag prompts ki lambi line hai jo baar baar bhool jati hai kya ho chuka.

### Char-layer stack, aur ab prompt itna important kyun nahi
Industry char layers se guzri hai, taqreeban har saal ek: pehle **prompt engineering** (tum jo alfaz bhejte ho), phir **context engineering** (jo kuch model ek turn mein dekhta hai), phir **harness engineering** (model ke ird-gird ka code jo tools chalata aur errors handle karta hai — yahin chota loop rehta hai), aur ab **loop engineering** (bahar wala cycle: system kis par kaam karta hai, kab shuru hota hai, kaise pata chalta hai khatam hua). Har layer pichli ko lapet leti hai, jaise ek dabbe ke andar dabba, aur har layer alag tarah ki galti rokti hai — behtar prompt sirf prompt theek karta hai, lekin koi prompt missing context, missing checker, ya schedule jo abhi bhi tum ho, usay bacha nahi sakta.

### Chote loop ka blind spot
Har agent ke andar ek chota "small loop" baitha hota hai: context model ko bhejo, jo tools maange chalao, results wapas do, dobara karo — code mein bas itna sa: `while True: reply = model(context); if not reply.tool_calls: break`. Us `break` line ko dekho — chota loop tab rukta hai jab **model khud faisla kare ke kaam khatam hai**. Koi ye check nahi karta ke model sahi bhi hai ya nahi. Ek aam ghalti: agent file edit karta hai, likhta hai "Done! Sab theek ho gaya," aur ruk jata hai — tests chalaye bagair hi. Isi liye loop engineering **outside stops** par zor deti hai jo model ki apni raye par depend nahi karte: ek checked condition (real test), ek limit (max tries), no-progress check, ya ek alag checker agent.

## Exam Mein Ye Kyun Aayega?
"Main prompt karta hoon" se "main wo system design karta hoon jo prompt karta hai" — ye poore course ka sab se bara skill shift hai. Aage har topic isi shift ko samjhe hue hone par depend karta hai.
