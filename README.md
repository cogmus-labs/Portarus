<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="public/img/portarus-banner-dark.png">
  <source media="(prefers-color-scheme: light)" srcset="public/img/portarus-banner-light.png">
  <img alt="Portarus" src="public/img/portarus-banner-dark.png" width="100%">
</picture>

### The signal layer between your message source and your AI agent.

[![Build](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square)](#)
[![Cloudflare Workers](https://img.shields.io/badge/Cloudflare_Workers-edge-F38020?style=flat-square&logo=cloudflare&logoColor=white)](#)
[![Tests](https://img.shields.io/badge/tests-1363_passing-brightgreen?style=flat-square)](#)
[![License](https://img.shields.io/badge/license-proprietary-blue?style=flat-square)](#)

</div>

---

## The problem

Your AI agent receives messages straight from the source — WhatsApp, Telegram, Slack, whatever. And whatever gets sent, your agent has to deal with it:

- **Sliced messages** — "hi" / "I have a question" / "about pricing" as three separate calls
- **Duplicated messages** — the same thing, twice or more
- **Bot spam** — noise that eats your token budget
- **Token bombs** — oversized payloads that blow up your LLM costs

Your agent processes all of it. Pays for all of it.

## The fix

**Portarus sits in front of your agent** to simplify, protect, unify, and route. Every filter, threshold, and behavior is fully customizable per gateway — you control what gets through and how.

You get:

- **A simplified workflow** — one URL replaces your webhook, everything else stays the same
- **A fully protected agent** — rate limiting, deduplication, and token budgets block the noise before it reaches you
- **Unified messages** — rapid-fire messages from the same user are batched into one payload, giving your AI better context
- **Routing, blacklists, and more** — send messages to different endpoints by keyword, block specific users, and review everything that was filtered

Replace one webhook URL. No SDK, no code changes, no deploy.

---

## Get started

**1.** Create an account at [portarus.com](https://portarus.com)

**2.** Create a gateway — pick your source channel, your destination platform, and enter your agent's endpoint URL

**3.** Copy the Gateway URL: `gateway.portarus.com/g/{slug}`

**4.** Replace the webhook URL in your message source with the Gateway URL. That's it.

Your agent now receives filtered, deduplicated, unified messages — each one with a full audit envelope attached.

---

## What your agent receives

Every message your agent gets includes the original payload plus a `_portarus` envelope with the full processing result.

<table>
<tr>
<th>Before — raw payload</th>
<th>After — with Portarus</th>
</tr>
<tr>
<td>

```json
{
  "user_id": "user_823",
  "message": "I need help with billing",
  "timestamp": "2026-09-08T14:30:00Z"
}
```

</td>
<td>

```json
{
  "user_id": "user_823",
  "message": "I need help with billing",
  "timestamp": "2026-09-08T14:30:00Z",
  "_portarus": {
      "user": "user-id",
      "message_unified": "First-message, Second-message, Third-message"
      "status": { "processed": true },
      "security": { 
            "response": Pass|Harm, 
            "reason": "token-bomb | rate-limit | duplication" 
            },
      "keyword_routing": { "matched": false },
      "latency_ms": 47,
      ...
  }
}
```

</td>
</tr>
</table>

Your agent parses `_portarus` to know exactly what happened — was it processed? which status? was it routed? how long did it take? Every decision is traceable.

---

## Docs

Full documentation at [portarus.com/docs](https://portarus.com/docs).

| I want to... | Go to |
|---|---|
| Set up my first gateway | [Quick Start](https://portarus.com/docs#quickstart) |
| Configure rate limits, dedup, or token budget | [Filters](https://portarus.com/docs#filters) |
| Batch rapid-fire messages into one | [Message Unification](https://portarus.com/docs#unification) |
| Route messages by keyword | [Keyword Routing](https://portarus.com/docs#routing) |
| Share a gateway with my team | [Sharing](https://portarus.com/docs#sharing) |
| Understand my traffic metrics | [Insights](https://portarus.com/docs#insights) |
| Debug a blocked or missing message | [Troubleshooting](https://portarus.com/docs#troubleshooting) |
| Read the full delivery envelope spec | [Envelope Reference](https://portarus.com/docs#envelope) |

---

## Stats

| | |
|---|---|
| **Response time** | `202 Accepted` in <100ms at the edge |
| **Global edge** | Cloudflare Workers — 300+ cities worldwide |
| **Test suite** | 1,363 tests passing (unit + security + integration + performance) |
| **Fail-open** | Your agent always receives its messages — infrastructure failures never block delivery |
| **Encryption** | AES-256-GCM at rest, HMAC-signed gateway URLs, SSRF protection on all outbound calls |
| **Delivery** | Async with retry — your message source gets `202` immediately, your agent gets the payload in the background |

---

<div align="center">

[portarus.com](https://portarus.com) · [Docs](https://portarus.com/docs) · [hello@cogmus.com](mailto:hello@cogmus.com)

© 2026 Cogmus. All rights reserved.

</div>
