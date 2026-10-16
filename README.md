# Agent Skills

A collection of specialized, production-ready AI agent skills and product engineering workflows.

## Skills Overview

### `founder-prd-builder`
- **Location:** [`src/founder-prd-builder/SKILL.md`](src/founder-prd-builder/SKILL.md)
- **Role:** Acts as an expert, patient Product Manager who guides founders (both non-technical and technical) through a structured, gate-driven interview to transform high-level vision into clear, engineering-grade Product Requirements Documents (PRDs).
- **Key Capabilities:**
  - Automated pre-interview workspace reconnaissance (infers existing architecture, tech stack, and dependencies before asking questions)
  - Frictionless, low-cognitive-load discovery using lettered multiple-choice options (`1A, 2C, 3B`) with freeform write-ins
  - Strict anti-vagueness gates and pushback on ambiguous requirements
  - Outcome-driven discovery inspired by Marty Cagan and Teresa Torres
  - Explicit transition from Strategy Gates (vision, audience, journey) to Engineering Gates (data boundaries, failure modes, error handling)
  - Token-efficient, AI-agent and developer-ready PRD output with numbered requirements (`FR-xxx`, `NFR-xxx`), user stories (`US-xxx`), verifiable acceptance criteria (`[ ]`), and MoSCoW prioritization

---

## Non-Technical Setup & Installation Guide

You do **not** need to be a software engineer or use the command line to use this skill. Choose the method that best fits your workflow:

### 📦 Quick Download: Pre-Packaged Releases (Zero-Code)

Every release of this repository automatically builds and attaches ready-to-use packages on the [**GitHub Releases**](../../releases) page:

- **`founder-prd-builder-web-bundle.md`** *(For ChatGPT & Claude Web Users)*:  
  A single, standalone text file formatted specifically for copying and pasting into ChatGPT Custom GPTs, Claude Projects, or Gemini System Prompts.
- **`founder-prd-builder-plugin.zip`** *(For Code Editors & CLI Users)*:  
  A pre-packaged archive containing the plugin manifest and skill files, ready to extract directly into your project or IDE configuration folder.

---

### Method 1: Web AI Chats (ChatGPT, Claude.ai, Gemini) — *Easiest / No Setup*

If you use a browser-based AI assistant, you can turn it into your personal Product Manager in under 60 seconds using the pre-packaged bundle:


#### In Claude.ai (Recommended: Claude Projects)
1. Open [Claude.ai](https://claude.ai) and click **Projects** in the sidebar (available on Pro/Team plans) or open a new chat.
2. If using a **Project**: Click **Project Knowledge** or **Set Custom Instructions**.
3. Open [`src/founder-prd-builder/SKILL.md`](src/founder-prd-builder/SKILL.md) and copy the entire text.
4. Paste it into the **Custom Instructions** field.
5. In your chat, type:  
   > *"I have an idea for a new product/feature. Please act as my founder PRD builder and walk me through the interview."*

#### In ChatGPT (Custom GPT or Custom Instructions)
1. Open [ChatGPT](https://chatgpt.com).
2. **Option A (Custom GPT):** Go to **Explore GPTs** → **Create**. In the **Configure** tab, paste the text of [`src/founder-prd-builder/SKILL.md`](src/founder-prd-builder/SKILL.md) into the **Instructions** box.
3. **Option B (Direct Chat):** Simply start a new chat, paste the entire [`SKILL.md`](src/founder-prd-builder/SKILL.md) file, and append:  
   > *"Please follow these instructions and help me build a PRD for: [Your App Idea]"*

---

### Method 2: AI Code Editors (Cursor, Windsurf, VS Code)

If you are using an AI-assisted code editor to work on your project:

#### Cursor
1. Create a file in your project folder at `.cursor/rules/founder-prd-builder.mdc` (or add to `.cursorrules` in your root folder).
2. Copy the contents of [`src/founder-prd-builder/SKILL.md`](src/founder-prd-builder/SKILL.md) into that file.
3. In Cursor Composer or Chat (`Cmd + L` or `Cmd + I` on Mac, `Ctrl + L` / `Ctrl + I` on Windows), type:  
   > *"@founder-prd-builder Help me create a PRD for [feature name]"*

#### Windsurf
1. Add or append the contents of [`src/founder-prd-builder/SKILL.md`](src/founder-prd-builder/SKILL.md) to your `.windsurfrules` file in the root of your workspace.
2. In Cascade Chat, type:  
   > *"Follow the founder-prd-builder rules to interview me and write a PRD for [feature name]"*

#### VS Code (Cline / Roo Code)
1. Save the file to `.clinerules` or your custom prompt library.
2. Start a task asking the agent to act as `founder-prd-builder`.

---

### Method 3: Agentic CLI Tools & Plugin Managers (Claude Code, Antigravity CLI)

This repository includes native plugin manifests ([`plugin.json`](plugin.json) and [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json)), allowing it to be installed directly as a plugin package:

- **Antigravity / Gemini CLI Plugin Install:**
  ```bash
  agy plugin install rubensteinventures/agent-skills
  ```
  *Or manual local install:*
  ```bash
  mkdir -p ~/.gemini/skills/founder-prd-builder
  cp src/founder-prd-builder/SKILL.md ~/.gemini/skills/founder-prd-builder/SKILL.md
  ```

- **Claude Code:**
  ```bash
  mkdir -p .claude/skills/founder-prd-builder
  cp src/founder-prd-builder/SKILL.md .claude/skills/founder-prd-builder/SKILL.md
  ```
  Claude Code will automatically recognize the skill when you ask to plan or spec a feature.

---

## How to Run the Interview (User Guide)

When working with the AI, the interview is designed to be low-effort and stress-free:

1. **Start the Conversation:** Tell the AI what you want to build in plain English:
   > *"I want to build an invoice generator for freelance designers."*
2. **Answer with Quick Shorthand:** The AI will ask 1 to 3 multiple-choice questions at a time with lettered options. You can reply with brief shorthand like:
   > `1A, 2C, 3B`  
   ...or type your own custom explanation if none of the options fit.
3. **When You Don't Know:** Never guess or feel pressured. Simply say:
   > *"I don't know yet, what do you recommend?"*  
   The AI will log it under **Open Questions & Assumptions** with a sensible default recommendation.
4. **Transition to Engineering:** Once the vision and user journey are clear, the AI will alert you that it is entering the **Engineering Gates** to define data handling, failure recovery, and scope boundaries.
5. **Get Your PRD:** Once the gates are complete, the AI will generate a complete, structured PRD (saved to `docs/prds/prd-[feature-name].md` or delivered in chat). You can hand this document directly to developers or feed it to AI coding agents to build your application without confusion.

---

## References & Prior Art

The enhancements to `founder-prd-builder` synthesize best-in-class concepts and workflows from leading PRD development skills across the AI engineering community:

1. **[James Rochabrun's PRD Generator](https://github.com/jamesrochabrun/skills/blob/main/skills/prd-generator/SKILL.md)**
   - *Key Ideas Incorporated:* Standard PM discovery taxonomy, metrics frameworks (AARRR Pirate Metrics, Google HEART Framework, North Star, OKRs), distinct usage patterns (New Feature, Enhancement, New Product, Quick One-Pager), and automated PRD validation standards.

2. **[The Utopia Studio's Agent PRD](https://github.com/The-Utopia-Studio/skills/blob/main/skills/founder-productivity/agent-prd/SKILL.md)**
   - *Key Ideas Incorporated:* The foundational rule of "PRD before code", strict interrogation standards (pushing back directly on vague answers like "relevant context" or "good UI"), preventing the "strategy-doc trap" by explicitly enforcing engineering gates (state, failure modes, data contracts, exit conditions), and treating "I don't know" as design work tracked in Open Questions rather than guessing.

3. **[Snarktank's Ralph PRD](https://github.com/snarktank/ralph/blob/main/skills/prd/SKILL.md)**
   - *Key Ideas Incorporated:* Frictionless multiple-choice lettered questioning format (A, B, C, D) for rapid founder iteration, explicit "Writing for Junior Developers / AI Agents" clarity guidelines, numbered functional requirements, verifiable checkbox acceptance criteria (`[ ]`), browser/UI verification gates, and explicit Non-Goals sections to prevent scope creep.

4. **[Callum Bir's BA PRD Skills](https://github.com/gocallum/nextjs16-agent-skills/tree/main/skills/ba-prd-skills)**
   - *Key Ideas Incorporated:* Context-aware repository reconnaissance (scanning existing codebases vs greenfield projects before asking questions), Marty Cagan outcome-focused questioning (*Inspired*), Teresa Torres assumption testing (*Continuous Discovery Habits*), MoSCoW prioritization, and token-efficient formatting optimized for AI parsing.

---

## Maintainers

For instructions on releasing new versions and updating package manifests, see [MAINTAINERS.md](MAINTAINERS.md).

