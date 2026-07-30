# 9. FDE AF Model I — the five layers

## Aasan Zabaan Mein Samjho

Ek line mein poori baat: neeche mehngi cheez ek hi baar banao, phir wo hamesha reuse hoti rahe — aur upar individual log customer-specific kaam par khud banate hain aur paisa kamate hain.

## Zaroori Concepts

### Layer 0 — equipment factory (ek baar banta hai, phir kabhi nahi)
Chaar asal, pehle se installed aur chalti hui cheezein:

- **Markdown + Docusaurus** — plain text likho, khud website ban jaati hai
- **Postgres + pgvector** — aisa database jo matlab se search kare, sirf exact lafzon se nahi
- **MCP** — AI agent ke information maangne aur lene ka standard tareeqa
- **Better Auth** — check karta hai kaun kya dekh sakta hai

Pizza wali example: oven, fridge, aur POS machine pehle se laga kar wired hain. Har naye restaurant ke liye ye dobara nahi banaye jaate.

Ye raw technical machinery deta hai. Layer 1 banane wale isay use karte hain. Isme koi asal content ya subject-matter nahi hota.

### Layer 1 — recipe management system (reusable kernel)
Wahi chaar tools mil kar ek working, reusable system ban jaate hain — jo kisi bhi Markdown content ko searchable aur trustworthy cheez mein badal sakta hai. Isay **kernel** kehte hain — kernel ka design sirf ek hi hai.

Phir koi bhi apna content isme daal kar ek **instance** bana sakta hai: is book ka content ek instance hai, kisi ka accounting rulebook doosra instance, kisi client ka manual teesra.

Pizza wali example: ek poori wired, chalti hui kitchen (kernel) hai, lekin abhi menu decide nahi hua. Pizza Hut ka menu daalo — ek instance. Domino's ka menu daalo — doosra instance. Kitchen wahi, content alag.

Ye kernel aur generic instances deta hai. Layer 2 banane wale, Layer 3 verticals, aur apna trustworthy content system chahne wala koi bhi client isay use karta hai.

### System of Record — teen alag scopes
"System of Record" ka lafz loosely use hota hai, isliye ye teen cheezein alag rakho:

- **Machinery** — raw tools (Layer 0)
- **Kernel** — wo ek assembled, reusable system (Layer 1)
- **Instance** — ek khaas content-filled copy (is book ka version, accounting wala version, ek client ka manual)

Ek kernel, bohot saari instances — bohot saare kernels nahi.

### Layer 2 — culinary school aur kitchen consultants
Reusable teaching aur building tools, do products mein pack kiye gaye: **Zia Tutor AI** poora method sikhata hai, aur **Zia Developer AI** cheezein banane mein madad karta hai.

Pizza wali example: ek hi culinary school, same curriculum — chahe baad mein pizza banao ya burger.

Ye generic learning aur building components deta hai. Aaj ke learners aur kal ke Layer 3 (jo inhi components ko reuse karta hai, badalta nahi) isay use karte hain.

### Layer 3 — asal franchise brand (jaise "Pizza Hut")
Ab baat profession-specific ho jaati hai. Ek profession ke liye — accounting, healthcare, waghera — teen cheezein saath banayi jaati hain:

1. **Domain System of Record** — us profession ke asal rules (tax law, medical protocol) jo Layer 1 kernel mein load kiye jaate hain
2. **Domain expert twin** — ek AI tutor jo us khaas expert ki awaaz mein sikhata hai
3. **Domain builder** — wo tool jo us profession ke AI workers banata hai, compliance built-in ke saath

Domain SoR ke andar, knowledge teen shapes mein bantti hai:

- **Corpus** — jo cheezein AI ko dhoond kar proof ke taur par cite karni hain (koi khaas regulation)
- **Map** — ek chhoti guide jo batati hai kya maujood hai aur kab check karna hai (onboarding se pehle KYC kabhi skip na karo)
- **Reflexes** — poora procedure jo ek saath handover hota hai, tukdon mein search nahi hota (fixed monthly-closing checklist)

Har profession ka sirf ek domain builder hota hai, jo us field ki har company share karti hai — kabhi bhi har customer ke liye alag fork nahi hota. Yehi **promotion law** hai: agar wahi fix baar baar clients mein repeat ho raha hai, to wo shared builder mein wapas fold ho jaata hai taake sab ko fayda ho, iske bajaye ke har consultant apna alag diverging version hamesha maintain karta rahe.

Ye har vertical ke liye trio deta hai. Us field ke professionals aur unke liye deploy karne wale FDEs isay use karte hain.

### Layer 4 — ek asal restaurant, ek city mein, ek owner ke zariye chalta hua
Asal kaam, ek paying company ke liye, is proof ke saath ke ye waqai kaam kar gaya. Building shuru hone se pehle do fixed points tay kiye jaate hain:

- **Contract of success** — baseline (abhi ki performance, jaise "4 ghante per file") plus target ("40 minute per file") plus acceptance criteria ("pehli koshish mein 95% sahi")
- **Proof in production** — business KPIs behtar hue, log ne waqai adopt kiya, aur agent evaluations pass hui — teeno zaroori hain, sirf ek nahi

Do alag roles ye karte hain: **Outcome Architect** business problem, workflow, aur outcome ka malik hota hai; **FDE** technical build, integration, aur evaluation ka malik hota hai. Chhote jobs mein ek hi banda dono role nibha sakta hai.

Ye ek company ke liye proven business outcome deta hai. Us company ki asal human aur AI teams isay use karti hain.

### Poora order jisme cheezein hoti hain (aksar test hota hai)
Expert commit karta hai, phir ek thin slice banta hai (ek outcome, poori tarah complete), phir sponsor milta hai, phir baseline measure hoti hai, phir contract of success sign hota hai, phir engagement build aur deploy hota hai, phir proof dikhaya jaata hai, phir System of Record "thicker" hota jaata hai.

Yaad rakho: ye customer se shuru nahi hota. Ye ek expert aur ek complete slice of work se shuru hota hai — yehi sponsor conversation ko create karta hai.

### Ayesha ka safar
Layer 0 pehle se chal raha hota hai jab wo shuru karti hai. Layer 1: wo apni khala ka accounting manual ek searchable system mein load karti hai. Layer 2: wo Zia Tutor AI aur Zia Developer AI se training leti hai. Layer 3: wo apni khala, jo asal expert hain, ke saath mil kar accounting trio banati hai. Layer 4: usay Chicago mein ek sponsor milta hai, "4 ghante se 40 minute" contract tay hota hai, wo Digital FTE banati hai, aur production mein result prove karti hai.

## Exam Mein Ye Kyun Aayega?
Ye poori technology aur business ka big picture hai. Almost har doosra topic inhi layers mein se kisi ek ka detail hai.
