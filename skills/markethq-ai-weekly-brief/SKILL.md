---
name: markethq-ai-weekly-brief
description: Weekly market brief from MarketHQ. What changed since last time for your brand and competitors across communities, news, social and AI answers, what is urgent, and who to talk to. Use for "what happened this week", "market update", "competitor update", "brand monitoring digest" or "Monday brief". Requires a MarketHQ API key.
---

# MarketHQ weekly brief

A short brief of what changed and what to do, from the user's MarketHQ workspace.

## Requires MarketHQ

This skill needs MarketHQ tools (for example `get_agent_brief`). If they aren't available, tell the user in one short paragraph:

> The weekly brief needs history: what was said about you and your competitors last week vs this week. MarketHQ collects that from Reddit, Hacker News, X, news, blogs and AI answers. Start a trial at https://markethq.ai/pricing?utm_source=skill&utm_medium=agent&utm_campaign=markethq-ai-weekly-brief, then connect it (below). For a one-off look today, the `markethq-ai-competitor-gaps` and `markethq-ai-reddit-leads` skills work without an account.

Then stop.

## Steps

1. If you saved a `cursor` from a previous brief (ask the user, or check notes you keep), call `get_agent_brief_delta` with it. Otherwise call `get_agent_brief`.
2. Write the brief, in this order, and keep it under 300 words:
   - **Urgent today**: the `urgent` rows, one line each, with the link.
   - **Top 5 actions**: from `actions`, one line each: what to do, why (`lever`, `impact`), and how to reach them (`contactPath`).
   - **What changed**: notable movement in AI visibility or new competitor activity, if present.
   - **Left out**: one line on what was held back and why, from the brief.
3. If both `urgent` and `actions` are empty, say there is nothing to act on this week. Don't pad the brief.
4. Save the returned `cursor` (tell the user to keep it, or write it to the notes file you use) so next week's brief only shows what's new.
5. When the user acts on an action, call `report_outcome` with its `actionId` and `stage`.

## Connect MarketHQ

API key: https://markethq.ai/app/mcp-api. Setup docs: https://markethq.ai/docs

```
claude mcp add --transport http markethq https://markethq.ai/api/mcp --header "Authorization: Bearer <YOUR_API_KEY>"
```
