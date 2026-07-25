# 28. Part 2 — The Golden Set

## Aasan Zabaan Mein Samjho

Golden set ek soch samajh kar chuni gayi collection hai real cases ki (khaas kar wo failures jo tum pehle hi pakad chuke ho) jinke khilaf tum system ko baar baar chalate ho.

Ye us cheez ke sabse qareeb hai jo agent behavior ke liye ek regression suite ho sakti hai. Socho tum ek doctor ho jo ek naye treatment ko test karne se pehle sab purani mushkil cases ki file nikaal kar dobara check karte ho — "pichli baar jo galtiyan hui thin, kya wo abhi bhi ho rahi hain?" Golden set bilkul yehi kaam karta hai.

## Zaroori Concepts

### Har pakdi gayi failure ek case ban jati hai
Sabse valuable cases wo hain jo pehle system ko tod chuki hain ya sharminda kar chuki hain. Unhein permanent test cases banane se wahi failure chupke se dobara nahi aa sakti.

### Case ki shape aur runner
Har case ka ek saaf structure hai (input, context, expected properties ya rubric) aur ek runner hai jo agent ko chalata hai aur result ko score karta hai.

### Origin line
Har case kahan se aayi (kaunsa real incident ya kaunsi synthetic construction), ye record karna tumhein samjhata hai ke set asal mein kya cover karta hai.

### Failures pehle aati hain
Real failures ko easy synthetic cases se zyada priority do. Set itna mushkil hona chahiye ke wo useful ho.

### 20-40 cases across difficulty
Ek practical size: itna bada ke regressions pakad sake, itna chota ke chala aur maintain kiya ja sake.

### Errors, fails ke barabar nahi hain
- **Error**: system crash ho gaya ya finish nahi kar saka.
- **Fail**: system finish hua lekin result ghalat ya kaafi acha nahi tha.
Dono important hain, lekin dono alag signals hain.

### Worked example: ek case asal mein kaisi dikhti hai
Ek real case ek chhoti si JSON file hoti hai, koi abstract idea nahi. Source se ek example: `deleted-test-001`, category `false_green`, judge ko `diff` parhne ko bolta hai, `expected: {verdict: "FAIL", risk: "high"}` ke saath, ek `must_mention` list, aur ek `origin` line jo wapas real incident ki taraf ishara karti hai ("bad night, 2026-06-30"). Ye `origin` field important hai — isi se pata chalta hai ke ek case proven reachable hai (ek real pakdi gayi failure) ya sirf koi imagine ki hui invented case hai.

### Runner ek loop hai, framework nahi
Source bilkul saaf kehta hai ke tumhein special eval software ki zaroorat nahi: runner sirf ek shell loop hai jo har case ko chand baar chalata hai (teen ek common starting point hai), agent se apna verdict ek file mein likhwata hai, aur `jq` jaise tool se us file ko expected ke sath compare karta hai. Ek baat yaad rakhne layak hai: errors aur fails alag se count kiye jate hain, kyunki "judge ne protocol tod diya aur koi jawab hi nahi diya" aur "judge ne jawab diya lekin ghalat tha" — dono alag problems hain jinke fix bhi alag hain.

## Exam Mein Ye Kyun Aayega?
Golden set ke bagair tumhare paas ye jaanne ka koi reliable tareeka nahi ke system behtar ho raha hai ya kharab. Exam mein ye samajhna zaroori hai ke isay kaise banaya aur maintain kiya jaye.
