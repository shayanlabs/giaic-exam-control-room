# 29. Part 3 — Calibrating the Judge

## Aasan Zabaan Mein Samjho

Agar judge khud unreliable hai, toh poora evaluation system sirf ek tamasha hai, kuch aur nahi.

Calibration wo kaam hai jisse judge ke scores ko jitna ho sake reality ke kareeb laya jata hai.

## Zaroori Concepts

### Anchored rubrics
Rubrics jinme concrete examples hote hain ke "achha," "acceptable," aur "bura" kaisa dikhta hai. Anchors subjectivity kaafi kam kar dete hain.

### Bar ek decision hai
Pass/fail line koi natural fact nahi. Ye decision hai ke tum kitna risk lene ko taiyar ho. Is decision ko explicit banao.

### Grader ko grade karo
Judge ko time time par human ground truth ke against check karna zaroori hai. Judge ko bhi ek system samjho jise khud evaluation chahiye.

### 4-cell table
True Pass / False Pass / True Fail / False Fail.
Jo cell usually sabse zyada matter karti hai wo hai **false pass** — wo cases jo judge ne theek bola lekin asal mein bure the.

### Judge se pehle rubric fix karo
Jab scores ghalat lagein, pehle rubric aur anchors dekho, model ko nahi.

### "Grade the grader" protocol, step by step
Source ek concrete ek-shaam ka protocol deta hai jise "grade the grader" kehte hain: jaan bujh kar bees graded items sample karo (real mix — FAILs aur borderline cases, aasan PASSes nahi, kyunke sab-obvious items par agreement chance se zyada hoti hai aur asal truth chupa deti hai); unhe blind grade karo, judge ke verdicts dekhne se pehle; compare karo aur disagreements ko 4-cell table mein sort karo; phir model chhedne se pehle rubric fix karo. Source ka rough guide: 9-in-10 se zyada overall agreement, high-severity items par zero false passes ke saath, matlab judge ne apni jagah kama li hai — kisi "obvious" case par ek bhi false pass matlab number par bharosa karna band karo jab tak fix na ho.

### Worked example — surface bias ko pakarna
Socho judge aur insaan 20 mein se 6 items par disagree karte hain, aur inme se paanch aisi cases hain jahan judge ne lamba, confident, achi tarah formatted kaam ko pass kar diya jo insaan ne fail kiya. Is pattern ka naam hai — surface bias, judge kaam ki jagah costume grade kar raha hai — aur source ke mutabiq pehla fix kabhi model badalna nahi. Pehla fix hai rubric ko dobara likhna taake wo fact-checkable sawaal poochhe ("kya diff ek test remove karti hai?") impression sawaal ki jagah ("kya ye achha hai?"), phir calibration dobara chalao model badalne se pehle.

## Exam Mein Ye Kyun Aayega?
Uncalibrated judge, judge na hone se bhi bura hai kyunke ye false confidence deta hai. Exam chahta hai tumhe calibration discipline pata ho.
