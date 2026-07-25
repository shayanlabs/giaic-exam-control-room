# 30. Part 4 — Evals in the Loop

## Aasan Zabaan Mein Samjho

Evals sirf tab madad karte hain jab wo development process ka zinda hissa hon, koi ek-baar ki report jo shelf par pari rahe.

Ye part isi baat ki hai — evaluation system ko khud healthy rakhna, jaise jaise product aur golden set change hote hain.

## Zaroori Concepts

### Regression suite
Golden set (ya uska bara hissa) har important change par automatically chalaya jata hai taake regressions jaldi pakri jayein.

### Drift aur baselines
Models, prompts, tools — sab change hote hain. Scores drift karte hain. Tumhe baselines chahiye aur ek clear process ke score ka change asal improvement hai ya sirf drift.

### Set change ho toh re-baseline karo
Agar cases add ya remove karo, purane numbers ab comparable nahi rehte. Jaan bujh kar re-baseline karo.

### Smoke / full / hold-out tiers
- **Smoke**: chota, tez set jo hamesha chalta hai.
- **Full**: poora golden set.
- **Hold-out**: cases jo development process ko dekhne nahi diye jate, final honesty checks ke liye.

### HOW MANY se pehle WHICH padho
92% se 87% girna itna useful nahi jitna ye jaanna ke *kaunsi* cases flip hui aur kyun. Hamesha pehle failures dekho.

### Ek baseline ek number se zyada hai
Source ek concrete `baseline.json` shape dikhata hai: ek `recorded` date, `reviewer_model`, `rubric_version`, `overall` rate, `by_category` breakdown, aur kisi bhi girawat ka `approved_by`. Reasoning matter karti hai — bina ye record kiye ke number kaise bana, wo aisa number hai jo baad mein samajh nahi aayega, aur rule ye hai ke baseline sirf *neeche* usi commit mein explicit written approval ke saath ja sakta hai — taake apni khud ki suite behtar karna kabhi accidentally punish na ho.

### Teen runs kya bata sakte hain, kya nahi
Source is baat mein careful hai: teen runs per case ek sasta development setting hai, ek smoke signal, stable estimate nahi — 3-of-3 ka matlab ye nahi ke true pass rate 100% ke qareeb hai, matlab hai teen sampled attempts pass hue. Fix ye hai ke sample decision ke hisaab se badhao: iterate karte waqt teen runs, release decision ke liye zyada runs (jab tak result move karna band na kare), aur sabse high-risk categories ke liye bara sample plus human review. Isi liye "HOW MANY se pehle WHICH padho" rule hai — 92% se 87% girna kuch nahi batata jab tak pata na chale ke naye fail hone wale cases sirf tone quibbles hain ya `deleted-test-001` jaisa false green.

## Exam Mein Ye Kyun Aayega?
Jo evals loop ka hissa nahi bante, wo jaldi stale aur misleading ho jate hain. Exam chahta hai tumhe pata ho unhe zinda aur trustworthy kaise rakhna hai.
