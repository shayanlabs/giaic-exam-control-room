# 31. Parts 5 + 6 — The 12-case suite and staying honest

## Aasan Zabaan Mein Samjho

Ek achi evaluation system ko bhi game kiya ja sakta hai, ya wo false confidence de sakti hai.

Ye final parts ek practical 12-case pattern aur wo honesty habits cover karte hain jo tumhe khud ko dhoka dene se bachati hain.

## Zaroori Concepts

### Goodhart's law
Jab koi measure target ban jata hai, wo achha measure rehna band kar deta hai. Agar team sirf golden-set score optimize karti rahe, toh score real-world quality reflect karna chhor deta hai.

### Hold-outs
Wo cases jinke against development process ko train ya tune karne nahi diya jata. Ye khud ko dhoka dene ke against last line of defense hain.

### Evals kya proof nahi kar sakte
Evals dikha sakte hain ke kuch jaani-pehchani failure modes absent hain. Ye proof nahi kar sakte ke system har mumkin future situation mein safe hai. Isi limit ko jaan na honesty ka hissa hai.

### Injection category ka bar — sabko pass hona zaroori hai
Security-sensitive categories (prompt injection aur waise hi) ke liye bar usually "sab pass hon" hota hai, "average score high ho" nahi. Ek bhi failure ek real risk hai.

### Attack fixtures live ammunition hain
Cases jo injection aur doosre attacks test karti hain, agar leak ya mishandle ho jayein toh khatarnak hain. Inhe waise hi treat karo jaise real exploits.

### Worked example — Goodhart gap
Socho ek team apni suite ko do mahine tune karti rahi jab tak wo perfect 36/36 na hit kar le — lekin unke sealed hold-outs, jinhe kabhi tune nahi kiya gaya, chupke se 90% se 70% par aa gaye. Kuch bhi malicious nahi hua — har chota prompt aur rule tweak wahi 36 verdicts ke against validate hua, isliye system dheere dheere test seekh gaya, material nahi. Source ka fix do moves hain: kuch hold-outs ko tuned set mein promote karo kyunke wo ab memorized cases se zyada reality represent karte hain, aur sabse purani low-severity cases ko recent production failures se refresh karo — phir re-baseline karo aur fresh hold-outs ka naya batch seal karo.

### Agent ko kabhi answer key mat dikhao
Fixtures ko physically khatarnak rakhne ke ilawa (real attack text jo kisi bhi session ko steer kar sakta hai jo galti se us folder mein pahunch jaye), source ek doosri, aasani se miss hone wali wajah bhi deta hai fixtures folder ko everyday context se bahar rakhne ki: reviewer `deleted-test-001` jaisi case par *test* toh ho sakta hai, lekin usay kabhi *padhne* nahi diya jana chahiye. Us folder ko eval runs ke ilawa padhne se rokne wala ek deny rule — source ki recommend ki hui ek-line deewar hai jo isay habit se wall bana deti hai.

## Exam Mein Ye Kyun Aayega?
Ye final honesty layer hi professional evaluation practice ko score-chasing exercise se alag karti hai. Exam chahta hai tumhe techniques aur unki limits, dono pata hon.
