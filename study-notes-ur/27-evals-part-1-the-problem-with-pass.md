# 27. Part 1 — The Problem with PASS

## Aasan Zabaan Mein Samjho

Normal test poochta hai: "kya jawab exactly ye string hai?"
**Eval** poochta hai: "kya kaam asal purpose ke liye sach mein achha hai?"

Test pass karna aur trustworthy hona — do alag baatein hain. Aur baat aur bigarti hai jab judge khud ek language model hota hai — toh usme wahi weaknesses ho sakti hain jo jis system ko wo judge kar raha hai usme hain.

## Zaroori Concepts

### Test vs eval
- **Test**: exact match, brittle, usually yes/no.
- **Eval**: rubric ya success criteria ke against graded judgment. Ek saath kai dimensions dekh sakta hai.

### 3 depths
Alag levels par judge kar sakte ho:
- **Answer** — kya final output achha hai?
- **Actions** — kya sahi steps liye gaye?
- **Trace** — kya poora reasoning aur tool-use history sound hai?

### Judge bhi ek model hai
Isliye judge in cheezon se pareshan ho sakta hai:
- **Leniency drift** — waqt ke saath zyada generous ho jata hai.
- **Self-preference** — apne jaisi style wale answers ko pasand karta hai.
- **Surface bias** — fluent language se impress ho jata hai chahe substance ghalat ho.
- **Drift** — models ya prompts update hone par khud ka behavior badal jata hai.

### Worked example — wo depth jo tough fix pakarta hai
Socho agent ek failing test ko "fix" karta hai — real bug fix karne ki jagah expected value ko seedha function mein hardcode kar deta hai. Depth 1 (answer) bolta hai PASS — tests green hain. Sirf Depth 2 (actions — asal diff padhna) dikhata hai ke ek constant seedha code mein daal diya gaya — yehi wo failure hai jo output-only eval ek mahine tak miss kar sakta hai. Isi liye source jaan bujh kar teen depths naam deta hai: **answer**, **actions**, aur **trace** — sasti cases ko sirf depth 1 chahiye, lekin jo cases asal mein tumhe bachati hain unhe depth 2 ya depth 3 grade karna zaroori hai.

### Ek clean demo itna kam kyun proof karta hai
Source curriculum ke wahi compounding math wapas dikhata hai: ek loop jiske har step 95% waqt kaamyab hota hai, 20-step run sirf takreeban 36% waqt saaf khatam karta hai. Demo ek hi run hai, aise task par jo demo achha karta hai isliye chuna gaya, aur koi ummeed lagaye baitha dekh raha hai — isliye ek clean demo aise system se bhi aa sakta hai jo zyada tar real tasks mein fail hota hai. Yehi asal farak hai jo ye note bata raha hai: demos convince karte hain, evals inform karte hain — dono chahiye, lekin kabhi confuse mat karo kaunsa kaunsa hai.

## Exam Mein Ye Kyun Aayega?
"Ye pass ho gaya" agent development mein sabse khatarnak phrases mein se ek hai. Exam chahta hai tumhe pata ho ke sirf pass hona kaafi kyun nahi.
