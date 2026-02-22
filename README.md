# AntiCheck

**Validate code architecture, security issues, and AI vibe-coding anti-patterns directly from your IDE using the Model Context Protocol (MCP).**

AntiCheck gives AI assistants like Claude, Cursor, and Windsurf the ability to act as Senior Engineers—auditing your local codebase for architectural flaws, security vulnerabilities, frontend issues, and common AI-generated bugs.

[![NPM Version](https://img.shields.io/npm/v/anticheck)](https://www.npmjs.com/package/anticheck)
[![NPM Downloads](https://img.shields.io/npm/dm/anticheck)](https://www.npmjs.com/package/anticheck)
[![Website](https://img.shields.io/badge/Website-anticheck.vercel.app-blue)](https://anticheck.vercel.app/)

👉 **[Read the Full Documentation on our Website](https://anticheck.vercel.app/docs)**

---

## ⚡ Install & Usage

AntiCheck operates as an **MCP server**. It is meant to be run by an AI Assistant rather than consumed directly by a human.

### Usage Options

You can either run AntiCheck using `npx` (no installation required) or install it globally via `npm`. Both methods work perfectly with Claude, Cursor, and Windsurf.

#### Option A: Using NPX
This method fetches and runs the latest version dynamically.

```json
{
  "mcpServers": {
    "anticheck": {
      "command": "npx",
      "args": ["-y", "anticheck"]
    }
  }
}
```

#### Option B: Global NPM Installation
First, install the package globally on your machine:
```bash
npm install -g anticheck
```
Then, update your MCP configuration to use the installed command:

```json
{
  "mcpServers": {
    "anticheck": {
      "command": "anticheck",
      "args": []
    }
  }
}
```

---

### Configuring Your IDE
Navigate to `Cursor Settings > Features > MCP Servers` and click `+ Add New MCP Server`.
- **Name:** anticheck
- **Type:** command
- **Command:** `npx`
- **Args:** `-y anticheck`

*Restart Cursor to see the tools.*

### 2. Using with Claude Desktop
Add this to your `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "anticheck": {
      "command": "npx",
      "args": ["-y", "anticheck"]
    }
  }
}
```

### 3. Using with Windsurf
In your `~/.windsurf/mcp_config.json`:
```json
{
  "mcpServers": {
    "anticheck": {
      "command": "npx",
      "args": ["-y", "anticheck"]
    }
  }
}
```

---

## 🎯 Output Example
Once installed, ask your AI: *"Run a full architecture and security audit using anticheck."*

The AI will scan your code and output a structured diagnostic:

> ❌ **Anti-pattern detected:**
> 
> **Rule Title:** Missing Pagination (v1.0)
> **Severity:** High (Weight: 80)
> **Finding:** The endpoint `GET /users` executes `.ToList()` on the `DbSet` without `Skip` or `Take`.
> **Impact:** Will cause memory exhaustion and DB timeouts in production.
> **Fix:** I will implement offset pagination for you.

---

## 💡 Why AntiCheck?

AI coding tools are incredibly fast but often produce specific types of technical debt known as **Vibe Coding**. AntiCheck is specifically designed to hunt these down using highly-weighted inspection rules.

- ❌ **Detects Bad Architecture:** Catches god classes, missing DTOs, and dependency arrows pointing the wrong way.
- 🔒 **Highlights Security Smells:** Finds hardcoded secrets, authorization bypasses, and unvalidated inputs.
- ⚡ **Catches Vibe Coding Bugs:** Flags missing React/Vue hooks cleanup, swallowed exceptions, infinite recursion, and missing `loading/error` states.
- 🤖 **Native MCP Integration:** The AI Assistant uses AntiCheck to find the bugs, and then *fixes them for you automatically*.

---

## 🛠️ How it Works
The NPM package `anticheck` is a lightweight proxy that bridges standard MCP stdio streams to our robust `.NET 10` backend running at `https://anticheckhub.runasp.net`. This allows us to keep the evaluation rules centrally updated and lightning-fast.

---

## 📄 License & Ownership
Created and maintained by **Muhamed Essam**. Source code for the backend API and validation rules is proprietary to AntiCheck. The NPM Proxy package is licensed under MIT.

---

<div align="center">
  <h3>Let's Connect</h3>
  <a href="https://github.com/muhamedessamz">
    <img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" alt="GitHub">
  </a>
  <a href="https://www.linkedin.com/in/mohamedessamz/">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn">
  </a>
  <a href="mailto:mohamedessamzakariaa@gmail.com">
    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email">
  </a>
</div>
