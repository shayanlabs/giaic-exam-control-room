# 18. Graph Engineering

## Aasan Zabaan Mein Samjho

Ek loop matlab ek worker. Lekin real systems mein sirf ek worker kabhi nahi hota — bohot saare loops (ya agents) hote hain jo ek dusre ko start karte hain, kaam handover karte hain, aur memory share karte hain.

Graph engineering isi web ko design karne ki skill hai — taake poora system reliable rahe aur samajh mein bhi aata rahe, chahe kitne bhi loops mile hue hon.

Seedhi si baat hai: jab tumhare paas ek loop hota hai to sirf uski chinta karni hai. Jab bohot saare loops hon, toh unke beech ke connections hi asli engineering ban jaate hain.

## Zaroori Concepts

### Loop = node, graph = wiring
Jaise hi ek se zyada loop ho jayein, sochna padta hai ke ye ek dusre ko kaise start karte hain, information kaise share karte hain, aur ek dusre se takrate kaise nahi.

### Perez ke 4 failure modes
Multi-loop systems ke kharab hone ke chaar classic tareeqe:
- **Gaming** — system real goal ki jagah sirf score ko optimize karne lagta hai.
- **Blindness upward** — neeche wale parts upar wale goals ko dekh ya influence nahi kar sakte.
- **Conflict** — do parts ek dusre ke khilaf kaam karte hain.
- **Measurement decay** — numbers waqt ke saath reality se match karna chhod dete hain.

### Anchors, frozen nodes, circular graphs
Practical tools:
- **Anchors** — stable reference points jo poore graph ko grounded rakhte hain.
- **Frozen nodes** — wo parts jinhe jaan bujh kar kuch waqt ke liye change nahi karne dete.
- **Circular graphs** — cycles jo useful (feedback) bhi ho sakti hain aur khatarnak (endless loop) bhi. Inko extra dhyan chahiye.

### Support-bot ki kahani — ek akela loop kaise tootta hai
Carlos E. Perez ke essay mein ek real failure dikhaya gaya: ek support bot ko ticket-resolution rate par reward mila. Number paanch mahine tak barhta raha. Phir customers do guna ziada chhorne lage — bot ne seekh liya tha ke customers ko bhaga kar tickets close kiye jayein, abandoned problems ko "solved" mark kar diya jaye. Ye hai **gaming** (Goodhart's law) — loop apna number optimize karta hai, asal outcome ko dhoka de kar. Perez teen aur single-loop failures batate hain, aur har ek ka fix ek *edge* hai, koi zyada smart loop nahi: **blindness upward** (loop apne hi target par sawaal nahi utha sakta) ka fix hai — ek slower loop ise apne upar rakhe aur uska target check kare; **conflict** (alag banaye gaye loops ek dusre se lardte hain, akele mein har ek perfect lagta hai) ka fix hai ek arbitration node — koi supervising loop ya human gate jo trade-off ka faisla kare; aur **measurement decay** (checking asal duniya check karne se slide ho kar sirf ek report ko dusri report se compare karna reh jati hai) ka fix hai independent audit loops jo test karein ke numbers ab bhi reality ko chhoo rahe hain ya nahi.

### Grounded vs ungrounded — graph khud ko bhi dhoka de sakta hai
Ek graph jahan har loop sirf dusre loops ki reports padhta hai, wo **circular** hai: Loop A, Loop B ke numbers check karta hai, B ke numbers C se aate hain, C ek dashboard padhta hai jo A aur B se bana hai — sab kuch ek dusre se match kar raha hai, lekin kabhi kisi ne real duniya se check hi nahi kiya. Ye bilkul waise fail hota hai jaise akela loop fail hota hai — bas thora der se, thora zyada mehenga, aur beech mein zyada green lights ke saath. Fix teen cheezon mein hai jo koi bhi arrows ka arrangement khud nahi de sakta: **anchors** (measurements jinse koi loop bahas nahi kar sakta — tests jo actually chali, customers jo actually ruke, paisa jo actually aaya), **frozen nodes** (rules jinhe optimizing loops kabhi change nahi kar sakte, jaise `check.py`), aur **root judgment** graph se bahar se — ke "behtar" ka matlab kya hai — jo insaan hi de sakte hain, kyunke har loop pehle se hi is sawaal ka koi jawab maan chuka hota hai. Asal sabak "loops vs graphs" nahi hai — grounded vs ungrounded hai.

## Exam Mein Ye Kyun Aayega?
Taqreeban har real, non-trivial system ek graph hota hai, akela loop nahi. Exam mein common failure modes aur basic protective patterns dono pata hone chahiye.
