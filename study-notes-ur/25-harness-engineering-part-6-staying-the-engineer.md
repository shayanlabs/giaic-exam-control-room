# 25. Part 6 — Staying the Engineer

## Aasan Zabaan Mein Samjho

Harness banana kaam ka sirf aadha hissa hai. Us harness ko mahino aur saalon tak healthy rakhna dusra aadha hissa hai.

Jo harness kabhi saaf nahi hoti, wo purani rules ka ek junk drawer ban jati hai — bilkul us almari ki tarah jisme har cheez thoons di gayi ho aur kuch bhi dhoond nahi paate. Ye agent ko dheema kar deti hai aur ajeeb bugs paida karti hai.

Is part ka core idea ye hai ke harness bhi ek zinda cheez hai — agar isay maintain na kiya jaye, to ye khud hi problem ban jati hai. Rules ka dher, purani coupling, aur observability ki kami — sab milkar harness ko waqt ke sath kamzor karte hain.

## Zaroori Concepts

### Observability
Jo tum dekh nahi sakte, usay improve nahi kar sakte. Tumhe logs, traces, aur numbers chahiye ke agent aur harness ne asal mein kya kiya.

### Capability-control trade-off
Zyada power aam tor par matlab kam control (aur ulta bhi sach hai). Har design choice is line par kahin na kahin baithti hai. Goal ye hai ke tum apna point jaan-boojh kar choose karo, power ko maximize karna maqsad nahi.

### Harness coupling
Harness aaj ke model ya tools ke exact behavior se kitni tight juri hui hai. Tight coupling harness ko todti hai jab models ya tools badal jate hain.

### Rule debt
Purani, overlapping, ya obsolete rules ka dher. Ye agent ko dheema aur system ko samajhna mushkil banata hai.

### Contracts se couple karo, behaviors se nahi
Stable success criteria aur interfaces ko prefer karo, is baat ki bajaye "isay bilkul waise karo jaise model X abhi kar raha hai."

### 90-day rule for retiring rules
Ek practical hygiene habit: har rule ko takreeban 90 din baad dobara dekhna chahiye aur ya to dobara justify karo ya hata do. Ye permanent rule debt ko rokta hai.

### Teen forces jo ratchet ko peeche dhakelte hain
Ratchet sirf ek taraf ghoomta hai — tight — aur yehi uska khatra bhi hai. Teen forces isay control mein rakhti hain. **Capability-control trade-off**: har rule jo ek failure hataati hai, wo ek move bhi hata deti hai, is liye maximum tight harness minimum ambition ka kaam degi — raat ke loops real repos par tight chalte hain, ek throwaway prototype session loose chalta hai, aur craft yehi hai ke zyada tar kaam ko sahi jagah beech mein rakha jaye. **Harness coupling**: ek harness jo ek model ki ajeeb aadaton ke saath bohot tight tuned ho, chupke se usi model ka hissa ban jati hai — ek real example ye hai ke naya model generation same text ke liye takreeban 30% zyada tokens generate karta hai, jo purani model par measure kiye gaye har token budget ko chupke se tod deta hai. Iska defense *contracts* se couple hona hai (exit codes, schemas, tests), ek model ke *behavior* se nahi. **Rule debt**: rules-file ki har line har beat mein tokens kharch karti hai, har hook har action mein seconds kharch karta hai — ek one-time ajeebiyat jo permanent rule kama leti hai, wo safety nahi, junk hai, is liye rule set ko har mahine review karo aur jo rule 90 din mein nahi chala aur uske saath koi linked incident nahi, usay removal ka candidate samjho (secrets ke around walls iski ek exception hain, hamesha is pruning se safe).

### Kab configuring rokni hai aur apni khud ki harness banani hai
Vendor harness (Claude Code, OpenCode) ke saath tab tak raho jab tak uske surfaces tumhare rules express kar sakte hain — ye zyada tar logon ke liye, zyada tar waqt sahi hai, aur vendor ki harness free mein har hafte behtar hoti hai. Apni khud ki harness tab banao jab product ki deewarein kisi aisi requirement ko rok rahi hon jo tumhare paas waqai hai: apna khud ka tool interface, apna khud ka verification stack, apna khud ka deployment shape. Yehi threshold hai book ke Mode 2 material mein — Build AI Agents, Eval-Driven Development, aur Deploy the Agent Harness — jo wahi paanch verbs hain (constrain, inform, verify, correct, escalate), sirf zyada code mein likhe gaye hain, settings file ke zariye configure kiye jaane ki bajaye.

## Exam Mein Ye Kyun Aayega?
Harness banana kaam ka sirf aadha hissa hai. Usay healthy rakhna dusra aadha hai. Exam mein long-term maintenance habits ka pata hona zaroori hai.
