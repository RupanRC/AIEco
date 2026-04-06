# The AI Ecosystem — Teaching Guide

> **Accompanying diagram:** `ai-ecosystem-diagram.excalidraw`
> **Audience:** Mixed experience (some coding, varying AI exposure)
> **Format:** Open the `.excalidraw` file at [excalidraw.com](https://excalidraw.com) and walk through each layer while using this guide.

---

## 1. AI (Artificial Intelligence) — The Umbrella

**What to say:**

> "AI is the broadest term here. It means any system that mimics or simulates human intelligence — recognizing images, playing chess, recommending videos, or understanding language. Everything we'll talk about today sits *inside* AI."

**Analogy:**
Think of AI like "Vehicles." It's the category. Cars, trucks, motorcycles — they're all vehicles, but they work differently. LLMs are one type of AI vehicle.

**Key point:**
Not all AI is LLMs. Spam filters, recommendation engines, and self-driving cars are AI too — but they don't use language models.

---

## 2. LLM (Large Language Model) — The Engine

**What to say:**

> "An LLM is a specific type of AI — one trained to predict the next word in a sequence. That's it. It reads your text, and predicts what should come next. The magic is that when you train it on enough data, it starts to *seem* like it understands."

**Key Concepts to explain:**

### Tokens
- **Definition:** The smallest unit of text an LLM processes. Not exactly words — a token can be a word, part of a word, or even punctuation.
- **Rule of thumb:** 1000 tokens ≈ 750 words (English)
- **Why it matters:** You're charged per token (input + output). More tokens = more cost.

### Context Window
- **Definition:** The maximum amount of text the LLM can "hold in memory" at once — your prompt + its response combined.
- **Analogy:** Like your working memory. If someone reads you a 200-page book and asks a question, you'll forget the beginning. The context window is how much the model can "remember" in one go.
- **Examples:**
  - GPT-4: ~8K–128K tokens (varies by version)
  - Claude: ~200K tokens
  - Free models on OpenRouter: ~4K–8K tokens

### Temperature
- **Definition:** Controls randomness. Low (0.1) = predictable, focused. High (0.9) = creative, varied.
- **Analogy:** Like a dial between "give me the textbook answer" and "give me something creative."

### Common Models (as of 2026)
| Model | Maker | Strengths |
|-------|-------|-----------|
| GPT-4 / GPT-5 | OpenAI | General purpose, strong reasoning |
| Claude 4 / Sonnet | Anthropic | Long context, code, safety |
| Gemini 2.5 | Google | Multimodal, free tier generous |
| Llama 3 / 4 | Meta | Open source, self-hostable |

---

## 3. API (Application Programming Interface) — The Connection

**What to say:**

> "An API is just a way for programs to talk to each other. Instead of you typing into a chat window, your *code* sends a message to the LLM and gets a response back. That's it — it's a web request, like loading a webpage, but between programs."

**Simple example:**
```
Your code → POST https://api.openai.com/v1/chat/completions
Body: {"model": "gpt-4", "messages": [{"role": "user", "content": "Hello!"}]}
Response: {"choices": [{"message": {"content": "Hi there!"}}]}
```

**Why APIs matter:**
- You can build AI into your own apps
- AI agents use APIs to interact with LLMs
- You pay per API call (usually per token)

---

## 4. API Providers — The Hosts

**What to say:**

> "These are the companies that actually run the LLMs and let you access them via API. You don't run the model yourself — they host it on their servers, and you send requests to them."

### Key Providers

| Provider | What They Offer | Free Tier |
|----------|----------------|-----------|
| **OpenRouter** | Aggregator — one API, many models (GPT, Claude, open-source) | Yes — several free models |
| **Kilo Code** | Developer-focused AI API | Free tier available |
| **OpenAI** | GPT models | Credits for new accounts (limited) |
| **Anthropic** | Claude models | Small free credits |
| **Google** | Gemini models | Generous free tier |

### OpenRouter (Recommended for learning)
- **Why:** One API key gives you access to dozens of models. You can switch between GPT, Claude, Llama, etc. without changing code.
- **Free models:** Yes — they offer several open-source models at zero cost. Great for experimenting.
- **Pricing:** Pay per token, usually cheaper than going direct to OpenAI/Anthropic.

### Kilo Code
- Developer-focused, often bundled with coding tools
- Good free tier for experimentation

---

## 5. AI Agents — The Workers

**What to say:**

> "An agent is AI that doesn't just answer questions — it *does things*. It can plan a task, use tools (like running code, editing files, searching the web), and iterate until the job is done. Think of it as the difference between asking someone for directions (chatbot) and asking someone to go deliver a package (agent)."

### Tools Your Juniors Should Know

| Tool | Type | Platform | Key Capability |
|------|------|----------|----------------|
| **Roo Code** | VS Code Extension | IDE | Code generation, file editing, terminal commands |
| **Cline** | VS Code Extension | IDE | Autonomous coding, browser use, MCP support |
| **Claude Code** | CLI | Terminal | Deep codebase understanding, multi-file edits |
| **OpenCode** | CLI | Terminal | Open-source AI coding assistant |
| **Open Manus** | Framework | Python | Build custom AI agents for workflows |
| **Antigravity** | IDE/Tool | Desktop | AI-assisted development environment |
| **Gemini CLI** | CLI | Terminal | Google's CLI for Gemini models |
| **OpenClaw** | CLI | Terminal | Open-source CLI AI tool |

### The Agent Workflow
```
You give a task → Agent plans steps → Agent uses tools (API, files, terminal)
→ Agent checks its work → Agent iterates → Agent delivers result
```

### VS Code Extensions (Roo Code, Cline)
- Best for: Day-to-day coding assistance
- They live in your editor, see your code, and can make edits directly
- Connect to any API provider (OpenRouter, OpenAI, etc.)

### CLI Tools (Claude Code, OpenCode, Gemini CLI)
- Best for: Terminal workflows, scripting, server environments
- No GUI needed — pure text interaction
- Often more powerful for large codebase operations

---

## 6. MCP (Model Context Protocol) — The Connector

**What to say:**

> "MCP is a standard protocol that lets AI agents connect to external tools and data sources — like your file system, databases, or web browsers. Before MCP, every tool needed custom integration. MCP is like USB-C: one standard port, plug in anything."

**Analogy:**
- **Before MCP:** Every phone had its own charger. Every tool needed custom code to work with an AI agent.
- **After MCP:** USB-C. One protocol. Plug in a database, a file system, a browser — the agent knows how to talk to all of them.

**What MCP connects agents to:**
- File systems (read/write files)
- Databases (query data)
- Web browsers (scrape, automate)
- Git repositories (commit, branch, review)
- APIs (fetch live data)

**Why it matters for your juniors:**
If they build or use AI agents, MCP means they don't need to write custom integrations for every tool. They configure an MCP server, and the agent can use it.

---

## 7. Putting It All Together — The Full Picture

Walk through the flow on the diagram:

```
YOU (the developer)
  ↓
AI AGENT (Roo Code, Cline, Claude Code)
  ↓ uses MCP to access tools
  ↓
API CALL (to OpenRouter, OpenAI, etc.)
  ↓
LLM (GPT-4, Claude, Gemini, Llama)
  ↓ processes your request
  ↓
RESPONSE flows back up the chain
```

**The one-liner:**
> "You use an Agent → which calls an API → which hits an LLM → which is a type of AI. MCP is how the Agent talks to your tools. Providers are who hosts the LLM."

---

## 8. Quick Reference Card

| Term | One-Line Definition | Analogy |
|------|-------------------|---------|
| **AI** | Machines that simulate intelligence | "Vehicles" (the category) |
| **LLM** | Text prediction engine trained on massive data | "Engine" (one type of vehicle) |
| **Token** | Unit of text the LLM processes | "Words" (roughly) |
| **Context Window** | How much text the LLM can process at once | "Working memory" |
| **API** | Program-to-program communication | "Phone call" |
| **Provider** | Company that hosts the LLM | "Phone company" |
| **Agent** | AI that can act autonomously with tools | "Employee" |
| **MCP** | Standard protocol for agent-tool connections | "USB-C" |

---

## Suggested Teaching Flow

1. **Open the Excalidraw diagram** — show the full picture first (2 min)
2. **Go top to bottom** — AI → LLM → API → Providers/Agents → MCP (15 min)
3. **Use the analogies** — they stick better than technical definitions
4. **Show a live example** — hit OpenRouter's free API, get a response (5 min)
5. **Demo an agent** — Roo Code or Cline doing a simple coding task (10 min)
6. **Q&A** — let them ask about anything that was unclear
