# 22. Part 3 — Inform

## Aasan Zabaan Mein Samjho

Ek constrained agent jise ye nahi pata ke usay kya jaanna zaroori hai, wo ya to fail hoga ya guess karne mein bohot paisa barbad karega. Harness ka "Inform" wala kaam ye hai ke agent ko sahi information, sahi waqt par, aur sahi form mein di jaye.

Yahin par **AX (agent experience)** ka concept aata hai — agent ke nazariye se duniya kitni saaf aur pleasant lagti hai. Socho ek naye employee ko office mein bhej diya jaye bina kisi manual, bina kisi labeled door ke — wo ghoomta rahega, waqt zaya karega. AX ka matlab hai agent ke liye wo manual aur labeled doors banana.

Achi information ka matlab sirf facts dena nahi — jab kuch ghalat ho, to error message bhi agle step ka rasta dikhana chahiye, warna agent wahi ghalti baar baar dohrata rahega.

## Zaroori Concepts

### Context surfaces as harness parts
Alag alag types ki knowledge alag jagah rehti hai:
- Jo hamesha sach hai → rules file (permanent instructions).
- Jo sirf is tarah ke task ke liye sach hai → skill.
- Bahar ke systems tak pahunchne ki ability → connector.

### Errors ko batana chahiye age kya karna hai
Ek achi error message sirf "ye fail ho gaya" nahi kehti. Ye agent (ya insaan) ko agla concrete kaam bhi batati hai. Buri error messages doom loops banati hain jahan agent wahi tooti hui cheez baar baar try karta rehta hai.

### AX (agent experience)
Agent ka apna version hai user experience ka. Clear tool names, helpful error messages, stable identifiers, predictable structure, aur achhe defaults — sab AX ko behtar banate hain. Behtar AX matlab zyada reliability aur kam cost.

### Teen surfaces bataur sawal, aur bug ko triage kaise karein
Har context surface exactly ek sawal ka jawab deta hai jo harness ko har beat mein handle karna hai: **rules file** batata hai "yahan hamesha kya sach hai?" (conventions, boundaries — har run mein parhi jaati hai, is liye chhoti rakho kyunki har line har beat mein tokens kharch karti hai); **skills** batati hain "ye specific kaam kaise karte hain?" (sirf tab load hoti hain jab task match kare, is liye detail free hai jab tak zaroorat na ho); **connectors** batate hain "ye kya reach kar sakta hai, aur kaise?" Jab koi run isliye fail ho ke agent ko *kuch pata nahi tha*, to ye tumhein das second ka triage deta hai, poore din ka prompt rewrite nahi: hamesha-sach fact → rules file; task-specific knowledge → skill; missing reach → connector.

### AX ki teen concrete findings
Har surface ka ek reader hota hai, aur wo tum nahi ho — wo agent hai, task ke beech mein, jo poochh nahi sakta tumhara matlab kya tha. Is reader ke liye design karne se teen findings nikalti hain: **kam, focused tools, bohot saare overlapping tools se behtar hain** (Anthropic ka rule of thumb — agar ek human engineer confidently ye na bata sake ke konsa tool sahi hai, to agent bhi nahi bata sakta); **tool descriptions asal mein kaam karti hain** ("customer database ko email ya ID se search karta hai; max 20 rows return karta hai" ye "customer tool" se kahin behtar hai, jaise ek labeled darwaza unlabeled darwaze se behtar hota hai); aur **errors ko batana chahiye age kya karna hai**, kyunki ek loop mein error message hi *agle attempt ka input* hoti hai — "Permission denied: request the `repo` scope" agle beat mein khud theek ho jata hai, jab ke sirf "Error 403" us beat ko zaya kar deta hai. Kisi bhi surface ke liye test yehi hai: kya ek competent ajnabi, sirf ye text dekh kar, sahi agla kadam le sakta hai?

## Exam Mein Ye Kyun Aayega?
Ek achi tarah inform kiya gaya agent, confused agent se kahin zyada sasta aur reliable hota hai. Exam mein tumhein pata hona chahiye ke alag alag knowledge kahan rehni chahiye.
