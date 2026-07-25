# 29. Part 3 — Calibrating the Judge

## Aasan Zabaan Mein Samjho

Agar judge khud hi unreliable hai, to poora evaluation system sirf ek dikhawa (theater) hai. Calibration wo kaam hai jisse judge ke scores ko jitna ho sake reality ke qareeb laaya jata hai.

Socho ek exam mein checker khud hi confuse ho ke sahi answers ko galat aur galat ko sahi mark kar de — chahe questions kitne hi acha bane hon, exam ka natija bekaar hoga. Isi liye judge ko khud bhi kabhi kabhi "test" karna zaroori hai — usay bhi ek exam dena parta hai.

## Zaroori Concepts

### Anchored rubrics
Rubrics jin mein "acha," "acceptable," aur "bura" kaisa dikhta hai iske concrete examples shamil hon. Anchors subjectivity ko kaafi kam kar dete hain.

### Bar ek decision hai
Pass/fail ki line koi natural fact nahi hai. Ye ek decision hai ke tum kitna risk lene ko tayyar ho. Is decision ko explicit banao.

### Grading the grader
Judge ko waqt waqt par human ground truth ke khilaf check karna zaroori hai. Judge ko bhi ek aisa system samjho jise khud evaluation ki zaroorat hai.

### 4-cell table
True Pass / False Pass / True Fail / False Fail.
Jo cell aam tor par sabse zyada matter karta hai wo hai **false pass** — wo cases jinhe judge ne "theek hai" kaha lekin asal mein wo bure the.

### Model se pehle rubric fix karo
Jab scores ghalat lagein, sabse pehle rubric aur anchors dekho, judge ke peeche wale model ko nahi.

### Grade-the-grader protocol, qadam ba qadam
Source ek concrete ek-dopeher ka protocol deta hai jise "grade the grader" kehte hain: jaan-boojh kar bees graded items ka sample lo (FAILs aur borderline cases ka ek real mix, easy PASSes nahi, kyunki sab obvious items par agreement chance se hi zyada hota hai aur asal truth chhupa deta hai); unhein blind grade karo, judge ke verdicts dekhne se pehle; compare karo aur disagreements ko 4-cell table mein sort karo; phir model ko haath lagane se pehle rubric fix karo. Source ka ek rough guide: 9-in-10 se zyada overall agreement, high-severity items par zero false passes ke sath, matlab judge ne apni jagah kama li hai — kisi bhi "obvious" case par ek bhi false pass ka matlab hai ke number par bharosa karna band karo jab tak wo fix na ho jaye.

### Worked example: surface bias ko rangey haath pakadna
Socho judge aur ek insaan 20 mein se 6 items par disagree karte hain, aur un chhe mein se paanch aise cases hain jahan judge ne lamba, confident, well-formatted kaam pass kar diya jise insaan ne fail kiya. Is pattern ka ek naam hai — surface bias, jahan judge kaam ki bajaye "costume" ko grade kar raha hai — aur source ke mutabiq iska pehla fix kabhi model swap karna nahi hota. Iska fix rubric ko rewrite karna hai taake wo fact-checkable sawal poochhe ("kya diff ek test hataata hai?") impression wale sawalon ki bajaye ("kya ye acha hai?"), phir calibration dobara chalao model swap sochne se pehle.

## Exam Mein Ye Kyun Aayega?
Ek uncalibrated judge, judge na hone se bhi bura hai kyunki ye false confidence banata hai. Exam mein calibration discipline samajhna zaroori hai.
