# AI Development Tools — Comparison Guide

> **Audience:** Mixed experience developers
> **Goal:** Understand the capabilities, use cases, and differences between AI coding tools

---

## 1. The Landscape

AI development tools fall into three categories:

| Category | What It Is | Examples |
|----------|-----------|----------|
| **IDE Extensions** | Plugins that live inside your code editor | Roo Code, Cline |
| **CLI Tools** | Terminal-based AI assistants | Claude Code, OpenCode, Gemini CLI, OpenClaw |
| **Frameworks** | Libraries to build your own agents | Open Manus, LangChain, AutoGen |

---

## 2. IDE Extensions

### Roo Code

**What it is:** VS Code extension that acts as an AI pair programmer with autonomous capabilities.

**Capabilities:**
- Reads your entire codebase for context
- Generates and edits code directly in files
- Runs terminal commands
- Debugs errors by reading stack traces
- Supports multiple API providers (OpenRouter, OpenAI, Anthropic, etc.)
- Can work in autonomous mode (plan → execute → verify loop)

**Best for:**
- Day-to-day coding assistance
- Refactoring existing code
- Writing tests
- Understanding unfamiliar codebases

**Setup:**
1. Install from VS Code Marketplace
2. Add your API key (OpenRouter recommended for free tier)
3. Select a model
4. Start chatting or give tasks

**Pricing:** Free extension — you pay for API usage only

---

### Cline

**What it is:** Autonomous AI coding agent for VS Code with browser automation and MCP support.

**Capabilities:**
- Everything Roo Code does, plus:
- **Browser automation** — can open websites, click, fill forms, scrape
- **MCP support** — connects to external tools via Model Context Protocol
- **File creation** — can create entire project structures
- **Web search** — can look up documentation in real-time
- **Self-correction** — reads errors and fixes them automatically

**Best for:**
- Building projects from scratch
- Web scraping tasks
- Tasks that need browser interaction
- When you want the agent to work independently

**Setup:**
1. Install from VS Code Marketplace
2. Configure API provider
3. Enable browser and MCP features in settings
4. Give it a task and watch it work

**Pricing:** Free extension — you pay for API usage only

---

### Roo Code vs Cline — Quick Comparison

| Feature | Roo Code | Cline |
|---------|----------|-------|
| Code editing | ✅ | ✅ |
| Terminal commands | ✅ | ✅ |
| Multi-file operations | ✅ | ✅ |
| Browser automation | ❌ | ✅ |
| MCP support | Limited | ✅ Full |
| Web search | ❌ | ✅ |
| Autonomous mode | ✅ | ✅ |
| Best for | Coding tasks | Full-stack automation |

---

## 3. CLI Tools

### Claude Code (Anthropic)

**What it is:** Anthropic's official CLI tool for Claude models, designed specifically for codebase interaction.

**Capabilities:**
- Deep codebase understanding — reads and analyzes entire projects
- Multi-file edits across your codebase
- Runs tests and fixes failures
- Git operations (commit, branch, diff analysis)
- Natural language task execution
- Built on Claude's strong reasoning abilities

**Best for:**
- Large codebase refactoring
- Complex multi-file changes
- Code review and analysis
- When you need strong reasoning over raw speed

**Setup:**
```bash
npm install -g @anthropic-ai/claude-code
claude  # Start interactive session
```

**Pricing:** Uses Claude API (paid), but very capable

---

### OpenCode

**What it is:** Open-source CLI AI coding assistant.

**Capabilities:**
- Terminal-based AI interaction
- Code generation and editing
- File operations
- Supports multiple API providers
- Open source — customizable and self-hostable

**Best for:**
- Developers who prefer terminal workflows
- Server/remote development
- When you want open-source tooling
- Quick code snippets and explanations

**Setup:**
```bash
# Check installation instructions in the repo
# Typically: npm install or pip install
```

**Pricing:** Free (open source) — you pay for API usage

---

### Gemini CLI (Google)

**What it is:** Google's CLI tool for interacting with Gemini models from the terminal.

**Capabilities:**
- Access to Gemini models (2.5 Pro, Flash, etc.)
- Code generation and explanation
- Integration with Google Cloud services
- Multimodal capabilities (can process images)
- Generous free tier through Google

**Best for:**
- Developers already in the Google ecosystem
- When you need multimodal AI (text + images)
- Quick prototyping with Gemini models
- GCP integration tasks

**Setup:**
```bash
# Install via Google's package manager or npm
# Configure with Google API key
```

**Pricing:** Generous free tier available

---

### OpenClaw

**What it is:** Open-source CLI AI tool for development workflows.

**Capabilities:**
- Terminal-based AI assistance
- Code generation and editing
- File system operations
- Open source and extensible

**Best for:**
- Developers wanting a lightweight CLI AI tool
- Custom workflows and scripting
- Open-source preference

**Pricing:** Free (open source) — you pay for API usage

---

## 4. Frameworks

### Open Manus

**What it is:** Open-source framework for building custom AI agents in Python.

**Capabilities:**
- Build agents with specific skills/tools
- Define workflows and task pipelines
- Integrate with any API provider
- Custom tool creation
- Multi-agent coordination

**Best for:**
- Building your own AI agents
- Custom automation workflows
- When off-the-shelf tools don't fit your needs
- Learning how agents work under the hood

**Setup:**
```bash
git clone https://github.com/mannaandpoem/OpenManus
cd OpenManus
pip install -r requirements.txt
# Configure API keys and run
```

**Pricing:** Free (open source) — you pay for API usage

---

## 5. Tool Selection Guide

### "I want to..." → Use this:

| Goal | Recommended Tool | Why |
|------|-----------------|-----|
| Code faster in VS Code | **Roo Code** | Deep editor integration, multi-provider |
| Build a project from scratch | **Cline** | Autonomous, browser, MCP |
| Refactor a large codebase | **Claude Code** | Strong reasoning, multi-file |
| Work on a remote server | **OpenCode** or **Claude Code** | CLI-based, no GUI needed |
| Use Google's models | **Gemini CLI** | Direct Gemini access |
| Build custom agents | **Open Manus** | Python framework, flexible |
| Stay open-source | **OpenCode** + **OpenClaw** | Fully open source stack |
| Experiment for free | **Roo Code** + **OpenRouter free models** | Zero cost to start |

---

## 6. Recommended Setup for Juniors

### Starter Setup (Free)
```
VS Code
  ├── Roo Code (extension)
  │     └── API: OpenRouter (free models)
  └── Cline (extension)
        └── API: OpenRouter (free models)

Terminal
  └── OpenCode or Gemini CLI (free tier)
```

**Total cost: $0** — all tools and APIs have free tiers.

### Intermediate Setup (~$10-20/month)
```
VS Code
  ├── Cline (extension)
  │     └── API: OpenRouter (paid models: Claude Sonnet, GPT-4)
  └── Roo Code (extension)
        └── API: OpenRouter

Terminal
  └── Claude Code (paid API)

GCP VM (e2-medium)
  └── Running Open Manus agent 24/7
```

### Pro Setup (~$50-100/month)
```
VS Code
  ├── Cline + Roo Code
  │     └── Multiple API providers for different tasks
  └── MCP servers for database, browser, git

Terminal
  ├── Claude Code
  └── Gemini CLI

GCP VM (n1-standard-4)
  └── Custom agent pipeline with Open Manus
```

---

## 7. API Provider Setup for These Tools

### OpenRouter (Recommended for all tools)
1. Sign up at [openrouter.ai](https://openrouter.ai)
2. Create an API key
3. Use the same key in Roo Code, Cline, OpenCode, etc.
4. Start with free models, upgrade when needed

### Why One Provider for Everything?
- Single billing dashboard
- Consistent API format
- Easy to switch models without changing tool config
- Free models available for experimentation

---

## 8. Common Workflows

### Workflow 1: Quick Code Fix
```
You: "Fix the bug in auth.py — users can't login"
  ↓
Roo Code: Reads auth.py, finds the issue, proposes fix
  ↓
You: Review and accept
  ↓
Done in 2 minutes instead of 20
```

### Workflow 2: Build a Feature
```
You: "Create a user profile page with avatar upload"
  ↓
Cline: Plans the steps
  ↓
Cline: Creates routes, models, views, templates
  ↓
Cline: Runs tests, fixes errors
  ↓
Cline: Opens browser to verify it works
  ↓
You: Review the complete feature
```

### Workflow 3: Refactor
```
You: "Refactor this monolithic file into modules"
  ↓
Claude Code: Analyzes the file structure
  ↓
Claude Code: Creates module plan
  ↓
Claude Code: Splits code, updates imports
  ↓
Claude Code: Runs tests to verify nothing broke
  ↓
You: Review the clean architecture
```

---

## 9. Tips for Juniors

1. **Start with free models** — Don't pay until you've exhausted free tiers
2. **Be specific with prompts** — "Fix the login bug" is better than "fix bugs"
3. **Review every change** — AI makes mistakes. Always read what it writes.
4. **Use the right tool** — CLI for server work, IDE extensions for coding
5. **Learn the basics first** — Don't let AI write code you don't understand
6. **Set up OpenRouter first** — One key works with all tools
7. **Experiment on throwaway projects** — Don't practice on production code

---

## 10. Quick Reference Card

| Tool | Type | Platform | Cost | Best For |
|------|------|----------|------|----------|
| **Roo Code** | IDE Extension | VS Code | Free + API | Daily coding |
| **Cline** | IDE Extension | VS Code | Free + API | Autonomous tasks |
| **Claude Code** | CLI | Terminal | Paid API | Large refactors |
| **OpenCode** | CLI | Terminal | Free + API | Server/remote work |
| **Gemini CLI** | CLI | Terminal | Free tier | Google ecosystem |
| **OpenClaw** | CLI | Terminal | Free + API | Lightweight CLI |
| **Open Manus** | Framework | Python | Free + API | Custom agents |
