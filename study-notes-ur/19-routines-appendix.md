# 19. Routines appendix

## Aasan Zabaan Mein Samjho

Routines Claude Code ka built-in tareeqa hai jisse kaam cloud mein chalta hai, bina tumhare dekhe. Matlab so jao, laptop band karo, kaam phir bhi chalta rahega.

Ye appendix ek practical field guide hai — har form field jo tum fill karte ho, Routine start karne ke saare tareeqe, secrets kaise handle hote hain, aur wo safety limits jo tumhe follow karni hain.

## Zaroori Concepts

### Har form field
Concrete boxes jo Routine banate waqt fill karne padte hain: prompt, kaun se repositories touch kar sakta hai, kaun se connectors use kar sakta hai, schedule, waghera.

### 3 triggers
Routine start hone ke alag tareeqe (time-based, event-based, aur teesra supported type).

### Secrets
Passwords aur API keys kaise safely store hote hain aur Routine ko diye jate hain — taake wo logs ya prompt text mein kabhi na dikhein.

### Two-routine gate
Ek practical safety rule jo control karta hai Routines ek dusre ko kaise start kar sakti hain. Automation ki runaway chain rokta hai.

### Claude-branch rule
Ek concrete rule ke Routine kaunsi Git branch par kaam kar sakti hai (aksar ek special branch). Isse Routine galti se main line ka kaam kharab nahi karti.

### Daily run caps
Ek Routine din mein kitni baar chal sakti hai, uski hard limit. Ye tumhare paise aur safety, dono ko protect karta hai.

### Wo confusion jo pura din barbaad kar deta hai — Local vs Remote
Desktop app ke "New routine" button mein do options milti hain — **Remote** ya **Local** — aur naam pehli baar mein sabko confuse karte hain. **Remote** asal cloud Routine banata hai jiski ye appendix baat kar rahi hai — ye Anthropic ke servers par chalta hai, laptop band ho phir bhi. **Local** ek bilkul alag feature banata hai, ek Desktop scheduled task, jo tumhari asal files par kaam karta hai (unsaved changes samet) lekin sirf tab jab tumhara machine on ho. Practical tareeqa yehi hai: pehle prompt ko one-off run ya Desktop task ki tarah test karo, jab theek chal jaye tab usay scheduled cloud Routine bana do.

### Two-routine gate — worked example
Chunke Routine apna prompt shuru se end tak khud chalati hai, beech mein rok kar tumse poochh nahi sakti — isliye asal approval gate do Routines ke *beech* mein rakhna padta hai, ek ke andar nahi. **Routine A** (jo draft banati hai) schedule par chalti hai aur kaam draft karti hai — `claude/` branch, Slack summary, draft email — bina usay ship kiye. **Insaan** ye draft padh kar decide karta hai. Sirf yahi approval **Routine B** (jo execute karti hai) ko uske API trigger se fire karti hai — uske `/fire` endpoint par ek POST, saath ek bearer token jo sirf ek baar dikhaya jata hai, isliye usay foran store karna zaroori hai. Routine B phir asal action leti hai: send karna, merge karna, deploy karna, pay karna. Ye wahi human gate hai jo main loop-engineering course mein tha, bas ab Routine primitives aur ek webhook se bana hai.

## Exam Mein Ye Kyun Aayega?
Routines hi wo pehli jagah hai jahan zyada tar students pehli baar asal unattended loop mehsoos karte hain. Exam ko practical controls aur safety features ki jaan-pehchan chahiye hogi.
