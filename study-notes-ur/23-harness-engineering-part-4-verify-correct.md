# 23. Part 4 — Verify & Correct

## Aasan Zabaan Mein Samjho

Agent ko limit karna aur usay information dena kaafi nahi hai. Ye bhi check karna zaroori hai ke kaam asal mein sahi hua hai — aur agar nahi hua toh kya karna hai, uska plan bhi chahiye.

Yehi harness ka "Verify & Correct" kaam hai.

## Zaroori Concepts

### Hooks
Agent ki zindagi ke wo khaas moments jahan tum apna khud ka code chala sakte ho: tool use hone se pehle, tool use hone ke baad, jab agent rukna chahta hai, waghera.

### Typed output
Agent se structured jawab lena (free-form text nahi) taake computer usay reliably check kar sake.

### Recovery
Failure ke baad kya hota hai. Achhe harness ke paas jaan-boojh kar bane recovery paths hote hain, sirf rukna ya blindly dobara try karna nahi.

### The ratchet
Ek pattern jo system ki measured quality ko sirf same rehne ya behtar hone deta hai — chupke se kharab hone nahi deta.

### Chaar failure classes
Problems ko group karne ka useful tareeqa:
- Context failure (agent ko kuch pata nahi tha jo zaroori tha)
- Constraint failure (agent ne kuch kar diya jo usay karne nahi dena chahiye tha)
- Verification failure (check khud ghalat tha ya missing tha)
- Planning failure (high-level plan hi kharab tha)

### PreToolUse / Stop gate (exit code 2)
Ek hard-stop mechanism. Ek khaas exit code return karke tool call block ki ja sakti hai ya agent ko poori tarah rok diya ja sakta hai.

### PostToolUse feedback deta hai
Tool chalne ke baad, result (ya uska summary) wapas diya jata hai taake agent aur harness dono decide kar sakein age kya karna hai.

### Typed output — ek verdict jo actually parse ho sake
Ek checker jo free text mein "PASS" ya "FAIL" bolta hai, us raat toot jayega jab wo bolega "Ye mostly pass hai, though mujhe kuch shakook hain..." — loop ya toh isay galat samjhega ya ruk jayega. Fix ye hai: ek fixed JSON shape maango, aur har field ko code se validate karo trust karne se pehle, misaal: `{"verdict": "PASS", "reasons": [], "risk": "low"}`, jo `jq` jaise tool se uski *allowed values* ke against check ho — sirf present hona kaafi nahi. Ek lazy validator jo sirf `.verdict` ka hona check kare, khushi khushi `{"verdict": "MAYBE"}` accept kar lega; ek real validator isay reject karega chahe JSON perfectly well-formed ho, kyunke `MAYBE`, `PASS` ya `FAIL` nahi hai. Jab verdict validate na ho paye, loop hamesha retry nahi karta ya guess nahi karta — wo **escalate** karta hai, likh deta hai "reviewer output unparseable: needs a human" aur aage badh jata hai. Ye wahi checker ladder hai loop engineering wala, bas iski sabse kamzor rung ko mazboot kar diya gaya hai: "bar wali rubric" ab ban gayi hai "bar wali rubric, aisi shape mein jo program padh sake."

### The ratchet — chaar failure classes, chaar ghar
Correction ki asal discipline yehi hai: jab agent galti kare, sirf kaam fix mat karo — harness ko change karo taake wo galti impossible ho jaye, phir usay dobara kabhi mat socho. Har failure inhi chaar classes mein se ek mein fit hoti hai, har ek ka apna fix surface hai: **context failure** ("usay pata nahi tha") rules file, skill, ya tool description mein fix hoti hai; **constraint failure** ("usne kuch aisa kar diya jo karna hi nahi chahiye tha") permission rule, sandbox, ya branch fence se fix hoti hai; **verification failure** ("bura kaam bhi done keh diya gaya") hook, required CI check, ya typed output se fix hoti hai; aur **planning failure** ("sahi pieces, galat order") ek level upar fix hoti hai, loop ke structure mein — chote tasks, subagent splits, step caps. Practice yehi hai: har failure ke baad paanch minute ka review — class ka naam lo, fix usi class ke surface mein likho. Do failures ka same shape hona impossible hona chahiye — agar repeat dikhe, matlab pehli baar galat class di thi.

## Exam Mein Ye Kyun Aayega?
Verification hi "acha lag raha hai" ko "hum jaante hain ke acha hai" mein badalti hai. Iske bina kisi bhi non-trivial loop ke output par bharosa nahi kiya ja sakta.
