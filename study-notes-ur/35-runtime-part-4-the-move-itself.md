# 35. Part 4 — The Move Itself

## Aasan Zabaan Mein Samjho

Ek chalte hue loop ko ek jagah se dusri jagah move karna utna aasan nahi jitna dikhta hai. Socho jaise koi ghar shift ho raha ho — tumhari acchi aadatein aur discipline tumhare sath chali jayengi, lekin furniture, wires, aur connections nayi jagah dobara set karni parti hain. Purane ghar mein jo bharosa tha wo automatically naye ghar transfer nahi hota — wahan dobara kamana parta hai.

Yehi baat loop ke sath hai — jo cheezein important hain (rules, evaluation suite, success criteria) wo tumhare sath travel karti hain, lekin mechanics — file paths, exact hooks, credential setup — usually dobara banani parti hain. Aur sirf isliye ke wo tumhare laptop pe safe tha, iska matlab nahi wo naye ghar mein bhi safe hoga — validate dobara karna parega.

## Zaroori Concepts

### The suitcase test
Jo cheezein sach mein tumhare sath aani chahiyein: specifications, skills, evaluation suite, spine format, success criteria. Baaqi sab saman hai jo shayad replace karna pare.

### Trust is re-earned, not transferred
Loop laptop pe safe tha, lekin naye runtime mein bhi safe hoga ye guarantee nahi — dobara test karna zaroori hai.

### Discipline travels but mechanics get rebuilt
Maker-checker ka idea, spine ka concept, stop conditions — ye sab travel karte hain. Lekin exact hooks, file paths, credential injection dobara implement karna parta hai.

### The arrival protocol
Nayi jagah pohanchne ka ek tarteeb wala tareeqa: full rule set category ke hisaab se organize karo, quality bars ko neeche mat karo "sirf move ki wajah se", aur probation period rakho jahan extra monitoring ho jab tak full trust na bane.

### What travels vs. what gets rebuilt, concretely
Suitcase mein jo jata hai: spec, rubric with anchors, golden set (har case ki origin line aur baselines ke sath), ratchet log, maker-checker split, human gate. Jo peeche reh jata hai: CLI flags, output formats, file paths, session state, purane runtime ka API-specific code, aur purani cost assumptions. Yaad rakhne wala ek rule: repo hi truth rakhta hai, aur har home ussi se configure hota hai — jo rule sirf vendor-side setting mein rehta hai, wo suitcase se chupke nikal jata hai.

### A worked example: a "regression" that was really a suitcase bug
Ek case mein Home 2 pe move karne se score 35/36 se 33/36 pe girta hai. Ek case flake tha (dobara chalane pe pass ho gaya — noise), lekin dusra miss har baar reproduce hota hai — pata chalta hai ek fixture purane laptop ke absolute file path se read kar raha tha. Ye agent ki regression nahi thi, ye suitcase error thi. Fix ye hua ke path relative banaya gaya aur ussi commit mein re-baseline kiya gaya.

## Exam Mein Ye Kyun Aayega?

Bahut se systems move ke dauran chupke se toot jate hain — exam expect karta hai ke tum jaano move khud ek serious engineering problem hai.
