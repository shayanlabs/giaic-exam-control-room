# 33. Part 2 — Headless Is the Bridge

## Aasan Zabaan Mein Samjho
Dekho, "headless" ka matlab seedha hai — loop chalega, lekin koi screen pe baith kar nahi dekhega. Cloud scheduling isi cheez ka pul hai: "jab main dekh raha hoon tab chalta hai" se "jab main so raha hoon tab bhi chalta hai" — is beech ka connection.

Maza ki baat ye hai ke tumne ye pul pehle hi paar kar liya hai, bina bataye. Eval runner mein jo `claude -p` ya `opencode run` commands chalate ho — wahi headless mode hai. Koi khula window nahi, bas prompt gaya, kaam hua, output aaya. Yehi wo idea hai jis pe Home 2 khada hai: jo bhi cheez command chala sakti hai — shell script, cron job, CI runner, cloud scheduler — wo ab tumhara agent bhi chala sakti hai. Bas ek rule yaad rakho: headless runs ko loudly fail hona chahiye, kyunke jo exit code koi check hi nahi karta, wo silently miss ho jaata hai.

Ab is mode pe bharosa karne se pehle, 6 cheezein pakki honi chahiye — inhe "minimum unattended kit" bolte hain.

## Zaroori Concepts

### Home 2 (cloud schedule)
4 homes mein se ek — loop cloud clock se start hota hai, aisi jagah chalta hai jahan tumhara laptop khula hone ki zaroorat nahi.

### Minimum unattended kit
1. **Idempotency** — do baar chale to double effect na ho.
2. **Missed-run detection** — pata chale agar scheduled run start hi nahi hua.
3. **Concurrency lock** — do runs ek dusre ke upar na chadhein.
4. **Credentials** — secrets safely available hon.
5. **Time limits** — run hamesha ke liye na chale.
6. **Cost limits** — run unlimited paisa na uda de.

### Ayesha ka invoicing loop
Ayesha Lahore mein freelance invoicing loop chalati hai, aur load-shedding roz shaam 6 baje bijli le jaati hai — bilkul us waqt jab client daily invoice expect kar raha hota hai. Uska masla sirf clock ka hai, loop to sahi kaam kar raha hai — to schedule ko cloud runner (Home 2) pe le jaana hi solution hai. Lekin dhyan rahe, scheduler bhi sirf "around" ek time promise karta hai, "exact" nahi — isliye missed-run detection aur 6:30 tak kuch na chale to alarm, yehi asal mein "without fail" deliver karta hai, akela scheduler nahi.

## Exam Mein Ye Kyun Aayega?
Headless wo pehla pul hai jo zyada tar log paar karte hain. Ye 6 controls minimum safety net hain, exam mein inka pata hona chahiye.
