# Explain Klaviyo billing in numbers

An assistant skill that tells a non-technical Klaviyo merchant why their bill is what it is: percent of plan limit, room left, days left, and what counts as billable. It starts with sample data and only reads the merchant's own account after they click Allow on a Klaviyo page. Read-only; it never asks for a key or token.

Try it: ask "Why did my Klaviyo bill go up?" once the skill and connector are installed.

## Install

| Platform | Quick start |
| --- | --- |
| Claude Code | `/plugin marketplace add serg9375/klaviyo-billing-skill` then `/plugin install klaviyo-billing@klaviyo-billing-marketplace` |
| Claude, ChatGPT, Dots, Grok, Muse | Add the MCP URL `https://klaviyo-agent-backend.vercel.app/mcp` and the skill; see [docs/install.md](docs/install.md) for exact steps and which are tested |

## Layout
- `skills/explain-klaviyo-billing/SKILL.md`: the skill ([Agent Skills](https://agentskills.io/specification) format)
- `.claude-plugin/`, `plugin.json`, `mcp.json`, `.mcp.json`, `.agents/plugins/`: plugin packaging for Claude Code and OpenAI
- `docs/`: install guide, discovery evals
- Connector backend: separate repo [serg9375/klaviyo-agent-backend](https://github.com/serg9375/klaviyo-agent-backend) (MCP at `/mcp`, OpenAPI at `/openapi.json`, `/llms.txt`)
