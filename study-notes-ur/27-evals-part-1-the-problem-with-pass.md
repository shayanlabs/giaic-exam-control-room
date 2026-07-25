# 27. Part 1 — The Problem with PASS

## Aasan Zabaan Mein Samjho

Ek normal test poochta hai: "Kya jawab exactly ye string hai?"
Ek **eval** poochta hai: "Kya kaam waqai real purpose ke liye kaafi acha hai?"

Test pass karna aur trustworthy hona — dono alag baatein hain. Aur is se bhi bura ye hai ke judge khud bhi aksar ek language model hota hai, is liye us mein wahi kamzoriyan ho sakti hain jo us system mein hain jinhe wo judge kar raha hai.

Socho ek exam mein ek student ne answer sheet mein sahi lafz likh diye lekin concept samjha hi nahi — wo test pass kar gaya lekin asal mein "acha student" nahi hai. Yehi farq test aur eval mein hai.

## Zaroori Concepts

### Test vs eval
- **Test**: exact match, brittle, aam tor par yes/no.
- **Eval**: rubric ya success criteria ke khilaf graded judgment. Ye ek sath kai dimensions dekh sakta hai.

### 3 depths
Tum alag alag levels par judge kar sakte ho:
- **Answer** — final output acha hai kya?
- **Actions** — kya sahi steps liye gaye?
- **Trace** — poori reasoning aur tool-use history sound hai kya?

### Judge bhi ek model hi hai
Is liye judge in cheezon se bhi affect ho sakta hai:
- **Leniency drift** — waqt ke sath zyada generous ban jata hai.
- **Self-preference** — apne style jaise dikhne wale answers ko pasand karta hai.
- **Surface bias** — fluent language se impress ho jata hai chahe substance ghalat ho.
- **Drift** — models ya prompts update hone par uska apna behavior badal jata hai.

### Worked example: wo depth jo mushkil fix pakadti hai
Socho agent ek failing test ko "fix" karta hai — real bug fix karne ki bajaye function ke andar seedha expected value hard-code kar deta hai. Depth 1 (answer) kehta hai PASS — tests green hain. Sirf Depth 2 (actions — asli diff parhna) dikhata hai ke ek constant seedha code mein likh diya gaya, aur yehi wo failure hai jo ek output-only eval mahine bhar tak miss karta rahega. Isi liye source jaan-boojh kar teen depths naam leta hai: **answer**, **actions**, aur **trace** — sasti cases ko sirf depth 1 chahiye, lekin jo cases tumhein waqai protect karti hain unhein depth 2 ya depth 3 par grade karna zaroori hai.

### Ek clean demo itna kam kyun prove karti hai
Source usi compounding math ki taraf ishara karta hai jo curriculum mein pehle aayi thi: ek loop jiske har step ka success rate 95% hai, wo sirf takreeban 36% baar ek 20-step run ko cleanly finish karta hai. Demo ek run hai, ek aise task par jo isliye chuna gaya kyunki wo demo mein achi lagti hai, kisi aise banda ke saamne jo ye chahta hai ke ye kaam kare — is liye ek clean demo aisi system se bhi aa sakti hai jo zyada tar real tasks mein fail hoti hai. Yehi asli farq hai jo ye note bata raha hai: demos convince karti hain, evals inform karti hain, tumhein dono chahiye lekin kabhi ye confuse na karo ke kaunsa kya kaam karta hai.

## Exam Mein Ye Kyun Aayega?
"Ye pass ho gaya" agent development ke sabse khatarnak phrases mein se ek hai. Exam mein ye samajhna zaroori hai ke sirf pass hona kaafi kyun nahi hai.
