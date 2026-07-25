# 38. Part 2 — The Surface

## Aasan Zabaan Mein Samjho
Web surface ke apne rules hain — accounts, files, connectors, aur finished kaam kahan reh jaata hai, sab alag tarah kaam karte hain. Agar surface samajh na aaye, to agent ka kaam gaayab bhi ho sakta hai ya platform ke andar hi locked reh sakta hai.

Sabse important idea ye hai: files teen tiers mein bantti hain. Tier 1 scratch hai — temporary, gayab ho sakta hai, koi masla nahi kyunke koi rough kaam ka audit nahi karta. Tier 2 platform storage hai — vendor ke system ke andar rehta hai. Tier 3 tumhari custody hai — export ho kar ya kisi jagah store ho kar jo pura tumhare control mein hai. Yaad rakhne wali ek line: **finished kaam platform se bahar nikalta hai, baaki sab andar reh sakta hai.**

Aur ek cheez — web session mein koi local filesystem nahi hota jise scope kiya ja sake. Isliye connector sirf agent ki bahar tak pahunch nahi, ye Tier-3 tak jaane ka main automated darwaza bhi hai. Do baatein yaad rakho: read scope aur send scope alag cheezein hain (jo mail summarize kar sakta hai wo send bhi kar sake, zaroori nahi), aur koi bhi bahar se aayi cheez — email, PDF — careful mode mein hi handle honi chahiye, kyunke usme chhupi hui instructions ho sakti hain (prompt injection).

## Zaroori Concepts

### Account spine
Identity aur permission structure jo sessions, files, aur connectors ko aapas mein jodta hai.

### Teen file tiers
Tier 1 — Scratch: temporary, gayab ho sakta hai. Tier 2 — Platform: vendor ke system ke andar. Tier 3 — Tumhari custody: export ya fully tumhare control mein. Finished kaam Tier 3 mein jaana chahiye.

### Connectors
Web agent ki bahar ki systems tak pahunch. Local connectors se zyada limited aur permissioned hote hain.

### Gate tumhari jeb mein
Approval step jo aksar phone ya notification pe hota hai — jab agent kisi consequential action ke liye tumhari door se permission mangta hai.

### Ayesha ka invoice, tier by tier
Ayesha ke monthly invoicing mein draft numbers (scratch math, temporary CSV) Tier 1 mein reh kar khatam ho jaate hain — sahi baat hai, koi rough kaam audit nahi karta. Reusable invoice template Tier 2 mein jaata hai, session ke saath attached. Final invoice PDF do jagah Tier 3 mein jaata hai — firm ke Drive folder mein save, aur mail connector se client ko bhej diya. Kyun dono jagah? Kyunke kabhi na kabhi koi poochega "March ka invoice kahan hai" — jawab "firm ke records mein" hona chahiye, "kisi agent account mein kahin" nahi.

## Exam Mein Ye Kyun Aayega?
Bina clear file ownership aur reliable gate ke, web agents black box ban jaate hain — kaam produce karte hain jispe pura bharosa nahi kar sakte, ya recover nahi kar sakte.
