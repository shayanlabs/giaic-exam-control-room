# 28. Part 2 — The Golden Set

## Aasan Zabaan Mein Samjho

Golden set matlab real cases ka ek carefully chuna hua collection (khaas taur par wo failures jo tum pehle hi pakar chuke ho) jinke against system ko baar baar chalate ho.

Ye agent behavior ke liye jitna qareeb ho sakta hai utna hi qareeb ek regression suite hai.

## Zaroori Concepts

### Har pakri hui failure ek case ban jati hai
Sabse valuable cases wahi hain jo pehle system ko tora ya sharminda kiya. Unhe permanent test cases banane se wahi failure chupke se wapas nahi aa sakti.

### Case ki shape aur runner
Har case ki ek clear structure hoti hai (input, context, expected properties ya rubric) aur ek runner jo agent ko chala kar result score karta hai.

### Origin line
Har case kahan se aayi ye record karna (kaunsa real incident ya kaunsa synthetic construction) samajhne mein madad karta hai ke set asal mein kya cover karta hai.

### Failures pehle aati hain
Real failures ko easy synthetic cases se pehle rakho. Set itna hard hona chahiye ke wo useful bhi ho.

### 20-40 cases, alag difficulty mein
Ek practical size — itni bari ke regressions pakar sake, itni choti ke run aur maintain ho sake.

### Errors, fails jaisi nahi hoti
- **Error**: system crash ho gaya ya finish hi nahi hua.
- **Fail**: system finish hua lekin result ghalat ya kaafi achha nahi tha.
Dono matter karte hain, lekin dono alag signals hain.

### Worked example — ek case asal mein kaisi dikhti hai
Ek real case ek chota JSON file hai, koi abstract idea nahi. Source se ek misaal: `deleted-test-001`, category `false_green`, judge ko `diff` padhne ko bolti hai, `expected: {verdict: "FAIL", risk: "high"}` ke saath, ek `must_mention` list, aur ek `origin` line jo wapas asal incident ki taraf point karti hai ("bad night, 2026-06-30"). Ye `origin` field matter karti hai — isi se pata chalta hai kaunsi case proven-reachable hai (ek real pakri hui failure) aur kaunsi sirf koi socha hua invented case hai.

### Runner ek loop hai, framework nahi
Source seedha kehta hai ke koi khaas eval software ki zaroorat nahi — runner sirf ek shell loop hai jo har case ko kai baar chalata hai (teen ek common starting point hai), agent se verdict ek file mein likhwata hai, aur `jq` jaisa tool use karke us file ko expected se compare karta hai. Ek detail yaad rakhne wali: errors aur fails alag alag count hoti hain, kyunke "judge ne protocol tor diya aur koi jawab nahi diya" aur "judge ne jawab diya lekin ghalat tha" — ye alag problems hain, alag fixes chahte hain.

## Exam Mein Ye Kyun Aayega?
Golden set ke bina ye pata karne ka koi reliable tareeqa nahi ke system behtar ho raha hai ya kharab. Exam chahta hai tumhe pata ho ise kaise banana aur maintain karna hai.
