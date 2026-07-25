# 30. Part 4 — Evals in the Loop

## Aasan Zabaan Mein Samjho

Evals tabhi kaam ke hain jab wo development process ka zinda hissa hon, na ke ek one-time report jo shelf par pari rahe. Ye part is baat par hai ke jab product aur golden set badalte rahein, tab evaluation system ko khud kaise healthy rakha jaye.

Socho tum ek gym routine follow kar rahe ho — sirf ek din weight measure karke bhool jaana kaafi nahi, tumhein regularly measure karte rehna hai, baselines set karni hain, aur ye samajhna hai ke ek din ka farq real progress hai ya bas normal fluctuation. Evals ko bhi isi tarah continuous rakhna zaroori hai.

## Zaroori Concepts

### Regression suite
Golden set (ya uska bada hissa) har important change par automatically chalaya jata hai taake regressions jaldi pakdi jayein.

### Drift aur baselines
Models, prompts, aur tools badalte rehte hain. Scores drift karte hain. Tumhein baselines chahiye aur ek saaf process ke ye decide karne ke liye ke score mein farq real improvement hai ya sirf drift.

### Set badalne par re-baseline karo
Agar tum cases add ya remove karte ho, to purane numbers ab comparable nahi rahe. Jaan-boojh kar re-baseline karo.

### Smoke / full / hold-out tiers
- **Smoke**: ek chota, tez set jo hamesha chalta hai.
- **Full**: pura golden set.
- **Hold-out**: wo cases jo development process ko dekhne ki ijazat nahi, final honesty checks ke liye use hoti hain.

### HOW MANY se pehle WHICH parho
92% se 87% ka drop us se kam useful hai jitna ye jaanna ke *kaunsi* cases flip hui aur kyun. Hamesha pehle failures ko dekho.

### Baseline sirf ek number se zyada hai
Source ek concrete `baseline.json` shape dikhata hai: ek `recorded` date, `reviewer_model`, `rubric_version`, ek `overall` rate, ek `by_category` breakdown, aur koi bhi drop kis ne `approved_by` kiya. Reasoning matter karti hai — jo rate bina record ke ho ke usay kis cheez ne banaya, wo aisa number hai jise tum baad mein interpret hi nahi kar sakte, aur rule ye hai ke baseline sirf *neeche* ja sakta hai agar usi commit mein explicit written approval ho, taake apni suite ko behtar banana kabhi galti se punish na ho.

### Teen runs kya bata sakte hain aur kya nahi
Source is baare mein bohot careful hai: har case ke liye teen runs ek sasta development setting hai, ek smoke signal, koi stable estimate nahi — 3-of-3 ka matlab ye nahi ke true pass rate 100% ke qareeb hai, iska matlab hai ke teen sampled attempts pass hue. Fix ye hai ke sample ko decision ke hisaab se scale karo: iterate karte waqt teen runs, release decision ke liye zyada runs (jab tak result move hona band na ho jaye), aur sabse zyada risk wali categories ke liye bade samples plus human review. Isi liye note ka "HOW MANY se pehle WHICH" rule bhi hai — 92% se 87% ka drop kuch nahi batata jab tak tumhein pata na ho ke naye fail hone wale cases tone ki mamuli baat hain ya `deleted-test-001` jaisi false green.

## Exam Mein Ye Kyun Aayega?
Evals jo loop mein integrate nahi kiye jate, jaldi stale aur misleading ban jate hain. Exam mein ye jaanna zaroori hai ke inhe zinda aur trustworthy kaise rakha jaye.
