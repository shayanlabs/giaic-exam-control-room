# 19. Routines Appendix

## Aasan Zabaan Mein Samjho

Routines Claude Code ka apna built-in tareeka hain jisse kaam cloud mein chalta hai bina tumhare dekhe. Socho tum ek alarm set karte ho aur kisi ko bol dete ho "har subah 9 baje ye kaam kar dena" — bas Routine bhi wahi karta hai, sirf ye insaan nahi, ek AI agent hai jo scheduled ya event-based tareeke se khud chal padta hai.

Ye appendix ek practical field guide hai — Routine banate waqt konsi form fields bharni hain, ye kin tareeqon se start ho sakti hai, secrets kaise safely handle hote hain, aur konsi safety limits follow karni zaroori hain.

Sabse zaroori cheez jo naye log ghalat samajhte hain wo hai Local vs Remote ka farq — dono naam sunne mein milte julte lagte hain lekin karte bilkul alag kaam hain. Isi tarah "two-routine gate" ek practical trick hai jisse tum bina insaan ke beech mein aaye bhi approval process bana sakte ho.

## Zaroori Concepts

### Har form field
Routine banate waqt jo boxes bharne hote hain: prompt, kaunse repositories ko touch kar sakta hai, kaunse connectors use kar sakta hai, schedule, waghera.

### Teeno triggers
Routine start hone ke different tareeke — time-based, event-based, aur teesra supported type.

### Secrets
Passwords aur API keys ko safely store karke Routine ko diya jata hai taake wo logs ya prompt text mein nazar na aayein.

### Two-routine gate
Ek practical safety rule jo limit karta hai ke Routines ek dusre ko kaise start kar sakti hain. Ye automation ki runaway chains rokta hai.

### Claude-branch rule
Ye concrete rule batata hai ke Routine kis Git branch par kaam kar sakti hai (aam tor par ek special branch). Isse Routine galti se main line of work ko damage nahi karti.

### Daily run caps
Ek din mein Routine kitni baar fire ho sakti hai, uski hard limit. Ye tumhare paise aur safety dono ko protect karti hai.

### Local vs Remote — ye mix-up ek pura din barbad kar sakta hai
Desktop app ke "New routine" button mein **Remote** ya **Local** ka choice hota hai, aur naye log yahin confuse ho jate hain. **Remote** asli cloud Routine banata hai jo is appendix ka topic hai — ye Anthropic ke servers par chalti hai, tumhara laptop band ho tab bhi. **Local** ek bilkul alag feature banata hai, ek Desktop scheduled task, jo tumhari real files par chalta hai (unsaved changes samet) lekin sirf jab tak tumhari machine on ho. Practical workflow: pehle prompt ko one-off run ya Desktop task se prove karo, phir jab sahi chal jaye tab usko scheduled cloud Routine mein promote karo.

### Two-routine gate — worked example
Routine apna prompt start se end tak chalati hai, beech mein rukna ya tumse poochna nahi ho sakta — is liye ek real approval gate do Routines *ke beech* mein banti hai, ek ke andar nahi. **Routine A** (drafter) schedule par fire hoti hai aur kaam draft karti hai — `claude/` branch, Slack summary, draft email — bina ship kiye. **Ek insaan** draft parhta hai aur decide karta hai. Sirf uski approval **Routine B** (executor) ko uske API trigger se fire karti hai — ek POST request uske `/fire` endpoint par, ek bearer token ke saath jo sirf ek baar dikhta hai, is liye usse turant save karna zaroori hai. Routine B phir asli action karti hai: send, merge, deploy, pay. Ye wahi human gate hai jo main loop-engineering course mein tha, sirf ab poori tarah Routine primitives aur ek webhook se bana hua hai.

## Exam Mein Ye Kyun Aayega?
Routines wo pehla tareeka hain jinse zyada tar students pehli baar sacchi unattended loops experience karte hain. Exam mein practical controls aur safety features ki familiarity expected hai.
