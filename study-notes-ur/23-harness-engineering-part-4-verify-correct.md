# 23. Part 4 — Verify & Correct

## Aasan Zabaan Mein Samjho

Sirf agent ko limit karna aur information dena kaafi nahi hai. Tumhe ye bhi check karna hai ke kaam waqai sahi hua hai, aur jab sahi nahi hua to uska plan bhi tumhare paas hona chahiye. Yehi harness ka "Verify & Correct" wala kaam hai.

Socho tum ek teacher ho jo student ka homework check kar rahe ho — sirf "kiya ya nahi kiya" nahi dekhte, sahi tareeke se kiya ya nahi wo dekhte ho, aur agar ghalat hai to usay bataate ho kaise theek karein. Harness bhi yehi role nibhaata hai agent ke liye.

Sabse important cheez ye hai ke verification khud bhi reliable honi chahiye — agar checker khud confuse ho jaye ya galat jawab de, to poora system dhoka kha sakta hai.

## Zaroori Concepts

### Hooks
Agent ki zindagi ke khaas moments jahan tum apna khud ka code chala sakte ho: kisi tool ke chalne se pehle, chalne ke baad, jab agent rukna chahta hai, waghera.

### Typed output
Agent se structured jawab lena (free-form text nahi) taake ek computer usay reliably check kar sake.

### Recovery
Failure ke baad kya hota hai. Achi harnesses ke paas deliberate recovery paths hote hain, sirf rukna ya blindly dobara try karna nahi.

### The ratchet
Ek pattern jo system ki measured quality ko sirf same rehne ya behtar hone deta hai — chupke se kabhi bhi worse nahi hone deta.

### Char failure classes
Problems ko group karne ka useful tareeka:
- Context failure (agent ko kuch aisa pata nahi tha jo zaroori tha)
- Constraint failure (agent ne kuch aisa kar diya jo usay karna hi nahi chahiye tha)
- Verification failure (check khud galat tha ya missing tha)
- Planning failure (high-level plan hi ghalat tha)

### PreToolUse / Stop gate (exit code 2)
Ek hard-stop mechanism. Ek khaas exit code return karke tool call ko block kiya ja sakta hai ya agent ko poori tarah rok diya ja sakta hai.

### PostToolUse feedback deta hai
Tool chalne ke baad, result (ya uska summary) wapas diya jata hai taake agent aur harness dono decide kar sakein age kya karna hai.

### Typed output: ek verdict jise tum waqai parse kar sako
Ek checker jo free text mein "PASS" ya "FAIL" jawab deta hai, wo us raat toot jayega jab wo jawab dega "Ye mostly pass hai, magar mujhe kuch shak hai..." — loop ya to usay ghalat parhega ya stall ho jayega. Fix ye hai: ek fixed JSON shape maango aur har field ko code se validate karo trust karne se pehle, jaise `{"verdict": "PASS", "reasons": [], "risk": "low"}`, aur is ko `jq` jaise tool se uski *allowed values* ke khilaf check karo — sirf field ke hone ka check nahi. Ek aalasi validator jo sirf ye check kare ke `.verdict` maujood hai, wo khushi se `{"verdict": "MAYBE"}` accept kar lega; ek asli validator isay reject karega chahe JSON perfectly well-formed ho, kyunki `MAYBE` na "PASS" hai na "FAIL". Jab verdict validate na ho sake, loop hamesha ke liye retry nahi karta ya guess nahi karta — wo **escalate** karta hai, likhta hai "reviewer output unparseable: needs a human" aur age badh jata hai. Ye loop engineering ki checker ladder hai, jiski sabse kamzor rung ko mazboot kiya gaya hai: "ek bar ke sath rubric" ban gaya "ek bar ke sath rubric, aisi shape mein jo program parh sake."

### The ratchet: char failure classes, char ghar
Correction ka core discipline: jab agent ghalti kare, sirf kaam theek mat karo — harness ko badal do taake wo ghalti namumkin ho jaye, phir usay dobara kabhi mat socho. Har failure in char classes mein se ek mein fit hoti hai, har ek ka apna fix surface hai: **context failure** ("usay pata nahi tha") rules file, skill, ya tool description mein fix hoti hai; **constraint failure** ("usne aisa kuch kar diya jo usay kabhi karna hi nahi chahiye tha") permission rule, sandbox, ya branch fence se fix hoti hai; **verification failure** ("bura kaam done keh diya gaya") hook, required CI check, ya typed output se fix hoti hai; aur **planning failure** ("sahi pieces, ghalat order") ek level upar fix hoti hai, loop ke structure mein — chhote tasks, subagent splits, step caps. Practice ye hai: har failure ke baad paanch minute ka review karo, class ka naam lo, aur fix us class ke apne surface mein likh do. Do failures jo same shape ki hon, namumkin honi chahiye — agar repeat dikhe, to pehli wali ghalat classify hui thi.

## Exam Mein Ye Kyun Aayega?
Verification hi wo cheez hai jo "acha laga" ko "hum jaante hain acha hai" mein badalti hai. Iske bagair kisi bhi non-trivial loop ke output par bharosa nahi kiya ja sakta.
