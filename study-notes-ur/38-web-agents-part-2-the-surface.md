# 38. Part 2 — The Surface

## Aasan Zabaan Mein Samjho

Web surface ke apne rules hain — accounts kaise kaam karte hain, files kahan rehti hain, connectors kya reach kar sakte hain, aur finished kaam aakhir mein kahan land karta hai. Agar tumhe ye surface samajh nahi aayi, to agent ka kaam ghayab ho sakta hai ya platform ke andar hi qaid reh sakta hai.

Socho jaise tum kisi office building mein kaam karte ho jiske teen floors hain. Ek floor scratch paper ke liye hai jo saaf ho jata hai, dusra floor company ki filing cabinet hai, aur teesra floor tumhara apna ghar hai jahan asli important cheezein rakhi jaati hain. Jab tak asal document teesre floor tak nahi pohanchta, wo kabhi bhi gum ho sakta hai.

Aur haan, jab agent tumhari ghair-hazri mein koi bara decision lena chahe, wahan ek approval gate hota hai jo aksar tumhare phone pe notification ki shakal mein aata hai — yehi tumhara control point hai.

## Zaroori Concepts

### Account spine
Wo identity aur permission structure jo sessions, files, aur connectors ko aapas mein jorti hai.

### The three file tiers
**Tier 1 — Scratch**: temporary, kabhi bhi gayab ho sakta hai. **Tier 2 — Platform**: vendor ke system ke andar rehta hai. **Tier 3 — Your custody**: export ho kar tumhare apne control mein aa jata hai. Finished kaam hamesha Tier 3 tak pohanchna chahiye.

### Connectors
Wo links jo web agent ko bahar ke systems tak reach dete hain. Ye local connectors se zyada limited aur permissioned hote hain.

### The gate in your pocket
Approval step jo aksar phone ya notification pe aata hai — jab agent koi consequential action lena chahe aur tum wahan maujood na ho, ye hi insaan ka control point hai.

### A worked example: Ayesha's invoice, tier by tier
Ayesha monthly invoicing karti hai. Draft numbers (scratch math, temporary CSV) Tier 1 mein rehte hain aur wahin khatam ho jate hain — theek hai, kisi ne scratch paper audit nahi karni. Invoice template jo agle mahine reuse hoga Tier 2 mein jata hai. Final invoice PDF Tier 3 mein do dafa jata hai — Drive folder mein save aur client ko email. Kyun? Kyunke kabhi na kabhi koi poochega "March ka invoice kahan hai" — aur jawab "firm ke records mein" hona chahiye, "kahin agent account mein" nahi. Yaad rakhne wala rule: **finished kaam platform se bahar nikalta hai, baaqi sab platform mein reh sakta hai.**

### Why connectors carry double weight on the web
Desktop agent pe ek teesra trust lever hota hai — kaunse local folders agent dekh sakta hai — lekin browser-only session mein local filesystem hoti hi nahi, is liye ye kaam tier decision aur connector scopes dono mila kar karte hain. Do baatein yaad rakho: read scope send scope jaisa nahi (summarize karna aur email bhejna do alag grants hain), aur untrusted content — koi email, koi PDF — hamesha careful mode mein handle honi chahiye kyunke usme chupi hui instructions ho sakti hain (prompt injection).

## Exam Mein Ye Kyun Aayega?

Files ki clear ownership aur reliable gate ke bina web agents black boxes ban jate hain jinka kaam tum poora bharosa nahi kar sakte ya recover nahi kar sakte.
