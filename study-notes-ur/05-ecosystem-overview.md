# 5. Ecosystem overview

## Aasan Zabaan Mein Samjho

Ek master cookbook socho jis par sab log yaqeen karte hain. Usi ek cookbook se teen darwaze khulte hain — ek unke liye jo seekhna chahte hain, ek unke liye jo banana chahte hain, aur ek unke liye jo inhi recipes se nayi books likhna chahte hain.

In darwazon ke peeche chaar tool boxes hain jo sab share karte hain. Sab kuch do jagah save hota hai — ek Git folder (master text) aur ek database (taake computers fast search kar sakein). Aur kyunke har banda apni khud ki AI brain le kar aata hai, is liye system chalane wale logon ko almost kabhi AI ka paisa nahi dena padta — isi liye cost near zero rehti hai.

## Zaroori Concepts

### One source, three gateways
**Source** khud book hai jo trusted System of Record ban chuki hai. **Teen gateways**: learners Claude (ya jaisa app) khol kar Zia Tutor AI se milte hain, builders Claude Code ya OpenCode khol kar Zia Developer AI se milte hain, aur authors publishing pipeline use karke book ke naye versions banate hain.

### Four packages (shared tool boxes)
**content** — trusted knowledge, **learning** — yaad rakhta hai student kahan tak pahoncha, **pedagogy** — teaching ke moves (kaise samjhana hai, kab quiz lena hai), **builder** — agents banane ke templates aur recipes.

### Git + Postgres
Git master text ko sambhalta hai. Postgres (pgvector naam ke special search tool ke saath) fast searchable version rakhta hai. Book ek jagah change karo, baaki sab khud update ho jata hai.

### Near-zero AI cost
Platform khud AI brain ka paisa nahi deta, har user apni subscription use karta hai. Platform sirf knowledge aur patle darwaze serve karta hai — isi liye bohot saare logon tak bina bade bill ke pahonch sakta hai.

## Exam Mein Ye Kyun Aayega?

Ye FDE AF Model se bana asal product hai — aage ke topics ye maan kar chalte hain ke tumhe pata hai pieces kaise judi hain aur cost itna kam kyun hai.
