# Install the skill and connector per platform

Two pieces, always installed together:

- **Connector**: remote MCP server `https://klaviyo-agent-backend.vercel.app/mcp` (no auth on the endpoint; live data goes through Klaviyo's own Allow screen). REST fallback: `https://klaviyo-agent-backend.vercel.app/openapi.json`.
- **Skill**: [`skills/explain-klaviyo-billing/SKILL.md`](../skills/explain-klaviyo-billing/SKILL.md), the instructions that tell the assistant when and how to use the tools.

Status key: **tested** = run end to end, **documented** = steps follow the vendor docs but were not run, **unknown** = no vendor docs found.

| Platform | Status | Steps |
| --- | --- | --- |
| Claude Code | manifest validated (`claude plugin validate`), install not run | `/plugin marketplace add serg9375/klaviyo-billing-skill` then `/plugin install klaviyo-billing@klaviyo-billing-marketplace`. The plugin bundles the skill and `.mcp.json`. |
| Claude (claude.ai / Desktop) | documented | Settings → Connectors → Add custom connector → paste the MCP URL. Upload `skills/explain-klaviyo-billing` as a zip under Settings → Capabilities → Skills. |
| ChatGPT and Dots | documented | Settings → Apps & Connectors → Advanced → Developer mode, add the MCP URL as a connector. Skills ship as an OpenAI plugin: `plugin.json`, `mcp.json`, `skills/` at the repo root, and `.agents/plugins/marketplace.json`. The policy fields in that marketplace file are unverified. Dots reportedly reuses ChatGPT connectors and personal skills; no official Dots docs were found. |
| Grok (xAI) | documented | grok.com/connectors → New Connector → Custom → paste the MCP URL. Skills accepts `.zip`, `.skill` or `.md`; import the skill folder zip. SKILL.md compatibility is unconfirmed. Custom connectors are on paid plans. |
| Muse Spark (Meta) | unknown | API-only. Meta says the model adapts to MCP servers and custom skills, but no install flow was found. Use the MCP URL as a tool server in your agent harness and paste the `SKILL.md` body as the system prompt. |

## Fallback when a platform has no MCP support

Use the REST tools: import `/openapi.json` as an action/function set and paste the body of `SKILL.md` into the system instructions. Tool names match the MCP tools. `handoff` has no endpoint: the model composes the support summary itself.
