# MarketHQ skills

Agent skills for brand and competitor intelligence: AI visibility (ChatGPT, Claude, Gemini, Perplexity), Reddit and Hacker News leads, AI crawler checks, competitor gap analysis and content gaps. Works in Claude Code, Cursor, Codex and any agent that supports skills.

```
npx skills add ManojSurya/markethq-skills
```

| Skill | What it does | Account needed |
|---|---|---|
| `markethq-ai-visibility` | Which brands AI answers recommend in your category, and where you stand | No |
| `markethq-ai-reddit-leads` | Threads asking for a product like yours, with honest draft replies | No |
| `markethq-ai-crawler-check` | Whether your robots.txt lets AI search crawlers in, and the fix | No |
| `markethq-ai-competitor-gaps` | Where competitors are ahead, with evidence and one action per gap | No |
| `markethq-ai-content-gaps` | What to write next, plus a ready-to-write outline | No |
| `markethq-ai-weekly-brief` | What changed this week for you and your competitors | MarketHQ |
| `markethq-ai-action-loop` | Your agent works MarketHQ's ranked task list and reports back | MarketHQ |

Every skill runs in your own agent. Connect [MarketHQ](https://markethq.ai?utm_source=github&utm_medium=readme&utm_campaign=skills) and the same skills switch to weekly tracking across six AI assistants, communities, news and search, with history and evidence behind every number.

```
claude mcp add --transport http markethq https://markethq.ai/api/mcp --header "Authorization: Bearer <YOUR_API_KEY>"
```

API key: https://markethq.ai/app/mcp-api · Docs: https://markethq.ai/docs

## License

MIT for the skill files. The MarketHQ name isn't covered by the license, so please don't publish forks under it.
