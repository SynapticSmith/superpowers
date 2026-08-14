# Superpowers: The Absolute Beginner's Guide

Welcome to the world of Superpowers! If you're completely new to coding agents, artificial intelligence, or software development in general, you are in exactly the right place.

This guide is designed to be your complete, all-encompassing resource. It covers everything from what Superpowers is, to how to install it, how it changes the way you build software, and even how to integrate it into your own tools.

---

## 🌟 What is Superpowers?

Imagine you have a highly skilled, enthusiastic junior programmer sitting right next to you. They are eager to write code, but left to their own devices, they might just start typing blindly without fully understanding what you actually want to build.

**Superpowers is a system that teaches your AI coding agent how to think, plan, and verify its work before it writes a single line of code.**

Instead of jumping straight into coding, an agent with Superpowers will:
1. **Stop and ask questions:** It clarifies your ideas through a "Brainstorming" phase.
2. **Make a plan:** It breaks the work down into small, manageable 2-5 minute tasks.
3. **Write tests first:** It adopts "Test-Driven Development" (TDD), ensuring the code actually works.
4. **Review its own work:** It uses "Subagents" to review the code for quality and compliance with the plan.

In short, Superpowers gives your AI a "software development methodology."

---

## 🧠 Core Concepts

Before we install anything, let's understand a few terms you will see frequently:

- **Coding Agent (or Harness):** This is the AI program you chat with to write code (like Claude Code, Codex, Gemini, OpenCode, Cursor, etc.).
- **Skills:** These are specific abilities Superpowers teaches your agent. For example, `brainstorming` is a skill, and `systematic-debugging` is another. Superpowers automatically activates these skills at the right moments.
- **Subagents:** For complex tasks, your main AI agent will spawn smaller, temporary AI agents (subagents) to tackle specific parts of the job or to review code independently.
- **Worktree:** A safe, isolated copy of your code where the AI can experiment and build features without messing up your main project.

---

## ⚙️ Setup and Configuration

Superpowers can be installed into many different Coding Agents. You only need to follow the instructions for the specific agent you are using. If you use multiple, you must install Superpowers separately for each one.

### 1. Claude Code
Superpowers is available via the official Claude plugin marketplace.
- Open your terminal and type:
  ```bash
  /plugin install superpowers@claude-plugins-official
  ```

*(Alternatively, from the Superpowers marketplace)*:
- Add the marketplace:
  ```bash
  /plugin marketplace add obra/superpowers-marketplace
  ```
- Install:
  ```bash
  /plugin install superpowers@superpowers-marketplace
  ```

### 2. Codex CLI and Codex App
Superpowers is available via the official Codex plugin marketplace.
- **For CLI:** Type `/plugins`, search for `superpowers`, and hit Install.
- **For the App:** Click on "Plugins" in the sidebar, find `Superpowers` in the Coding section, and click the `+` icon.

### 3. Gemini CLI
- Install the extension:
  ```bash
  gemini extensions install https://github.com/obra/superpowers
  ```
- To update it later:
  ```bash
  gemini extensions update superpowers
  ```

### 4. OpenCode
OpenCode uses its own plugin manager. Add superpowers to your `opencode.json` file (either globally or in your project):
```json
{
  "plugin": ["superpowers@git+https://github.com/obra/superpowers.git"]
}
```
*Restart OpenCode after saving the file.*

### 5. Cursor
- In the Cursor Agent chat, type:
  ```text
  /add-plugin superpowers
  ```
- Or search for "superpowers" in the plugin marketplace.

### 6. Factory Droid
- Register the marketplace:
  ```bash
  droid plugin marketplace add https://github.com/obra/superpowers
  ```
- Install:
  ```bash
  droid plugin install superpowers@superpowers
  ```

### 7. GitHub Copilot CLI
- Register the marketplace:
  ```bash
  copilot plugin marketplace add obra/superpowers-marketplace
  ```
- Install:
  ```bash
  copilot plugin install superpowers@superpowers-marketplace
  ```

---

## 🚀 How to Use Superpowers: The Basic Workflow

Once installed, you don't need to do anything special to "activate" Superpowers. It happens automatically. Here is what a typical session looks like:

1. **You ask for a feature:** You tell your agent, "Let's build a to-do list app."
2. **Brainstorming:** The agent will **not** write code immediately. It will ask you questions to refine the idea and present a design document in chunks for your approval.
3. **Using Git Worktrees:** Once you approve the design, the agent sets up an isolated workspace (a new branch) so it doesn't break your existing code.
4. **Writing Plans:** The agent breaks the approved design down into bite-sized, 2-5 minute tasks.
5. **Subagent-Driven Development:** The agent dispatches subagents to complete the tasks. It writes a failing test, writes the code to pass the test, and then independent subagents review the work for quality.
6. **Finishing:** Once all tasks are complete, the agent verifies everything works and asks if you want to merge the new feature into your main codebase.

---

## 🔌 Integration: Adding Superpowers to Custom Programs

If you are a developer building your own AI harness or program, you can integrate Superpowers. The core philosophy is that Superpowers is a zero-dependency plugin.

A true integration does two things:
1. **Injects bootstrap context:** It must load the `using-superpowers` bootstrap at the start of every session. This adds awareness of Superpowers to the conversation.
2. **Registers the skills directory:** It ensures the agent can discover all the skills without manual configuration.

**The Acceptance Test for Integrations:**
To prove your integration works, open a clean session in your harness and say exactly:
> "Let's make a react todo list"

If your integration is correct, the `brainstorming` skill will automatically trigger before any code is written. If it starts writing code immediately, the bootstrap context was not loaded correctly.

*(For a technical example of integration hooks across platforms like Windows/macOS/Linux, refer to the `docs/windows/polyglot-hooks.md` and `docs/README.opencode.md` files in the repository).*

---

## 🧪 Testing and Creating New Skills

If you want to create new skills for Superpowers (Note: changes to the core project have a very high bar for acceptance), Superpowers includes its own methodology.

1. **Use the `writing-skills` skill:** Tell your agent you want to write a new skill, and it will follow the project's strict guidelines.
2. **Testing:** Superpowers relies on integration tests that run actual headless Claude Code sessions.
   - Tests are located in the `tests/` directory.
   - You can analyze how much an agent thought and how many tokens it used via the `tests/claude-code/analyze-token-usage.py` tool.
   - Always run integration tests to verify your new skill works from start to finish without errors.

---

## 🤝 Need Help?

Superpowers is built by the community and the team at Prime Radiant.
- **Discord Community:** Join the conversation, ask questions, and share what you've built. [Join Discord](https://discord.gg/35wsABTejz)
- **Issue Tracker:** Run into a bug? Report it on [GitHub](https://github.com/obra/superpowers/issues).

Enjoy your new coding Superpowers!
