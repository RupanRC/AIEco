# AI Ecosystem Course Playlist - Design Specification

## 1. Overview
A standalone, self-contained HTML page serving as a curated video playlist for the AI Ecosystem presentation. Creating a separate file (`ai-ecosystem-playlist.html`) prevents blowing out the main presentation's context and file size, while providing a dedicated, focused course experience.

## 2. Architecture & Integration
*   **File Structure:** A new file `ai-ecosystem-playlist.html` will be created in the project root.
*   **Integration:** A "View Course Playlist" button/link will be added to the final slide (Slide 25) of `ai-ecosystem-presentation-v2.html`, opening the new page in a new tab.
*   **Visual Style:** Dark theme (`#0f0f1a` background) matching the main presentation. Self-contained, with no external CSS/JS dependencies.

## 3. Layout & UX (Tabbed View)
*   **Two-Column Design:** 
    *   **Left Sidebar (30%):** Vertical navigation menu listing the curriculum topics. Clicking a topic switches the active view in the right pane. Active states use accent colors.
    *   **Right Content Area (70%):** A scrollable list of video cards for the selected topic.
*   **Video Cards:** Each card displays:
    *   Title and creator/channel.
    *   Duration.
    *   Brief description explaining why it's relevant to the presentation.
    *   A "Watch on YouTube" button (opens the video directly in a new tab).

## 4. Curriculum Categories & Colors
1.  **AI & LLM Basics** (Accent: Blue `#4fc3f7`)
2.  **APIs & Providers** (Accent: Purple `#ce93d8`)
3.  **AI Agents & Tools** (Accent: Teal `#80cbc4`)
4.  **MCP & Advanced Topics** (Accent: Pink `#f48fb1`)

## 5. Content Sourcing Requirement
During implementation, the agent must proactively source **real, high-quality YouTube videos** for each topic category from respected channels (e.g., 3Blue1Brown, Andrej Karpathy, Fireship, Anthropic/OpenAI official channels, IBM Technology, CopilotKit, AICodeKing). Placeholder links are not acceptable for the final deliverable.