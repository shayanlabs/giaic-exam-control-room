# 33. Part 2 — Headless Is the Bridge

## Aasan Zabaan Mein Samjho

"Headless" ka matlab hai loop bina kisi insaan ke screen dekhe bhi chal sakta hai. Socho jaise ek naukar itna trained ho jaye ke usko roz roz samne khare ho ke instructions dene ki zaroorat na rahe — bas ek baar taskeel karo aur wo apna kaam kar leta hai.

Cloud scheduling wo pull hai jo "jab tak mai dekh raha hoon tab chalta hai" se "mai so raha hoon tab bhi chalta hai" ke darmiyan hai. Ye bridge crossing karna itna mushkil nahi jitna lagta hai — kyunke tumne pehle hi headless mode use kiya hua hai bina jaane. Jab bhi tumne `claude -p` ya `opencode run` chalaya, wo agent ek command ki tarah chala tha, conversation ki tarah nahi — koi window khuli nahi thi, bas ek prompt gaya aur output aaya. Yehi principle Home 2 (cloud schedule) ke peeche hai: jo bhi cheez command chala sakti hai — shell script, cron job, CI runner — wo tumhara agent bhi chala sakti hai.

Lekin ek zaroori rule yaad rakhna: headless run zor se fail hona chahiye. Agar exit code koi check nahi kar raha, to ek failed run chupke se guzar jayega aur kisi ko pata bhi nahi chalega.

## Zaroori Concepts

### Home 2 (cloud schedule)
Char homes mein se ek — loop ko cloud ka clock start karta hai, aur wo aise environment mein chalta hai jisko tumhara laptop khula hone ki zaroorat nahi.

### The minimum unattended kit
Loop ko bina dekhe chalane se pehle ye 6 cheezein zaroor honi chahiye: **Idempotency** (dobara chalne se double asar na ho), **missed-run detection** (pata chale agar scheduled run start hi nahi hui), **concurrency lock** (do runs ek dusre ko tabahi na macha dein), **credentials** (secrets safely available hon), **time limits** (run hamesha ke liye na chale), aur **cost limits** (unlimited paisa kharch na ho).

### Headless is something you already built
Eval runner ke `claude -p` aur `opencode run` calls dikhate hain ke headless mode koi naya concept nahi — ye tumne pehle hi use kar liya tha. Bas ab isko schedule pe daalna hai.

### A worked example: Ayesha's invoicing loop
Ayesha, Lahore mein, ek freelance-invoicing loop chalati hai. Roz shaam 6 baje client ko invoice bhejna hota hai, lekin load-shedding aksar ussi waqt bijli le jati hai. Uska masla sirf clock ka hai — loop khud theek kaam karta hai — is liye schedule ko cloud runner (Home 2) pe move karna kaafi hai. Lekin scheduler bhi sirf "around" ek time promise karta hai, "exactly" nahi — isi liye missed-run detection aur 6:30 tak alarm jaisi cheezein zaroori hain taake "bina fail" ka wada asli mein pura ho.

## Exam Mein Ye Kyun Aayega?

Headless wo pehla pull hai jo zyada tar students cross karenge — aur ye 6 controls hi minimum safety net hain jo bina samjhe koi bhi loop unattended nahi chorna chahiye.
