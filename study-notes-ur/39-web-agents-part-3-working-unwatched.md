# 39. Part 3 — Working Unwatched

## Aasan Zabaan Mein Samjho
Ye poore stack ka asal maqsad hai — agent kaam kare jab tumhara koi bhi device online na ho. Pattern simple hai: brief do, plan dekho, approve karo, phir jab kaam ho jaaye to review karo. Koi bhi step skip kiya to risk badh jaata hai.

Sochne wali baat: desktop agent pe tum kaam chalte hue dekh sakte ho, beech mein rok sakte ho. Web surface pe tum chale jaate ho — yehi to poora point hai — isliye plan step hi tumhara asli, shayad akela, intercept hota hai niyat aur finished kaam ke beech. Agar "pehle apna plan batao, phir meri approval ka wait karo" wali line skip ki, to pehli baar galti tab pakdi jaayegi jab wo poori task mein har file ke saath ho chuki hogi. Plan review mein bas 4 cheezein check karo, do minute lagte hain: scope sirf wahi hai jo maine bola tha? koi cheez verify hone se pehle act to nahi kar rahi? koi connector ya send maanga jo maine nahi maanga tha? format ya audience ke baare mein kya chup-chap assume kar liya? Ek line ka redirect plan stage pe kuch nahi lagta, lekin ek confidently execute ho chuki galti saaf karne mein poora din lag sakta hai.

## Zaroori Concepts

### Delegation loop
Brief → plan → approve → review. Clear brief do, system plan proposal kare, tum approve karo, kaam ho, phir review karo.

### Scheduled tasks, koi device online nahi
Session vendor ke servers pe rehta hai, schedule pe fire ho sakta hai chahe tumhare saare laptop-phone off hon.

### Schedule ke 4 jawab
Achi schedule config batati hai: kab chalega, kya karne ki ijazat hai, kaise report karega, aur fail hone pe kya hoga.

### Reporting vs acting
Sirf report dene wale agent aur duniya mein actions le sakne wale agent mein bada farq hai. Permission boundary clear honi chahiye.

### Ayesha ki misaal — report vs act
Ayesha do scheduled tasks chahti hai: Monday morning unpaid invoices ka summary (Drive se padho, brief account mein save karo) — ye reporting hai, ghalat week ka matlab bas rewrite. Aur Friday ko har late client ko automatic payment reminder email — ye act karna hai, duniya mein bahar, unattended, cadence pe, aur ghalat run ka matlab real clients ko galat email jaana, bina kisi check ke. Ek lafz ka farq — **acting** vs reporting — decide karta hai kya abhi safe hai aur kya deeper tooling (checker, stopping condition, saved state) ka wait kare.

## Exam Mein Ye Kyun Aayega?
Sach mein bina dekhe kaam hona hi is poori chain ki economic wajah hai. Exam mein delegation pattern aur safety boundaries ki samajh chahiye.
