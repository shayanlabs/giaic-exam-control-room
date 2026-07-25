# 37. Part 1 — The Shift

## Aasan Zabaan Mein Samjho

Ab ek hi web address do bilkul alag cheezein ho sakta hai — pehli wo purani chat box jo har turn pe tumhara wait karti hai, aur doosri ek remote session jo tab bhi kaam karti rahe jab tum browser tab band kar do. Yehi asal "shift" hai jo web agents laye hain.

Socho jaise ek dukaan ka darwaza — pehle tum andar khare rehte the, salesman tumse baat karta tha, tumhare bina wo kuch nahi karta tha. Ab wahi darwaza ek office ka bhi ho sakta hai jahan andar log tumhari ghair-hazri mein bhi kaam kar rahe hain, aur tum sirf report lene wapas aate ho. Farq ye hai ke same jagah (claude.ai ya chatgpt.com) dono roles nibha sakti hai — tumhe pata hona chahiye tum kis mein ho.

Ek simple test hai — agar type karna band karo aur tab band kar do, aur system bhi ruk jaye, to tum abhi bhi chat box mein ho. Agar wo chalta rahe, to tum remote-session duniya mein ho. Asal baat ye hai ke sync turn "wait karke chalta hai," lekin delegated run "start hone ke baad khud aage badhta hai" — chahe tumne wo chat box mein hi type kar ke start kiya ho.

## Zaroori Concepts

### Same address, two different things
claude.ai ya chatgpt.com interactive chat bhi ho sakti hai aur longer-running schedulable agent session ka surface bhi. Pehchanna zaroori hai tum kaunsi mein ho.

### The remote session
Ek aisi session jo vendor ke servers pe rehti hai aur tumhare laptop ya browser khule bina bhi chal (ya restart ho) sakti hai.

### Two vendors, one shape
Products alag hain lekin underlying shape same hai — heartbeat, connectors, run-until-done, spine, gate, body — same 6 parts har jagah.

### The stop-typing test
Agar type rokne aur tab band karne se system ruk jaye, to tum chat box mein ho. Agar chalta rahe, to remote session hai.

### The 6 parts
Wahi 6 loop parts web surface pe bhi apply hote hain — implementation details badalte hain, shape nahi.

### A worked example: Ayesha's power cut
Ayesha Lahore mein 5 baje ek report web session mein start karti hai. 6 baje bijli chali jati hai. 8 baje phone se session khol ke dekhti hai — kaam mukammal hai ya approval ke liye ruka hua hai. Uski bijli kabhi asal masla thi hi nahi, kyunke session vendor ke servers pe chal rahi thi — laptop sirf ek khidki tha. Ye ek desktop agent se bilkul mukhtalif hai jahan machine hi runtime hai — wahan bijli jate hi kaam ruk jata.

## Exam Mein Ye Kyun Aayega?

Web agents sabse accessible surface hain zyada tar logon ke liye — exam expect karta hai tum jaano loop ke ideas is surface pe kaise map hote hain.
