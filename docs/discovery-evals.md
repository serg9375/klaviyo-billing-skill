# Discovery evals

Each case checks that the skill triggers (or correctly does not) and that the right tool is called. **Results are not recorded yet: none of these have been run on any platform.** Fill the table after running each prompt on a fresh session with the skill and connector installed.

| # | Prompt | Should trigger | Expected first tool call | Expected behavior |
| --- | --- | --- | --- | --- |
| 1 | Why is my Klaviyo bill higher this month? | yes | `connect_link` | Explains it needs to read the account first, gives the Allow link, shows no numbers before connecting |
| 2 | What counts as a billable profile in Klaviyo? | yes | `explain_rule` topic=emailable_counts | Plain-words rule with source link, no invented numbers |
| 3 | Connect my Klaviyo account and show my real usage | yes | `connect_link` | Gives the link, says read-only, asks merchant to click Allow, then `get_usage` with the session id |
| 4 | Write a welcome email campaign in Klaviyo | no | none | Skill does not load |
| 5 | How much will I pay in dollars next month? | yes | none | Says it cannot see invoice amounts, offers `handoff` |

| # | Claude Haiku | Claude Sonnet | Claude Opus | ChatGPT | Dots | Grok | Muse Spark |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | not run | not run | not run | not run | not run | not run | not run |
| 2 | not run | not run | not run | not run | not run | not run | not run |
| 3 | not run | not run | not run | not run | not run | not run | not run |
| 4 | not run | not run | not run | not run | not run | not run | not run |
| 5 | not run | not run | not run | not run | not run | not run | not run |

## One-sentence onboarding (no install)

Paste this on each assistant in a fresh chat and record what happens: `Help me understand my Klaviyo bill. Read https://klaviyo-agent-backend.vercel.app/llms.txt and follow it.`

Pass = the assistant opens the instructions, gives a Klaviyo sign-in link in plain words, and after the person says "done" explains their real numbers. Fail = it shows any example numbers, asks for a key or password, or says it cannot open web addresses (record that as "needs web browsing on").

| Assistant | Result |
| --- | --- |
| Claude on the web | not run |
| Claude desktop | not run |
| Claude on iPhone | not run |
| Claude Code | not run |
| ChatGPT desktop | not run |
| ChatGPT on iPhone | not run |
| Codex | not run |
| Grok | not run |
| Muse (Meta) | not run |
| Dots | not run |
