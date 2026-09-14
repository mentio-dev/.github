# Mentio

Social listening for developers. Mentio watches Reddit, Hacker News, X, GitHub,
Bluesky, LinkedIn, Stack Overflow, DEV, YouTube and news for your keywords,
scores every mention for relevance, sentiment and intent, and delivers the ones
that matter to Slack, Telegram, email, a webhook, or straight into your AI
agent. API and MCP first: the dashboard is one client of the same API.

- **Website**: [mentio.dev](https://mentio.dev)
- **Docs**: [docs.mentio.dev](https://docs.mentio.dev)
- **Blog**: [mentio.dev/blog](https://mentio.dev/blog/)

## Three ways in

```bash
# Claude Code, Cursor, Codex, claude.ai, ChatGPT: one MCP server
claude mcp add --transport http mentio https://mcp.mentio.dev/mcp

# The command line
npx @mentio-dev/cli auth:login && npx @mentio-dev/cli mentions:search --platform reddit

# Any language: the REST API, described by one OpenAPI document
curl -H "Authorization: Bearer $MENTIO_API_KEY" https://api.mentio.dev/v1/mentions
```

## Repositories

| Repository | What it is |
| --- | --- |
| [sdk](https://github.com/mentio-dev/sdk) | TypeScript SDK, `npm i @mentio-dev/sdk`. Generated from the OpenAPI document on every release. |
| [sdk-python](https://github.com/mentio-dev/sdk-python) | Python client, `pip install mentio`. Sync and async, typed. |
| [cli](https://github.com/mentio-dev/cli) | `mentio` on the command line: one command per endpoint, a live mentions feed, MCP helpers. |
| [claude-skills](https://github.com/mentio-dev/claude-skills) | Claude Code skills: the five-minute Reddit routine and the rules that keep it honest. |
| [openclaw-skill](https://github.com/mentio-dev/openclaw-skill) | The Mentio skill for OpenClaw agents, published to ClawHub as `mentio`. |

The SDKs, the CLI and the skill reference are generated from the API, so they
are always complete; these repositories are published from the main codebase
on every release. Issues are welcome on any of them.

## Pricing, in one line

$5 per keyword per month and $0.008 per matched mention, from a prepaid
balance. No plan, no seat, no tier. Every account starts with $5.80 of credit.

Built on Cloudflare Workers, Queues, D1 and Durable Objects. Made by
[Pau](https://x.com/pauguirao).
