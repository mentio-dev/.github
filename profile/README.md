# Mentio

**Social listening for developers.** Mentio watches ten platforms for your keywords, scores every mention for relevance, sentiment and intent, and delivers the ones that matter to Slack, Telegram, email, a webhook, or straight into your AI agent. API and MCP first: the dashboard is one client of the same API.

[mentio.dev](https://mentio.dev) · [Docs](https://docs.mentio.dev) · [API reference](https://docs.mentio.dev/api/keywords/create-keyword) · [Blog](https://mentio.dev/blog/) · [Dashboard](https://app.mentio.dev)

## Three ways in

```bash
# An AI agent: Claude Code, Cursor, Codex, claude.ai, ChatGPT, one MCP server
claude mcp add --transport http mentio https://mcp.mentio.dev/mcp
```

```ts
// TypeScript: npm install @mentio-dev/sdk
import { createMentio } from '@mentio-dev/sdk';
const mentio = createMentio({ apiKey: process.env.MENTIO_API_KEY! });
const { data } = await mentio.searchMentions({ query: { platform: 'reddit', intent: 'buy_intent' }, throwOnError: true });
```

```python
# Python: pip install mentio
from mentio import Mentio
for m in Mentio(api_key="mk_live_...").mentions.search(platform="reddit", intent="buy_intent").data:
    print(m.classification.relevance, m.post.url)
```

```bash
# The command line: npm i -g @mentio-dev/cli
mentio auth:login && mentio mentions:watch --platform reddit | jq -r '.post.url'
```

## What it watches

| Platform | What arrives | How often |
| --- | --- | --- |
| Reddit | Posts, every subreddit, through the official API | every 30 minutes |
| Hacker News | Stories and comments | every hour |
| X | Posts and replies, with the parent post and follower count | every hour |
| GitHub | Issues and pull requests that name the term | every 15 minutes |
| Bluesky | Posts, the whole network | live, within seconds |
| LinkedIn | Public posts | every 3 hours |
| Stack Overflow | Questions and answers | every hour |
| DEV | Articles | every hour |
| YouTube | Videos | twice a day |
| News | Web articles | every 15 minutes |

Every mention carries a relevance score, a sentiment, and intents: `buy_intent`, `question`, `complaint`, `praise`, `comparison`. Keywords can be restricted per platform.

## The API, in five areas

Keywords · Mentions (search, triage, CSV export) · People (the authors behind the mentions, tags and merges) · Alerts and channels (instant rules and daily digests to Slack, Telegram, email, webhooks) · Analytics (summary, series, breakdown, share of voice). One [OpenAPI document](https://api.mentio.dev/v1/openapi.json), and every SDK below is generated from it on every release, so nothing is ever missing.

## Repositories

| Repository | What it is | Install |
| --- | --- | --- |
| [sdk](https://github.com/mentio-dev/sdk) | Official TypeScript SDK | `npm i @mentio-dev/sdk` |
| [sdk-python](https://github.com/mentio-dev/sdk-python) | Official Python SDK, sync and async | `pip install mentio` |
| [cli](https://github.com/mentio-dev/cli) | `mentio` on the command line, plus a live feed and MCP helpers | `npm i -g @mentio-dev/cli` |
| [claude-skills](https://github.com/mentio-dev/claude-skills) | Claude Code skills: the five-minute Reddit routine and its rules | copy into `.claude/skills/` |
| [openclaw-skill](https://github.com/mentio-dev/openclaw-skill) | The skill for OpenClaw agents | `npx clawhub@latest install mentio` |

Issues are welcome on any of them.

## Latest from the blog

- [Twitter keyword alerts in 2026: what still works on X](https://mentio.dev/blog/twitter-keyword-alerts/)
- [Reddit API pricing in 2026: is it free, what it costs, who gets access](https://mentio.dev/blog/reddit-api-pricing/)
- [How to find customers on Reddit with Claude Code](https://mentio.dev/blog/find-customers-on-reddit/)

## Pricing, in one line

$5 per keyword per month and $0.008 per matched mention, from a prepaid balance. No plan, no seat, no tier. Every account starts with $5.80 of credit, no card.

Built on Cloudflare Workers, Queues, D1 and Durable Objects. Made by [Pau](https://x.com/pauguirao).
