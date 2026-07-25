# 39. Part 3 — Working Unwatched

## Aasan Zabaan Mein Samjho

Ye poori web-agents stack ka asal maqsad hai — agent tumhare kisi bhi device ke online hue bina useful kaam kar sake. Iska tareeqa ek clear delegation loop hai jisme scheduled execution aur explicit reporting shamil hai.

Socho jaise tum kisi trusted assistant ko ek kaam de kar chutti pe chale jao — pehle tum usse brief karte ho, wo apna plan batata hai, tum approve karte ho, phir wo kaam karta hai, aur wapis aa kar tum uska review karte ho. Agar tum in steps mein se koi bhi skip karo, risk barh jata hai.

Sabse important cheez samajhne wali ye hai ke sirf "report banana" aur "asal duniya mein action lena" mein zameen-aasman ka farq hai — permission boundary bilkul clear honi chahiye.

## Zaroori Concepts

### The delegation loop
brief → plan → approve → review. Tum clear brief dete ho, system plan proposes karta hai, tum approve karte ho, kaam hota hai, phir tum review karte ho. Koi bhi step skip karna risk barhata hai.

### Scheduled tasks with no device online
Technical haqeeqat ye hai ke session vendor ke servers pe rehta hai aur schedule pe chal sakta hai chahe tumhara koi bhi laptop ya phone band ho.

### The 4 answers of a schedule
Achi schedule configuration char sawalon ka jawab deti hai: kab chalega, kya karne ki ijazat hai, kaise report karega, aur fail hone pe kya hoga.

### Reporting vs acting
Ek agent jo sirf report banata hai aur ek agent jo asal duniya mein action bhi le sakta hai — dono mein bara farq hai. Permission boundary explicit honi chahiye.

### Why the plan step is the real safety net
Desktop agent pe tum kaam chalte hue dekh sakte ho aur beech mein rok sakte ho. Web surface pe tum chale jate ho — yehi to iska point hai — is liye plan hi tumhara ikalauta intercept hota hai galti pakadne ka. Plan review karte waqt char cheezein 2 minute mein check karo: scope sirf wahi hai jo tumne kaha tha? Kuch verify hone se pehle act to nahi kar raha? Koi connector ya send jo tumne nahi manga wo use to nahi ho raha? Aur format/audience ke baare mein wo chupke se kya assume kar raha hai? Ek line ka redirect plan stage pe free hai; ek confidently execute hui ghalat run saaf karne mein poora din lag jata hai.

### The invoicing example: reporting vs acting, made concrete
Ayesha do scheduled tasks chahti hai — Monday morning unpaid invoices ka summary (sirf read aur report), aur Friday ko late clients ko automatic payment reminder emails. Monday wala reporting hai — ghalat hafta bas rewrite ki keemat rakhta hai. Friday wala **act** karta hai duniya mein unattended — ghalat run sach much clients ko email bhej degi bina kisi check ke. Farq ka ek lafz: **acting** vs reporting.

## Exam Mein Ye Kyun Aayega?

True unattended kaam hi is poore course ka economic aur practical justification hai — exam expect karta hai tum delegation pattern aur safety boundaries dono samjho.
