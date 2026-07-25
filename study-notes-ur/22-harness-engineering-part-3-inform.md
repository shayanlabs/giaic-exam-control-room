# 22. Part 3 — Inform

## Aasan Zabaan Mein Samjho

Ek agent jo constrained toh hai lekin jo cheez usay pata honi chahiye wo nahi jaanta — wo ya fail hoga, ya guessing mein bohot sara paisa barbaad karega.

Harness ke "Inform" kaam ka matlab hai agent ko sahi information, sahi waqt par, aur sahi form mein dena.

Aur yahi wo jagah hai jahan **AX (agent experience)** rehta hai — matlab agent ki nazar se duniya kitni saaf aur pleasant lagti hai.

## Zaroori Concepts

### Context surfaces harness ke parts ki tarah
Alag knowledge alag jagah rehni chahiye:
- Jo hamesha sach hai → rules file (permanent instructions).
- Jo sirf is tarah ke task ke liye sach hai → skill.
- Bahar ke systems tak pahunchne ki ability → connector.

### Errors ko batana chahiye age kya karna hai
Achi error message sirf "fail ho gaya" nahi bolti. Wo agent (ya insaan) ko agla concrete action batati hai. Buri error messages doom loops banati hain jahan agent wahi tooti hui cheez baar baar try karta rehta hai.

### AX (agent experience)
Agent ka version hai user experience ka. Clear tool names, helpful error messages, stable identifiers, predictable structure, aur achhe defaults — sab AX behtar karte hain. Behtar AX matlab zyada reliability, kam cost.

### Teen surfaces sawaal ki tarah, aur bug ko triage kaise karein
Har context surface ek hi sawaal ka jawab deta hai jo harness ko har beat handle karna hota hai: **rules file** batati hai "yahan hamesha kya sach hai?" (conventions, boundaries — har run padhi jati hai, isliye choti rakho kyunke har line har beat tokens kharch karti hai); **skills** batati hain "ye specific kaam kaise karte hain?" (sirf tab load hoti hain jab task match kare, isliye detail free hai jab tak zaroorat na ho); **connectors** batate hain "kya reach kar sakta hai, aur kaise?" Jab koi run fail ho kyunke agent ko kuch pata nahi tha, ye tumhe das second ka triage deta hai, poori shaam prompt rewrite karne ke bajaye: hamesha-sach fact → rules file; task-specific knowledge → skill; missing reach → connector.

### AX ke teen concrete findings
Har surface ka ek reader hota hai, aur wo tum nahi ho — wo agent hai, task ke beech mein, jisse pooch nahi sakta tumhara matlab kya tha. Isi reader ke liye design karne se teen findings nikalti hain: **kam, focused tools zyada overlapping tools se behtar hote hain** (Anthropic ka rule — agar ek human engineer confidently na bata sake ke kaunsa tool sahi hai, toh agent bhi nahi bata payega); **tool descriptions asal kaam karti hain** ("customer database ko email ya ID se search karta hai; zyada se zyada 20 rows return karta hai" — ye "customer tool" se kahin behtar hai, jaise labeled darwaza unlabeled se behtar); aur **errors ko batana chahiye age kya karna hai**, kyunke loop mein error message hi agle attempt ka input hai — "Permission denied: `repo` scope maango" agle beat mein khud theek ho jata hai, jabke sirf "Error 403" us beat ko barbaad kar deta hai. Kisi bhi surface ka test yahi hai: kya sirf ye text dekh kar koi ajnabi bhi sahi agla step le sakta hai?

## Exam Mein Ye Kyun Aayega?
Ek achi tarah informed agent confused agent se kaafi zyada sasta aur reliable hota hai. Exam mein pata hona chahiye ke alag knowledge kahan reh ni chahiye.
