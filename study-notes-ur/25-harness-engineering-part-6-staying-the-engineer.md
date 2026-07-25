# 25. Part 6 — Staying the Engineer

## Aasan Zabaan Mein Samjho

Harness banana toh aadha kaam hai. Usay mahinon, saalon tak healthy rakhna doosra aadha kaam hai.

Jo harness kabhi saaf nahi hoti, wo purani rules ka junk drawer ban jati hai. Isse agent slow hota hai aur ajeeb ajeeb bugs paida hote hain.

## Zaroori Concepts

### Observability
Jo tum dekh nahi sakte usay improve nahi kar sakte. Tumhe logs, traces, aur numbers chahiye ke agent aur harness ne asal mein kya kiya.

### Capability-control trade-off
Zyada power usually zyada kam control laati hai (aur ulta bhi). Har design choice is line par kahin na kahin baithi hoti hai. Goal ye hai ke apni jagah jaan bujh kar chuno, power ko maximize karna nahi.

### Harness coupling
Harness aaj ke model ya tools ke exact behavior se kitni tight bandhi hui hai. Tight coupling se harness tootne lagti hai jab models ya tools change hote hain.

### Rule debt
Purani, overlapping, ya obsolete rules ka dher. Isse agent slow hota hai aur system samajhna mushkil ho jata hai.

### Contracts se couple karo, behaviors se nahi
Stable success criteria aur interfaces ko prefer karo — "isko exactly waise karo jaise model X abhi karta hai" ki jagah.

### 90-day rule — rules retire karne ka
Ek practical hygiene habit: har rule ko takreeban 90 din baad dobara dekho, aur ya to justify karo ya hata do. Isse permanent rule debt nahi banti.

### Teen forces jo ratchet ko peeche khinchti hain
Ratchet sirf ek taraf ghoomta hai — tight, aur yehi iska khatra bhi hai. Teen forces isay balance mein rakhti hain. **Capability-control trade-off**: har rule jo ek failure hataati hai, ek move bhi hata deti hai — isliye maximum tight harness minimum ambition wala kaam deti hai; real repos par overnight loops tight chalti hain, throwaway prototype session loose chalti hai, aur craft yehi hai ke zyada tar kaam beech mein sahi jagah rakha jaye. **Harness coupling**: ek harness jo ek model ki ajeeb habits ke bohot kareeb tune ho, chupke se usi model ka hissa ban jati hai — misaal ke taur par, naya model generation same text ke liye takreeban 30% zyada tokens generate karta hai, jo purane model par measure kiya har token budget chupke se tor deta hai. Iska defense hai *contracts* (exit codes, schemas, tests) se couple karna, na ke ek model ke *behavior* se. **Rule debt**: rules-file ki har line har beat tokens kharch karti hai, har hook har action mein seconds kharch karta hai — ek one-time ajeebogareeb cheez ko permanent rule bana dena safety nahi, junk hai; isliye rule set ko har mahine review karo, aur jo rule 90 din se nahi chali aur uska koi linked incident nahi, usay hatane ka candidate maano (secrets ke ird gird deewarein iski ek exception hain, ye pruning se hamesha safe hain).

### Configure karna kab rokna hai aur khud banana kab shuru karna hai
Vendor harness (Claude Code, OpenCode) ke saath tab tak raho jab tak uski surfaces tumhare rules express kar sakein — zyada tar logon ke liye zyada tar waqt yehi kaafi hai, aur vendor ki harness har hafte free mein behtar hoti rehti hai. Apna khud ka harness sirf tab banao jab product ki deewarein us requirement ko rok rahi hon jo tumhare paas asal mein hai: apna tool interface, apna verification stack, apna deployment shape. Yehi threshold hai book ke Mode 2 material mein jaane ka — Build AI Agents, Eval-Driven Development, aur Deploy the Agent Harness — jo wahi paanch verbs hain (constrain, inform, verify, correct, escalate), bas zyada code mein likhe hue, kam settings file mein configure kiye hue.

## Exam Mein Ye Kyun Aayega?
Harness banana sirf aadha kaam hai. Usay healthy rakhna doosra aadha hai. Exam ko long-term maintenance habits ka pata hona chahiye.
