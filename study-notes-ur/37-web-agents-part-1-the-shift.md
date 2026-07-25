# 37. Part 1 — The Shift

## Aasan Zabaan Mein Samjho
Yaar, socho — claude.ai ya chatgpt.com, ek hi address, lekin do bilkul alag cheezein de sakta hai. Ek simple chat box jo tumhare turn ka wait karta hai. Aur ek remote session jo tumhare tab band karne ke baad bhi kaam karta rehta hai. Yehi hai "the shift" — samajhna ye hai ke tum kaunsa wala use kar rahe ho.

Farq karne ka aasan tareeqa: agar tum typing band karo, tab band karo, aur system bhi ruk jaaye — to tum abhi bhi chat box mein ho. Agar kaam chalta rahe — to tum remote-session duniya mein ho. Isko "stop-typing test" bolte hain.

Asal farq technical hai: ek plain chat turn *synchronous* hota hai — chalta hai jab tak tum wait karo, phir ruk jaata hai, tumhare agle turn ka wait karta hai. Ek agent run *delegated* hota hai — ek baar start ho gaya to apne aap outcome ki taraf badhta rehta hai, tumhare agle message ka mohtaj nahi. Interesting baat ye hai ke tum chat box ke andar se hi ek delegated run start kar sakte ho — bas itna likh kar: "Har Monday, ye emails summarize kar do." Alfaaz chat mein gaye, lekin jo set up hua wo delegated task hai, normal reply nahi.

## Zaroori Concepts

### Ek address, do alag cheezein
claude.ai ya chatgpt.com interactive chat bhi ho sakta hai, aur longer-running schedulable agent sessions ka surface bhi. Pata hona chahiye tum kaunsa use kar rahe ho.

### Remote session
Aisa session jo vendor ke servers pe rehta hai, tumhare laptop ya browser khule bina chal (ya restart ho) sakta hai.

### Do vendors, ek shape
Products alag dikhte hain, lekin underlying shape same hai: heartbeat, connectors, run-until-done, spine, gate, body.

### Stop-typing test
Agar typing rukne aur tab band karne se system ruk jaaye — chat box hai. Agar chalta rahe — remote session hai.

### Ayesha ka power cut
Ayesha Lahore mein 5 baje ek client report web session mein start karti hai. 6 baje load-shedding se bijli chali jaati hai. 8 baje phone se session kholti hai — kaam khatam mil jaata hai, ya approval ka wait kar raha hota hai. Uski bijli kabhi masla thi hi nahi, kyunke session vendor ke server pe chal raha tha, laptop sirf ek window tha. Band window us cheez ko nahi rokti jo doosri taraf chal rahi hai.

### 6 parts ek decoder ring hain
"Triggers" matlab heartbeat. "Integrations" matlab connectors. "Autopilot mode" matlab run-until-done loop (pehla sawal poochho: stopping condition kya hai, check kaun karta hai). "Workspace memory" matlab state spine. Isi lens se koi bhi naya product ek minute mein samajh aa jaata hai.

## Exam Mein Ye Kyun Aayega?
Web agents sabse accessible surface hain zyada tar logon ke liye. Exam mein samajh honi chahiye ke loop ke ideas is surface pe kaise map hote hain.
