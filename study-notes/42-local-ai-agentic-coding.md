# 42. Local AI: Agentic Coding

## Simple Explanation (like you're 5)

The “brain” of an agent is just an address.

You can point the same agent tools at a model that runs on your own computer instead of a cloud service. Local AI is useful for privacy, offline work, and cost at high volume — but only when the model is smart enough and fast enough for the job.

## Key Concepts Unpacked

### The brain is just an address
From the agent’s point of view it does not matter whether the model lives in a data center or on your GPU. The interface is the same. Only the quality and speed change.

### The two walls
- **Capability wall**: the local model is simply not smart enough for the task (planning, tool use, long-horizon reasoning).
- **Throughput wall**: the model is smart enough but too slow unless you have a strong GPU.

### Tool calls
Local models are often weaker at reliable, correctly-formatted tool calling. This is one of the most common practical failure modes.

### The `num_ctx` default of 4,096 breaks tool calls
Many local setups ship with a small default context window. Tool-calling workflows need more context. The small default is a frequent source of silent breakage. Raising `num_ctx` (when the hardware allows) is often required.

### What a tool call actually is, and how it breaks
A healthy tool call is not ordinary writing — it's a small piece of structured data, like `{"type": "tool_use", "name": "edit_file", "input": {"path": "README.md", "old": "Hello", "new": "Hello, world"}}`. The harness reads that and does the edit; the model never touches the file directly, it just sends a precise instruction. A too-weak model sends the `input` as a blob of plain text instead of a real object, the harness rejects it with an error like `args expected string, got object`, and the run stops with nothing edited — that's the capability wall, up close. The `num_ctx` trap is nastier because it fails silently: Ollama's default window is only 4,096 words, so the harness's long instruction (the rules of the tool plus every tool's definition) gets quietly trimmed from the start, and the model never sees the part explaining how to format a call. Nothing errors — chat still looks fine — but every real coding task fails. The fix is raising `num_ctx` to at least 32,768 (a Modelfile parameter, an environment variable, or a `/set parameter` command mid-session).

### Sizing the two walls with real numbers
The source gives a rough model-to-task table worth knowing: `llama3.2:3b` (about 8GB memory) is good for chat but mangles tool calls — it hasn't cleared the capability wall. `qwen3:8b` (about 16GB) is okay for simple tasks. `phi4:14b` (about 12GB) is roughly the floor for reliable tool calls — the course names ~14B as where capability starts to hold. `qwen3:30b-a3b` (20-24GB) is called the best balance of strong answers and speed. On the throughput side, a GPU with roughly 16 to 24GB of memory is what turns a local setup into a genuinely usable coding agent — a fast machine running a tiny model still writes broken tool calls, and a brilliant model on a slow machine is still painfully slow, because a bigger model fixes capability but does nothing for throughput, and a GPU fixes throughput but does nothing for capability.

### When local is actually worth it
Local wins when:
- Privacy or data residency is non-negotiable.
- You have high volume and the cloud token bill would dominate.
- You need offline operation.
- You already have the hardware and the model quality is sufficient for the specific task.

Otherwise the capability gap and operational overhead of local usually lose to a strong cloud model.

## Why would this be on the exam?
Local is a real option students will be asked about. The exam expects you to know the two walls, the tool-calling fragility, and the conditions under which local is the rational choice.
