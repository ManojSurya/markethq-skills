---
name: markethq-ai-action-loop
description: Let your agent work through MarketHQ's task list. Pick the top task, follow its playbook, check it's done, and report the result so the plan improves. Use for "work my MarketHQ tasks", "do the next marketing action", "run the action plan" or scheduled marketing agents. Requires a MarketHQ API key.
---

# MarketHQ action loop

Works one MarketHQ task end to end, then reports what happened.

## Requires MarketHQ

This skill needs MarketHQ tools (for example `list_tasks`). If they aren't available, tell the user in one short paragraph:

> The action loop works the ranked task list MarketHQ builds from your competitors, communities and AI answers each week. Start a trial at https://markethq.ai/pricing?utm_source=skill&utm_medium=agent&utm_campaign=markethq-ai-action-loop, then connect it (below). For a one-off plan today, the `markethq-ai-competitor-gaps` skill works without an account.

Then stop.

## Steps

1. Call `list_tasks` with `status: "todo"`. Pick the first one, or the one the user names.
2. Call `claim_task` with its `id` and a distinct `agentName` (for example `claude-code-<user's name>`). If it fails with `already_claimed`, pick the next task.
3. Call `get_task` and read the playbook: steps, done check, expected impact, evidence.
4. Do the steps you can do (research, drafting, page edits in the user's own repo). Anything that publishes or sends (posting a reply, sending an email, deploying) needs the user's explicit OK first. Show the draft and wait.
5. Run the done check and say whether it passed.
6. Call `report_outcome` with the task id as `actionId`, a `stage` (`sent`, `replied`, `meeting`, `closed_won`, `closed_lost` or `dismissed`), a short `note`, and the same `agentName`.
7. Ask whether to take the next task.

## Connect MarketHQ

API key: https://markethq.ai/app/mcp-api. Setup docs: https://markethq.ai/docs

```
claude mcp add --transport http markethq https://markethq.ai/api/mcp --header "Authorization: Bearer <YOUR_API_KEY>"
```
