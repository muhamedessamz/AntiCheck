# AntiCheck

**Validate code architecture, security issues, and AI vibe-coding anti-patterns directly from your IDE using the Model Context Protocol (MCP).**

AntiCheck gives AI assistants like Claude, Cursor, and Windsurf the ability to act as Senior Engineers—auditing your local codebase for architectural flaws, security vulnerabilities, frontend issues, and common AI-generated bugs.

[![NPM Version](https://img.shields.io/npm/v/anticheck)](https://www.npmjs.com/package/anticheck)
[![NPM Downloads](https://img.shields.io/npm/dm/anticheck)](https://www.npmjs.com/package/anticheck)

---

## ⚡ Install & Usage

AntiCheck operates as an **MCP server**. It is meant to be run by an AI Assistant rather than consumed directly by a human.

### 1. Using with Cursor
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
Created and maintained by [**Muhamed Essam**](https://github.com/muhamedessamz).
Source code for the backend API and validation rules is proprietary to AntiCheck. The NPM Proxy package is licensed under MIT.
