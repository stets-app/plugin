# Stets for your AI app

[Stets](https://stets.app) builds and hosts websites, without a dashboard. You talk to the AI agent you already use,
and the agent writes, builds and publishes your site through Stets. Every change becomes a new version with a preview
address, and nothing goes live until you say "publish".

This repository holds two things: the address of Stets' MCP server, `https://stets.app/mcp`, in the formats that AI
apps read, and one skill that tells the agent how to work with it. There is no code to install. The first time your
app connects, you sign in with Google or Microsoft.

## Add Stets to your app

Checked with Stets, through to a chat that uses it:

| App | How |
|---|---|
| Claude (web, desktop, phone) | Settings → Connectors → Add custom connector, URL `https://stets.app/mcp` |
| Claude Code | `claude mcp add --transport http stets https://stets.app/mcp`, start `claude`, type `/mcp` to sign in |
| ChatGPT | Plugins → + → Add custom MCP server, URL `https://stets.app/mcp` |

Not tried with Stets yet (from each app's own docs):

| App | How |
|---|---|
| Claude Code, as a plugin | `claude plugin marketplace add stets-app/plugin`, then `claude plugin install stets@stets` |
| VS Code (Copilot) | Command Palette → MCP: Add Server → HTTP, URL `https://stets.app/mcp` |
| Cursor | Settings → MCP → add a server with the URL `https://stets.app/mcp` |
| Gemini CLI | `gemini extensions install https://github.com/stets-app/plugin` |
| Codex | `codex mcp add stets --url https://stets.app/mcp`, then `codex mcp login stets` |
| Any other app with MCP | a remote MCP server (Streamable HTTP) at `https://stets.app/mcp`, with OAuth |

Step by step, with pictures: [stets.app/start](https://stets.app/start).

## Then ask

- "Make me a one-page website for my bakery, with the opening hours and a contact form."
- "Move my WordPress site www.example.com to Stets, at the same addresses."
- "Go back to yesterday's version of my site."

## What's in here

| File | Read by |
|---|---|
| `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`, `.mcp.json` | Claude Code, VS Code |
| `plugin.json`, `mcp.json` ([Agent Plugins](https://agent-plugins.org) 1.0) | Cursor, VS Code, OpenAI |
| `gemini-extension.json` | Gemini CLI |
| `skills/stets/SKILL.md` | the apps that load skills: the order of work (connect, find the site, read the guide, change, preview, publish on a yes) |

## What it runs and sends

Nothing runs on your computer. Your app connects to `https://stets.app/mcp` and signs in there; the skill is text
for the agent. What Stets keeps is on [stets.app/privacy](https://stets.app/privacy).

Help: [stets.app/help](https://stets.app/help) · Privacy: [stets.app/privacy](https://stets.app/privacy) ·
Terms: [stets.app/terms](https://stets.app/terms) · hello@stets.app
