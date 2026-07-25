# 34. Part 3 — The Managed Runtime

## Aasan Zabaan Mein Samjho

Managed runtime samjho ek aisi service jo tumhe agent, uske chalne ki safe jagah, aur ek session de deti hai — bina is baat ke tumhe khud servers chalane parein. Ye aise hai jaise tum ek furnished flat kiraye pe le lo — bijli, pani, security sab tayyar, tumhe sirf rehna hai. Fayda ye hai ke tumhe khud ye sab set up nahi karna, lekin nuqsan ye hai ke tumhara control kam ho jata hai aur is convenience ke liye tumhe paisa dena parta hai.

Is model ka sabse important idea ye hai ke jo model sochta hai (agent) aur jo sandbox action karta hai (environment), ye dono ab alag alag dikhte hain — pehle tumhare laptop pe ye dono ek hi jagah, ek hi process mein rehte the, ab service inhe connect karti hai.

Socho jaise tum ek restaurant mein khana order karte ho — tumhe kitchen chalani nahi parti, bas menu se select karo aur khana table pe aa jata hai. Lekin agar recipe change karni ho ya kitchen ka control chahiye ho, to wo tumhare paas nahi.

## Zaroori Concepts

### Agent / environment / session
Managed runtime teen cheezein deta hai: **agent** (configured worker — model, prompt, tools, guardrails), **environment** (wo sandbox jahan kaam actually hota hai), aur **session** (ek continuous run jiska apna memory aur cost meter hota hai).

### What you get, what you give up, and what it costs
Tumhe milta hai easy scaling, isolation, aur kam operational load. Tum dete ho host pe deep control aur kabhi kabhi exact tool versions ka control. Cost aksar active time ke hisaab se measure hoti hai.

### The self-hosted sandbox option
Agar zyada control chahiye ya compliance rules ki wajah se managed service kaafi nahi, to tum khud bhi apna isolated environment chala sakte ho.

### About $0.08 per active session-hour; idle time is free
Ye ek concrete pricing example hai jo course ke waqt ka hai. Important idea ye hai ke tum active kaam ka paisa dete ho, sirf configuration exist karne ka nahi.

### The three objects, named precisely
Course ka concrete example hai Claude Managed Agents (public beta, April 2026). Yahan agent, environment, aur session ka concept clearly separate hota hai, aur session pause/resume bhi ho sakti hai kyunke laptop khula rehne ki zaroorat nahi.

### What you give up, precisely
Teen cheezein deni parti hain — **visibility** (tum machine nahi, sirf service ka event log dekhte ho), **custody** (tumhara data kisi aur ke infrastructure pe chalta hai — kuch regulators ke liye ye deciding factor hai), aur **portability** (tumhari definition vendor ke shapes mein likhi hoti hai, is liye chorna matlab rewrite karna, sirf move karna nahi).

## Exam Mein Ye Kyun Aayega?

Zyada tar production loops kisi na kisi managed runtime mein rehte hain, is liye trade-offs aur cost model samajhna zaroori hai.
