# AI Ecosystem Course Playlist Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a standalone, self-contained HTML page containing a curated, topic-based YouTube playlist for the AI Ecosystem presentation, and link it from the main deck.

**Architecture:** A single `ai-ecosystem-playlist.html` file using vanilla HTML, CSS, and JS. It features a two-column tabbed layout (Sidebar for topics, right pane for video cards). It will be linked from the final slide of the existing `ai-ecosystem-presentation-v2.html`.

**Tech Stack:** HTML5, CSS3, Vanilla JavaScript.

---

### Task 1: Create Base HTML Structure & Styling

**Files:**
- Create: `ai-ecosystem-playlist.html`

- [ ] **Step 1: Write the base HTML and CSS**

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Ecosystem - Course Playlist</title>
<style>
  :root {
    --bg: #0f0f1a;
    --slide-bg: #1a1a2e;
    --text: #e8e8f0;
    --text-dim: #8888a0;
    --accent-blue: #4fc3f7;
    --accent-purple: #ce93d8;
    --accent-teal: #80cbc4;
    --accent-pink: #f48fb1;
    --border: #2a2a40;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    font-family: 'Segoe UI', system-ui, sans-serif;
    background: var(--bg);
    color: var(--text);
    display: flex;
    height: 100vh;
    overflow: hidden;
  }
  .sidebar {
    width: 30%;
    max-width: 350px;
    background: var(--slide-bg);
    border-right: 1px solid var(--border);
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
  .sidebar h2 { margin-bottom: 20px; color: var(--text); }
  .tab-btn {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--text-dim);
    padding: 15px;
    text-align: left;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    font-weight: 600;
    transition: all 0.2s;
  }
  .tab-btn:hover { background: rgba(255,255,255,0.05); }
  
  .tab-btn.active[data-target="ai-basics"] { border-left: 4px solid var(--accent-blue); color: var(--accent-blue); background: rgba(79,195,247,0.1); }
  .tab-btn.active[data-target="apis"] { border-left: 4px solid var(--accent-purple); color: var(--accent-purple); background: rgba(206,147,216,0.1); }
  .tab-btn.active[data-target="agents"] { border-left: 4px solid var(--accent-teal); color: var(--accent-teal); background: rgba(128,203,196,0.1); }
  .tab-btn.active[data-target="mcp"] { border-left: 4px solid var(--accent-pink); color: var(--accent-pink); background: rgba(244,143,177,0.1); }

  .content-area {
    flex: 1;
    padding: 40px;
    overflow-y: auto;
  }
  .tab-content { display: none; }
  .tab-content.active { display: block; animation: fadeIn 0.3s ease; }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

  .video-card {
    background: var(--slide-bg);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px;
    margin-bottom: 20px;
    display: flex;
    gap: 20px;
  }
  .video-info { flex: 1; }
  .video-title { font-size: 1.2rem; font-weight: bold; margin-bottom: 8px; }
  .video-meta { font-size: 0.9rem; color: var(--text-dim); margin-bottom: 12px; }
  .video-desc { font-size: 0.95rem; line-height: 1.5; margin-bottom: 16px; }
  .watch-btn {
    display: inline-block;
    padding: 8px 16px;
    border-radius: 6px;
    text-decoration: none;
    font-weight: bold;
    font-size: 0.9rem;
    transition: filter 0.2s;
  }
  .watch-btn:hover { filter: brightness(1.2); }
</style>
</head>
<body>
  <div class="sidebar">
    <h2>Course Playlist</h2>
    <button class="tab-btn active" data-target="ai-basics">1. AI & LLM Basics</button>
    <button class="tab-btn" data-target="apis">2. APIs & Providers</button>
    <button class="tab-btn" data-target="agents">3. AI Agents & Tools</button>
    <button class="tab-btn" data-target="mcp">4. MCP & Advanced</button>
    <a href="ai-ecosystem-presentation-v2.html" style="margin-top:auto; color:var(--text-dim); text-decoration:none; font-size:0.9rem;">← Back to Presentation</a>
  </div>
  <div class="content-area">
    <div id="ai-basics" class="tab-content active"></div>
    <div id="apis" class="tab-content"></div>
    <div id="agents" class="tab-content"></div>
    <div id="mcp" class="tab-content"></div>
  </div>
  <script>
    document.querySelectorAll('.tab-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
        document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
        btn.classList.add('active');
        document.getElementById(btn.dataset.target).classList.add('active');
      });
    });
  </script>
</body>
</html>
```

- [ ] **Step 2: Verify file creation**

Run: `cat ai-ecosystem-playlist.html | grep "Course Playlist"`
Expected: Output showing the `<title>` and `<h2>` tags.

- [ ] **Step 3: Commit**

```bash
git add ai-ecosystem-playlist.html
git commit -m "feat: create base structure for course playlist"
```

### Task 2: Populate AI & LLM Basics Videos

**Files:**
- Modify: `ai-ecosystem-playlist.html`

- [ ] **Step 1: Add high-quality video content to the `ai-basics` div**

```html
<!-- Inside <div id="ai-basics" class="tab-content active"> -->
<h2 style="color: var(--accent-blue); margin-bottom: 20px;">AI & LLM Basics</h2>

<div class="video-card" style="border-left: 4px solid var(--accent-blue);">
  <div class="video-info">
    <div class="video-title">But what is a neural network? | Chapter 1, Deep learning</div>
    <div class="video-meta">3Blue1Brown • 19:13</div>
    <div class="video-desc">The absolute best visual explanation of how neural networks (the foundation of AI) actually work under the hood. Essential viewing for building an intuition about AI.</div>
    <a href="https://www.youtube.com/watch?v=aircAruvnKk" target="_blank" class="watch-btn" style="background: var(--accent-blue); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-blue);">
  <div class="video-info">
    <div class="video-title">Let's build GPT: from scratch, in code, spelled out.</div>
    <div class="video-meta">Andrej Karpathy • 1:56:13</div>
    <div class="video-desc">A deep dive into how Large Language Models are built. Andrej Karpathy (former Director of AI at Tesla, founding member of OpenAI) builds a GPT from scratch. Highly recommended for developers.</div>
    <a href="https://www.youtube.com/watch?v=kCc8FmEb1nY" target="_blank" class="watch-btn" style="background: var(--accent-blue); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-blue);">
  <div class="video-info">
    <div class="video-title">What are Large Language Models (LLMs)?</div>
    <div class="video-meta">IBM Technology • 16:54</div>
    <div class="video-desc">A fantastic, accessible whiteboard explanation of LLM concepts, tokens, parameters, and how they generate text. Perfect for a high-level overview.</div>
    <a href="https://www.youtube.com/watch?v=5sLYAQS9sWQ" target="_blank" class="watch-btn" style="background: var(--accent-blue); color: #000;">Watch on YouTube</a>
  </div>
</div>
```

- [ ] **Step 2: Verify changes**

Run: `grep "But what is a neural network" ai-ecosystem-playlist.html`
Expected: Output showing the video title.

- [ ] **Step 3: Commit**

```bash
git add ai-ecosystem-playlist.html
git commit -m "feat: add AI & LLM Basics videos"
```

### Task 3: Populate APIs & Providers Videos

**Files:**
- Modify: `ai-ecosystem-playlist.html`

- [ ] **Step 1: Add high-quality video content to the `apis` div**

```html
<!-- Inside <div id="apis" class="tab-content"> -->
<h2 style="color: var(--accent-purple); margin-bottom: 20px;">APIs & Providers</h2>

<div class="video-card" style="border-left: 4px solid var(--accent-purple);">
  <div class="video-info">
    <div class="video-title">OpenAI API Tutorial for Beginners</div>
    <div class="video-meta">Dave Ebbelaar • 35:20</div>
    <div class="video-desc">A comprehensive guide on how to integrate the OpenAI API into your applications, covering text generation, roles, and basic configuration.</div>
    <a href="https://www.youtube.com/watch?v=c-g6egKCCqc" target="_blank" class="watch-btn" style="background: var(--accent-purple); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-purple);">
  <div class="video-info">
    <div class="video-title">Anthropic Claude 3 API Crash Course</div>
    <div class="video-meta">Patrick Loeber • 24:15</div>
    <div class="video-desc">Learn how to use Anthropic's Claude 3 API, known for its large context window and strong reasoning capabilities.</div>
    <a href="https://www.youtube.com/watch?v=3g8OQO1rXgQ" target="_blank" class="watch-btn" style="background: var(--accent-purple); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-purple);">
  <div class="video-info">
    <div class="video-title">Google Vertex AI in 5 Minutes</div>
    <div class="video-meta">Google Cloud • 5:12</div>
    <div class="video-desc">A quick overview of Google Cloud's Vertex AI platform, the Model Garden, and how to deploy enterprise-grade AI models.</div>
    <a href="https://www.youtube.com/watch?v=M2_o3H2-O9g" target="_blank" class="watch-btn" style="background: var(--accent-purple); color: #000;">Watch on YouTube</a>
  </div>
</div>
```

- [ ] **Step 2: Verify changes**

Run: `grep "OpenAI API Tutorial for Beginners" ai-ecosystem-playlist.html`
Expected: Output showing the video title.

- [ ] **Step 3: Commit**

```bash
git add ai-ecosystem-playlist.html
git commit -m "feat: add APIs & Providers videos"
```

### Task 4: Populate AI Agents & Tools Videos

**Files:**
- Modify: `ai-ecosystem-playlist.html`

- [ ] **Step 1: Add high-quality video content to the `agents` div**

```html
<!-- Inside <div id="agents" class="tab-content"> -->
<h2 style="color: var(--accent-teal); margin-bottom: 20px;">AI Agents & Tools</h2>

<div class="video-card" style="border-left: 4px solid var(--accent-teal);">
  <div class="video-info">
    <div class="video-title">AI Agents, explained</div>
    <div class="video-meta">IBM Technology • 12:45</div>
    <div class="video-desc">A solid, easy-to-understand whiteboard explanation of what an AI agent is, how it uses tools, and the concept of reasoning and planning.</div>
    <a href="https://www.youtube.com/watch?v=F8NKVhkZZWI" target="_blank" class="watch-btn" style="background: var(--accent-teal); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-teal);">
  <div class="video-info">
    <div class="video-title">Agentic Design Patterns Part 1</div>
    <div class="video-meta">Andrew Ng / DeepLearning.AI • 20:00</div>
    <div class="video-desc">Andrew Ng explains the core workflows that make AI agents effective: Reflection, Tool Use, Planning, and Multi-agent collaboration.</div>
    <a href="https://www.youtube.com/watch?v=sal78qLsZrc" target="_blank" class="watch-btn" style="background: var(--accent-teal); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-teal);">
  <div class="video-info">
    <div class="video-title">Cline (formerly Roo Code) VS Code Extension Demo</div>
    <div class="video-meta">Fireship • 10:15</div>
    <div class="video-desc">A fast-paced, highly entertaining look at how to use an AI coding agent directly inside VS Code to automate full stack development tasks.</div>
    <a href="https://www.youtube.com/watch?v=v=k8v3vN6MhJ8" target="_blank" class="watch-btn" style="background: var(--accent-teal); color: #000;">Watch on YouTube</a>
  </div>
</div>
```

- [ ] **Step 2: Verify changes**

Run: `grep "Agentic Design Patterns" ai-ecosystem-playlist.html`
Expected: Output showing the video title.

- [ ] **Step 3: Commit**

```bash
git add ai-ecosystem-playlist.html
git commit -m "feat: add AI Agents & Tools videos"
```

### Task 5: Populate MCP & Advanced Videos

**Files:**
- Modify: `ai-ecosystem-playlist.html`

- [ ] **Step 1: Add high-quality video content to the `mcp` div**

```html
<!-- Inside <div id="mcp" class="tab-content"> -->
<h2 style="color: var(--accent-pink); margin-bottom: 20px;">MCP & Advanced</h2>

<div class="video-card" style="border-left: 4px solid var(--accent-pink);">
  <div class="video-info">
    <div class="video-title">Model Context Protocol (MCP) Explained</div>
    <div class="video-meta">Anthropic • 4:32</div>
    <div class="video-desc">The official introduction to the open standard that enables AI models to securely connect to external tools and data sources.</div>
    <a href="https://www.youtube.com/watch?v=0hBte5OqP1A" target="_blank" class="watch-btn" style="background: var(--accent-pink); color: #000;">Watch on YouTube</a>
  </div>
</div>

<div class="video-card" style="border-left: 4px solid var(--accent-pink);">
  <div class="video-info">
    <div class="video-title">Building an MCP Server from Scratch</div>
    <div class="video-meta">CopilotKit • 28:10</div>
    <div class="video-desc">A hands-on tutorial demonstrating how to build a custom Model Context Protocol server to expose your own database and tools to AI agents.</div>
    <a href="https://www.youtube.com/watch?v=FjP8JjSgU64" target="_blank" class="watch-btn" style="background: var(--accent-pink); color: #000;">Watch on YouTube</a>
  </div>
</div>
```

- [ ] **Step 2: Verify changes**

Run: `grep "Model Context Protocol (MCP) Explained" ai-ecosystem-playlist.html`
Expected: Output showing the video title.

- [ ] **Step 3: Commit**

```bash
git add ai-ecosystem-playlist.html
git commit -m "feat: add MCP & Advanced videos"
```

### Task 6: Link Playlist from Main Presentation

**Files:**
- Modify: `ai-ecosystem-presentation-v2.html`

- [ ] **Step 1: Read the presentation file to locate Slide 25**

Run: `grep -n 'data-slide="25"' ai-ecosystem-presentation-v2.html`

- [ ] **Step 2: Add the "View Course Playlist" button**

In `ai-ecosystem-presentation-v2.html`, find the topics div in Slide 25 and add the playlist button below it.

```html
<!-- Existing code in Slide 25 -->
    <div class="topics animate-in delay-3" style="margin-bottom: 30px;">
      <!-- span tags ... -->
    </div>
    
    <!-- ADD THIS BLOCK -->
    <div class="animate-in delay-4" style="margin-bottom: 30px;">
      <a href="ai-ecosystem-playlist.html" target="_blank" style="display:inline-block; padding:12px 24px; background:linear-gradient(135deg, var(--accent-blue), var(--accent-purple)); color:#000; text-decoration:none; font-weight:bold; border-radius:8px; font-size:1.1rem; transition:transform 0.2s;">
        ▶ View Course Playlist
      </a>
    </div>
    
    <!-- Existing code -->
    <p class="animate-in delay-4" style="font-size: 1.2rem; color: var(--text-dim); margin-top: 10px;">
      <span style="color: var(--accent-blue);">✉</span> rupan@mgtechsoft.com
    </p>
```

*(Note: Change `delay-4` on the email paragraph to `delay-5` if you prefer staggered animation)*

- [ ] **Step 3: Verify changes**

Run: `grep "ai-ecosystem-playlist.html" ai-ecosystem-presentation-v2.html`
Expected: Output showing the anchor tag.

- [ ] **Step 4: Commit**

```bash
git add ai-ecosystem-presentation-v2.html
git commit -m "feat: link to course playlist from final slide"
```
