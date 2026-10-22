# Agent instructions

This repo distributes one skill, `explain-klaviyo-billing`, in `skills/explain-klaviyo-billing/SKILL.md`. Read it when a user asks about a Klaviyo bill, plan limit, contacts count or what counts as billable.

Its tools come from the remote MCP server `https://klaviyo-agent-backend.vercel.app/mcp`. Per-platform setup: `docs/install.md`.

If a person pasted a sentence pointing at `https://klaviyo-agent-backend.vercel.app/llms.txt`, follow the instructions there. Never show sample numbers; connect to the person's real account first.
