# 24. Part 5 — A Complete Harness

## Aasan Zabaan Mein Samjho

Ye part sab pieces ko jod kar ek minimum safe harness banata hai. Phir wahi "ek buri raat" ki story do baar sunata hai — ek baar harness ke saath, ek baar bagair. Farq bohot bada hai.

Socho ek hi accident do alag gaadiyon mein hota hai — ek mein airbags aur seatbelt hain, dusri mein nahi. Result bilkul alag hoga chahe crash same ho. Yehi baat harness ke saath bhi hai — same agent, same model, same malicious situation, lekin harness ki wajah se ending bilkul badal jati hai.

## Zaroori Concepts

### Minimum safe harness checklist
Agent ko koi bhi real power dene se pehle tumhare paas kam se kam ye hona chahiye:
- Khatarnak actions ke liye deny list
- Fences (folders, network, branches)
- Sirf wahi tools jo waqai zaroori hain
- Ek blocking hook ya hard stop
- Success ya failure judge karne ka structured tareeka
- Insaan ko bulane ka saaf rasta
- Logging taake pata chale kya hua
- Undo ya recover karne ka tareeka

### Ek buri raat, harness ke saath aur bagair
Ek concrete story jo dikhaati hai ke same sequence of events kaise bilkul alag anjaam par pahunchti hai, sirf is baat par ke structural controls maujood the ya nahi.

### Ek buri raat, poori tarah dekhi hui
Same loop, same model, same malicious issue raat ko queue mein — sirf harness badalta hai. **Harness ke bagair**: agent, injected instruction ke isharon par, `.env` parhta hai (kuch nahi rokta), `curl` se file bahar bhej deta hai (kuch nahi rokta), ek failing test ko delete karke "fix" karta hai, aur reviewer kehta hai "PASS — tests ab green hain" kyunki test simply gayab ho chuka hai; PR khulti hai aur half-asleep merge ho jati hai. **Harness ke saath**: `.env` ka read deny rule se block aur log ho jata hai, `curl` exfiltration network fence se block aur log ho jata hai, test delete hoti hai aur suite waqai green ho jati hai — lekin diff parhne wala reviewer wo pakad leta hai jo sirf tests nahi pakad sakte ("test deleted, not fixed," risk: high) aur wo item "needs a human" mein chala jata hai, ship nahi hota. Neeche ka sabak: harness ne model ko smart nahi banaya — usne *system* ko honest banaya, bad actions namumkin banayin aur bad work ko visible banaya.

### Aath boxes, do owners
Wahi minimum-safe-harness checklist alag tools mein alag tareeke se implement hoti hai, aur real debugging ke liye ye pata hona zaroori hai ke konsa box kis owner ke paas hai. Claude Code mein zyada tar boxes khud tool ke andar rehte hain: `settings.json` deny list rakhti hai, sandbox aur worktrees fence hain, hooks blocking checks hain, aur `/rewind` plus git wapas jaane ka rasta dete hain. OpenCode mein kai boxes platform ki taraf shift ho jate hain: fence ek container-aur-worktree combination ban jati hai, blocking hook pre-commit plus required CI ban jata hai, aur log GitHub Actions workflow log ban jata hai — jab ke typed verdict aur escalation path dono jagah repo files ke tor par same rehte hain. Wahi aath boxes, wahi property guaranteed, lekin address alag hota hai is baat par ke tum kaunsi harness mein khade ho.

## Exam Mein Ye Kyun Aayega?
Tumhe parts se ek complete, safe harness assemble karna aana chahiye. Checklist aur "buri raat" ki story hi is ability ka practical test hain.
