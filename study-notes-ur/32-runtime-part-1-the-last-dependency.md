# 32. Part 1 — The Last Dependency

## Aasan Zabaan Mein Samjho

Dekho, jab tak tumhara loop sirf tumhare laptop pe chalta hai aur tum saamne baithe screen dekh rahe ho, tab tak wo ek "personal tool" hai — bas tumhara chota sa khilona. Asal masla tab shuru hota hai jab tum chahte ho ke ye bina tumhare bhi chale. Ab sawal ye uthta hai: kaam actually hoga kahan, aur is baat ka faisla kaun karega ke kaam shuru kab ho?

Isko aise socho — pehle tumne apne kaam ke har weak point ko theek kiya: ek akela banda faisla nahi karta (maker-checker), koi action bina ijazat ke nahi hota (harness), aur checker khud bhi check hota hai (evals). Ab jo aakhri weak point bacha hai wo tumhara laptop hai — agar wo band ho gaya, session logout ho gaya, ya bijli chali gayi, to poora system ruk jayega. Ye hi "last dependency" hai.

Jaise koi dukaan chalane wala banda khud hi cashier, khud hi manager, khud hi security guard ho — jab tak wo dukaan pe hai sab theek hai, lekin jaise hi wo chutti pe gaya, dukaan band. Loop ko aise nahi rehna chahiye.

## Zaroori Concepts

### The 4 homes
Loop ko chalane ki 4 jagah (homes) ho sakti hain — tumhara apna laptop, cloud ka schedule, ek managed service, ya customer ka apna computer. Har jagah ka apna control, cost aur reliability ka trade-off hota hai.

### Control plane vs execution plane
Control plane wo decide karta hai ke kya chalna hai, kab chalna hai, aur kis permission ke sath. Execution plane wo asal jagah hai jahan agent process aur uske tools actually kaam karte hain. Dono alag cheezein hain, aur inhe alag samajhna zaroori hai.

### The last single point of failure
Pehle sab weak points fix ho chuke — sirf ek reh gaya: tumhara hardware, tumhara laptop khula hona, session login hona. Jab system tumhare hardware se zyada reliable ho jaye, to samjho ye ab apni jagah se bahar nikalne ke qabil hai.

### Four homes, concretely
Home 1 (tumhara session) — sab kuch tumhare control mein, banane ke liye theek, lekin bharosa karne ke liye nahi. Home 2 (cloud schedule) — same rules, bas clock kisi aur ke computer pe chala gaya. Home 3 (managed runtime) — vendor control plane sambhalta hai. Home 4 (apna process) — harness tumhare khud likhe software ka hissa ban jata hai. Ye chaaron options hain, koi seedhi nahi ke sab ko chadhna hi hai.

## Exam Mein Ye Kyun Aayega?

Laptop chhorna hi wo moment hai jahan ek personal experiment asal system banta hai — exam mein control aur execution ki separation samajhna zaroori hai.
