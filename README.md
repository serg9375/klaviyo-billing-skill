# Understand your Klaviyo bill

Copy this sentence and paste it into your AI assistant (Claude, ChatGPT, Codex, Grok, Muse or Dots):

```
Help me understand my Klaviyo bill. Read https://klaviyo-agent-backend.vercel.app/llms.txt and follow it.
```

That is all. Your assistant gives you a link, you press Allow on Klaviyo's own page, and it explains your real bill in plain words. It only reads; it never asks for a password.

---

## For developers

An assistant skill that tells a non-technical Klaviyo merchant why their bill is what it is: percent of plan limit, room left, days left, and what counts as billable. It only shows the merchant's own account data, after they click Allow on a Klaviyo page. There is no sample mode. Read-only; it never asks for a key or token.

### Install (permanent, optional)

The sentence above works without installing anything. To install the skill and connector so the assistant remembers them:

| Platform | Quick start |
| --- | --- |
| Claude Code | `/plugin marketplace add serg9375/klaviyo-billing-skill` then `/plugin install klaviyo-billing@klaviyo-billing-marketplace` |
| Claude, ChatGPT, Dots, Grok, Muse | Add the MCP URL `https://klaviyo-agent-backend.vercel.app/mcp` and the skill; see [docs/install.md](docs/install.md) for exact steps and which are tested |

### Layout
- `skills/explain-klaviyo-billing/SKILL.md`: the skill ([Agent Skills](https://agentskills.io/specification) format)
- `.claude-plugin/`, `plugin.json`, `mcp.json`, `.mcp.json`, `.agents/plugins/`: plugin packaging for Claude Code and OpenAI
- `docs/`: install guide, discovery evals
- Connector backend: separate repo [serg9375/klaviyo-agent-backend](https://github.com/serg9375/klaviyo-agent-backend) (landing page at `/`, assistant instructions at `/llms.txt`, MCP at `/mcp`, OpenAPI at `/openapi.json`)
