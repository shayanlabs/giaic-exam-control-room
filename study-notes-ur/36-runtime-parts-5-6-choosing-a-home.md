# 36. Parts 5 + 6 — Choosing a home

## Aasan Zabaan Mein Samjho
Ek loop ke liye "sabse best ghar" jaisi koi cheez nahi hoti. Har case alag hai. Chaar sawal poochho, jawab khud mil jaayega:
1. User kaun hai — developer, end-user, internal ops, ya external customer?
2. Kya cheez tumhare control mein honi chahiye — data, credentials, model, logs, vendor badalne ki azadi?
3. Koi insaan wait kar raha hai (interactive) ya poori tarah unattended chal raha hai?
4. Ek buri raat ki cost kya hogi — paisa, reputation, safety, compliance?

Aur ye zaroori nahi ke poora system ek hi ghar mein rahe — development laptop pe, scheduled kaam cloud mein, sensitive execution locked-down environment mein — mix karna bilkul normal hai, aksar smart move hai.

## Zaroori Concepts

### 4 sawal
User kaun hai? Kya must-own hai? Koi wait kar raha hai? Buri raat ki cost kya hai?

### Homes mix karna
Alag alag hisson ko alag alag ghar mein chalana normal aur aksar smart hota hai.

### Lock-in ek rate hai
Vendor lock-in yes/no sawal nahi. Ye ek rate hai — chhodna kitna mehnga aur slow hai. Design aisa rakho ke ye rate acceptable rahe.

### Ownership drift
Dheere dheere, chupke se control kam hota jaata hai jab zyada se zyada critical cheezein vendor ke black box ke andar chali jaati hain. Bachao — periodic review.

### Ayesha ka bank wala case
Ayesha ab 5 clients handle karti hai, ek bank hai jo mangta hai data unki apni infrastructure pe rahe. Home 1 out ho jaata hai kyunke doosre log depend karte hain. Asal sawal Q2 hai — agar bank ka "must" execution aur data tak limited hai, to managed control plane + **self-hosted sandbox** kaafi hai. Lekin agar requirement control plane tak (prompts, sessions, model path) pahunchti hai, to sirf owned runtime hi jawab hai. Yahi wo edge hai jahan sirf tools configure karna kaafi nahi rehta — yahan se Mode 2 (custom agent infrastructure banana) shuru hota hai.

### Lock-in leak hota hai, sign nahi hota
Ek rule jo sirf vendor ke dashboard mein tweak hui, repo mein kabhi copy nahi hui. Ek eval case jo sirf service console mein add hua. Ek bar jo dashboard mein renegotiate hui, commit ke bina. Har ek suitcase se chupke nikalne wali cheez hai. Test simple hai: kabhi kabhi ek fresh ghar sirf repo se configure karne ki koshish karo — agar wo complete na ho sake, leak mil gaya, abhi chhota hai. Ownership drift ka defense bhi simple hai: calendar reminder rakho reports padhne ke liye, sirf dashboard exist karna kaafi nahi.

## Exam Mein Ye Kyun Aayega?
Ghalat ghar choose karna mehenga hota hai aur short term mein reverse karna mushkil. Exam mein ek decision framework chahiye, sirf favorite tool nahi.
