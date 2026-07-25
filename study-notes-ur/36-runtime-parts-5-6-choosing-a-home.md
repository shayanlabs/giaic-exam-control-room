# 36. Parts 5 + 6 — Choosing a Home

## Aasan Zabaan Mein Samjho

Koi ek "best" home nahi hai jo har loop ke liye perfect ho. Sahi choice iss baat pe depend karti hai ke user kaun hai, tumhe kya cheez apne control mein rakhni hai, koi insaan wait kar raha hai ya nahi, aur agar raat ko kuch ghalat ho jaye to uski keemat kya hogi. Aur haan, tum alag alag homes ko mix bhi kar sakte ho — jaise development laptop pe, scheduled kaam cloud mein, aur sensitive kaam kisi locked-down jagah pe.

Vendor lock-in ko yes/no sawal mat samjho — ye ek "rate" hai, matlab agar tumne chorna chaha to kitna mehnga aur mushkil hoga. Aur "ownership drift" ek dheeme dheeme hone wala nuqsan hai — jab tumhare critical pieces vendor ke black box mein zyada se zyada shift hote jate hain, aur pata bhi nahi chalta.

## Zaroori Concepts

### The 4 questions
Home choose karne se pehle 4 sawal poochho: **User kaun hai?** (developer, end-user, internal ops...), **Kya cheez tumhe khud own karni hai?** (data, credentials, model, logs...), **Koi insaan wait kar raha hai?** (interactive ya fully unattended), aur **Buri raat ki keemat kya hogi?** (paisa, reputation, safety, compliance).

### Mixing homes
Ye bilkul normal aur smart hai ke alag alag system ke hisse alag alag homes mein rahein.

### Lock-in as a rate
Vendor lock-in yes/no event nahi, ek rate hai — dekho leaving kitni mehngi aur slow hai, aur design aisi rakho ke ye rate acceptable rahe.

### Ownership drift
Jab critical control chupke se vendor ke black box mein chala jata hai. Isse bachne ka tareeqa periodic review hai.

### A worked example: when even Home 3 isn't enough
Ayesha (Part 2 wali) ab paanch clients serve karti hai, aur ek bank client ki demand hai ke uska data unki apni infrastructure pe rahe. Q1 se Home 1 out ho jata hai kyunke doosre log depend karte hain. Q2 asal deciding factor hai — agar bank ka "must" data/execution tak mehdood hai to self-hosted sandbox ke sath managed control plane kaafi hai. Lekin agar demand control plane tak (prompts, sessions, model) pohanche, to sirf owned runtime hi jawab hai. Yahin se Mode 2 — apna custom agent infrastructure banana — shuru hota hai.

### Lock-in is a rate, not a yes/no event
Lock-in aksar leak hota hai, sign nahi hota — ek rule sirf vendor-side setting mein tweak hua, ek eval case sirf console mein add hua, ek bar dashboard mein renegotiate hua bina commit ke. Test simple hai: periodically try karo ke repo se hi fresh home configure ho jaye — agar nahi hota, to leak abhi chhota hai, pakad lo. Ownership drift ka defense hai calendar reminder rakhna taake per-category reports actually padhe jayein, sirf dashboard exist karne se kaam nahi chalta.

## Exam Mein Ye Kyun Aayega?

Ghalat home choose karna mehnga aur short term mein reverse karna mushkil hota hai — exam chahta hai tumhare paas ek decision framework ho, sirf favorite tool nahi.
