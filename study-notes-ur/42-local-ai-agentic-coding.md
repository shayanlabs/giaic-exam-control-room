# 42. Local AI: Agentic Coding

## Aasan Zabaan Mein Samjho
Ek agent ka "dimaag" bas ek address hai — itni simple baat hai. Agent ko farq nahi padta model data center mein baitha hai ya tumhare apne GPU pe — interface same rehta hai, bas quality aur speed badalti hai. Isi liye same agent tools ko tum apne computer pe chal rahe model ki taraf point kar sakte ho, cloud ki bajaye.

Local AI privacy, offline kaam, aur high volume pe cost bachane ke liye achi hai — lekin sirf tab jab model kaafi smart aur kaafi fast ho.

Do "walls" hain jo local ko rokti hain. Pehli — **capability wall**: model bas kaam ke liye kaafi smart nahi (planning, tool use, long-horizon reasoning). Doosri — **throughput wall**: model smart to hai, lekin strong GPU ke bina bohot slow hai. Ek bada model capability fix karta hai, speed nahi. Ek achha GPU speed fix karta hai, capability nahi.

Tool calls sabse common practical failure spot hai. Healthy tool call koi normal likhawat nahi — ek chhota structured data piece hota hai, jaise `{"type": "tool_use", "name": "edit_file", "input": {"path": "README.md", "old": "Hello", "new": "Hello, world"}}`. Harness ise padh kar edit karta hai, model khud file ko touch nahi karta. Kamzor model `input` ko plain text blob bhej deta hai, harness error de kar reject kar deta hai (jaise `args expected string, got object`), run ruk jaata hai — bas yehi capability wall hai, live dekho to.

Aur ek chhupa hua trap: Ollama ka default context window sirf 4,096 words hai. Harness ki lambi instruction (tool ke rules, har tool ki definition) shuru se chup-chap trim ho jaati hai, aur model ko kabhi pata hi nahi chalta call format kaise karna hai. Kuch error nahi aata, chat bilkul theek lagta hai — lekin har real coding task fail ho jaata hai. Fix: `num_ctx` ko kam se kam 32,768 tak badhao (Modelfile parameter, environment variable, ya `/set parameter` command se).

## Zaroori Concepts

### Dimaag bas ek address hai
Agent ke liye farq nahi ke model data center mein hai ya GPU pe — sirf quality aur speed badalti hai.

### Do walls
Capability wall — model kaam ke liye kaafi smart nahi. Throughput wall — smart hai lekin strong GPU ke bina slow.

### Tool calls
Local models reliable, correctly-formatted tool calling mein kamzor hote hain — sabse common practical failure.

### num_ctx ka 4,096 default tool calls todta hai
Chhota default context window silent breakage ki wajah banta hai. Hardware allow kare to num_ctx badhana zaroori hota hai.

### Sizing table
`llama3.2:3b` (~8GB) chat ke liye theek, tool calls mein fail. `qwen3:8b` (~16GB) simple tasks ke liye okay. `phi4:14b` (~12GB) reliable tool calls ka floor. `qwen3:30b-a3b` (20-24GB) best balance answers aur speed ka. Throughput ke liye 16-24GB GPU chahiye ek genuinely usable local coding agent ke liye.

### Local kab actually worth hai
Privacy/data residency non-negotiable ho, high volume ho aur cloud bill dominate kare, offline chahiye ho, ya hardware pehle se ho aur model quality kaafi ho. Warna cloud model usually behtar deal hai.

## Exam Mein Ye Kyun Aayega?
Local ek real option hai jo students se poocha jaayega. Exam mein do walls, tool-calling ki fragility, aur local sahi choice kab hoti hai — ye teeno pata hone chahiye.
