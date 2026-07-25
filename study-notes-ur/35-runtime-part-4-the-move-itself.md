# 35. Part 4 — The Move Itself

## Aasan Zabaan Mein Samjho
Dekho, ek chalta-phirta loop utha kar naye ghar shift karna — jitna aasan sunta hai utna hai nahi. Achi cheezein, jaise discipline aur good ideas, tumhare saath chali aati hain. Lekin concrete mechanics — file paths, hooks, credential setup — usually dobara banane padte hain. Aur sabse important: sirf isliye ke loop laptop pe safe tha, naye runtime mein bhi safe hoga ye guarantee nahi hai. Trust dobara kamana padta hai, transfer nahi hoti.

To sawal ye hai: suitcase mein kya rakhna hai, aur kya peechhe chhod dena hai?

## Zaroori Concepts

### Suitcase test
Jo saath aana chahiye: spec (job kya hai, "done" ka matlab kya hai), rubric aur uske anchors, golden set (har case ki `origin` line aur baseline ke saath), ratchet log (pakde gaye failures ki list), maker-checker split, aur human gate. Jo peechhe chhoot jaata hai: CLI flags, output formats, file paths, session state, ek runtime ke API pe likha code, purane ghar ke cost assumptions.

### Trust dobara kamai jaati hai, transfer nahi hoti
Laptop pe safe hona naye runtime mein safety guarantee nahi deta. Dobara validate karna zaroori hai.

### Discipline travel karti hai, mechanics rebuild hoti hain
Maker-checker idea, spine concept, stop conditions — ye travel karte hain. Exact hooks, file paths, credential injection — ye usually dobara banane padte hain.

### Arrival protocol
Naye ghar mein pahunch kar ye sequence follow karo:
1. Poora rule set, category ke hisaab se organize kiya hua.
2. Quality bars wahi rakho — "sirf move ke liye" standard neeche mat lao.
3. Probation period — extra monitoring ke saath, full trust milne se pehle.

### Ek "regression" jo asal mein suitcase bug tha
Ek move Home 2 pe hua, score 35/36 se 33/36 pe gir gaya. Ek case bas flaky nikla (re-run pe pass ho gaya), lekin dusra miss har baar reproduce hua — wajah thi ek fixture jo purane laptop ka absolute file path use kar rahi thi. Ye asli regression nahi tha, suitcase error tha. Fix simple: path ko relative banao, aur usi commit mein re-baseline karo.

## Exam Mein Ye Kyun Aayega?
Bohot saare systems move ke dauran chupke se toot jaate hain. Move khud ek serious engineering problem hai — exam mein yehi samajh chahiye.
