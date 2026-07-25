# 32. Part 1 — The Last Dependency

## Aasan Zabaan Mein Samjho
Dekho, jab tak koi loop sirf tumhare laptop pe chalta hai aur tum saamne baithe usay dekh rahe ho, wo bas ek personal tool hai. Koi masla nahi. Lekin jaise hi usay bina tumhare chalna padta hai — matlab tum so rahe ho ya kahin aur busy ho — ek naya sawal khada ho jata hai: ye kaam actually kahan hoga, aur usay start kaun karega?

Isay "last dependency" isliye bolte hain kyunke ye series ka aakhri step hai. Pehle maker-checker wale idea ne ek akeli, bina-check ki hui raay ka masla khatam kiya. Phir harness ne bina-nigrani wale actions ka masla hal kiya. Phir evals ne aise checker ka masla suljhaya jo khud check nahi hota tha. Ab jo bacha hai wo tumhari judgment nahi — insaan wala gate to sahi jagah pe hi rehta hai — bacha hai tumhara **hardware**: laptop khula hona, session login hona, machine on aur network pe hona.

Jis din system tumhare laptop se zyada reliable ho jaye, samjho wo apne ghar se bada ho chuka hai. Ab time hai naya ghar dhoondne ka.

Iske liye do cheezein clear honi chahiye:
1. **Control plane** — decide karta hai kya chalega, kab, aur kitni permission ke saath.
2. **Execution plane** — jahan actual kaam, tools, aur side-effects hote hain.

Sawal hamesha yehi hai: loop ko chalata kaun hai, aur kaam ho kahan raha hai?

## Zaroori Concepts

### Control plane vs Execution plane
Control plane decide karta hai "kya" aur "kab"; execution plane wo jagah hai jahan asal mein kaam hota hai. Dono alag ho sakte hain — jaise ek company decide kare aur dusri jagah kaam ho.

### The last single point of failure
Baaki sab risks fix ho chuke — akeli raay, bina-nigrani action, bina-check checker. Ab sirf tumhara hardware hi weak link hai.

### 4 homes
1. **Home 1 (tumhara session)** — sab kuch tumhare control mein, banane ke liye theek, depend karne ke liye risky.
2. **Home 2 (cloud schedule)** — wahi rules aur skills, bas clock kisi aur ke computer pe chali jaati hai.
3. **Home 3 (managed runtime)** — vendor control plane sambhalta hai, execution plane unka ya tumhara ho sakta hai.
4. **Home 4 (apna process)** — harness khud tumhare likhe software ke andar ek library ban jata hai, ye Agent SDK ka ilaka hai.

Ye 4 options hain, koi ladder nahi — har loop ke liye alag se choose karna hota hai.

## Exam Mein Ye Kyun Aayega?
Laptop chhodna wo moment hai jab ek personal experiment asli system banta hai. Exam mein control plane aur execution plane ka farq clear hona chahiye.
