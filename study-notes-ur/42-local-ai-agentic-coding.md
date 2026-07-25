# 42. Local AI: Agentic Coding

## Aasan Zabaan Mein Samjho

Agent ka "dimaagh" asal mein bas ek address hai. Tum wahi agent tools ek aise model ke sath bhi connect kar sakte ho jo cloud pe nahi, tumhare apne computer pe chal raha ho. Local AI privacy, offline kaam, aur high volume pe cost ke liye faydemand hai — lekin sirf tab jab model kaafi smart aur kaafi tez ho.

Socho jaise tum ek chef ko ghar pe rakh lo bnisbat restaurant se order karne ke. Ghar wala chef free hai, private hai, lekin agar wo utna skilled nahi to khana theek nahi banega — chahe wo kitni bhi der lagaye. Aur agar skilled hai lekin bohot dheema hai, to wo bhi kaam nahi aayega. Yehi do "walls" hain jo local AI ke sath takrati hain.

## Zaroori Concepts

### The brain is just an address
Agent ke nazariye se koi farq nahi parta ke model data center mein hai ya tumhare GPU pe — interface same rehta hai. Sirf quality aur speed badalti hai.

### The two walls
**Capability wall**: local model itna smart nahi ke planning, tool use, ya long-horizon reasoning kar sake. **Throughput wall**: model smart to hai lekin strong GPU ke bagair bohot dheema hai.

### Tool calls
Local models aksar reliable, sahi-format tool calls banane mein kamzor hote hain — ye sab se aam practical failure hai.

### The `num_ctx` default of 4,096 breaks tool calls
Bahut se local setups chote context window ke sath aate hain by default. Tool-calling workflows ko zyada context chahiye hota hai — chota default aksar chupke se sab kuch tabah kar deta hai. Hardware allow kare to `num_ctx` barhana zaroori hota hai.

### What a tool call actually is, and how it breaks
Ek healthy tool call koi aam likhawat nahi — ye ek chota structured data hota hai, jaise `{"type": "tool_use", "name": "edit_file", "input": {"path": "README.md", "old": "Hello", "new": "Hello, world"}}`. Harness ise padh kar edit karta hai; model khud file ko touch nahi karta. Kamzor model `input` ko plain text bhej deta hai object ki bajaye, harness error deta hai `args expected string, got object`, aur run bina kuch kiye ruk jati hai — ye capability wall hai. `num_ctx` ka masla aur bhi khatarnak hai kyunke chupke se hota hai: Ollama ka default window sirf 4,096 words ka hai, is liye harness ki lambi instruction (tools ke rules aur unki definitions) shuru se hi trim ho jati hai, aur model ko pata hi nahi chalta call kaise format karni hai. Koi error nahi aata — chat theek dikhti hai — lekin har real coding task fail hoti hai. Fix ye hai ke `num_ctx` ko kam se kam 32,768 tak barhao (Modelfile parameter, environment variable, ya `/set parameter` command se).

### Sizing the two walls with real numbers
`llama3.2:3b` (~8GB) chat ke liye theek hai lekin tool calls mein ghalti karta hai — capability wall paar nahi kar paata. `qwen3:8b` (~16GB) simple tasks ke liye theek hai. `phi4:14b` (~12GB) reliable tool calls ke liye taqreeban floor hai — course ~14B ko wo point kehta hai jahan se capability theek hoti hai. `qwen3:30b-a3b` (20-24GB) best balance mana jata hai. Throughput ke liye 16 se 24GB GPU memory hi local setup ko genuinely usable banati hai — tez machine chota model bhi ghalat tool calls degi, aur brilliant model dheemi machine pe bhi painfully slow rahega, kyunke bara model capability theek karta hai, throughput nahi, aur GPU throughput theek karta hai, capability nahi.

### When local is actually worth it
Local jeetta hai jab: privacy ya data residency zaroori ho, high volume ki wajah se cloud token bill bohot barh jaye, offline kaam chahiye ho, ya tumhare paas pehle se hardware ho aur model quality kaafi ho. Warna local ka capability gap aur operational load usually strong cloud model se haar jata hai.

## Exam Mein Ye Kyun Aayega?

Local ek asal option hai jo students se poocha jayega — exam expect karta hai tum do walls, tool-calling ki nazuk nature, aur local kab rational choice hai, ye jaano.
