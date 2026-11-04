<div align="center">

# Portarus CLI

**Create and manage [Portarus](https://portarus.com) gateways from your terminal.**

</div>

---

## Install

Nothing to install — run it with `npx`:

```bash
npx portarus
```

Requires **Node ≥ 18**. No runtime dependencies.

---

## Quick start

```bash
npx portarus
```

1. **Sign in** — opens your browser to authorize (Google or GitHub).
2. **Pick your source** — WhatsApp, Telegram, Slack, Discord, Instagram, Messenger…
3. **Pick your destination** — n8n, Make, Zapier, LangChain, custom HTTP…
4. **Paste your agent's URL** (must be `https`).

Portarus prints your **Gateway URL** and a **secret** (shown once). Put the Gateway URL in your source, and send `Authorization: Bearer <secret>` from your destination. That's it.

### One-liner (no prompts)

```bash
npx portarus whatsapp n8n https://your-agent.example.com
```

Positional order is **FROM TO URL**. Anything you omit is asked interactively.

---

## Commands

| Command | What it does |
|---|---|
| `npx portarus [FROM] [TO] [URL]` | Create a gateway (prompts for anything missing) |
| `npx portarus login` | Sign in only |
| `npx portarus logout` | Remove stored credentials |
| `npx portarus whoami` | Show the signed-in email and where your keys live |
| `npx portarus --help` | Show help |

---

## Options

| Flag | Effect |
|---|---|
| `--from=`, `--to=`, `--url=` | Set values by name instead of position |
| `--protection` | Enable **only** protection: rate limit, dedup, token cap |
| `--unification` | Enable **only** message unification |
| *(none)* | Enable everything (default) |
| `--device` | Device-code login — no browser (SSH / headless) |
| `--json` | Machine-readable output (for CI / scripting) |
| `--show-secret` | Include the secret in `--json` output *(may land in CI logs)* |
| `-y`, `--yes` | Don't prompt; use defaults |
| `-h`, `--help` | Show help |

`--protection` and `--unification` are mutually exclusive.

---

## Sources & destinations

**FROM** (source): `whatsapp` · `telegram` · `slack` · `discord` · `instagram` · `messenger` · `custom`

**TO** (destination): `n8n` · `n8n-self` · `make` · `zapier` · `langchain` · `custom`

Short aliases work too (`wa`, `tg`, `ig`, `fb`, `n8n-self`, `zap`, `lc`, …). The destination URL must be `https`.

> **Custom source?** The *custom webhook* source needs manual field mapping, so the CLI sends you to the dashboard to finish it.

---

## How auth works

- Browser login uses **loopback + PKCE** — the token never travels in a URL.
- No browser? Use `--device` for a device-code flow (enter a short code at [portarus.com/activar](https://portarus.com/activar)).
- The CLI token is **scoped to gateway create/read only** and is revocable from your dashboard.
- Credentials live in `~/.portarus/credentials.json`.

## Where your keys live

Each gateway gets an **ECDSA P-256** (ZKP) and an **RSA-2048** (quarantine) keypair, generated **on your machine**. Public keys go to the server; **private keys never leave your computer** — they're saved under `~/.portarus/keys/`.

```bash
npx portarus whoami   # shows the exact folder
```

Back that folder up — it's the only copy. Without it you can't decrypt quarantine or sign ZKP.

---

## Scripting / CI

```bash
npx portarus wa n8n https://agent.example.com --json --yes
```

```json
{
  "gateway_url": "https://gateway.portarus.com/g/abc123",
  "from": "whatsapp_business",
  "to": "n8n_cloud",
  "name": "My gateway 4f8a2c10",
  "dashboard_url": "https://portarus.com/dashboard",
  "email": "you@example.com"
}
```

The secret is **omitted** from `--json` unless you pass `--show-secret`.

---

<div align="center">

[**portarus.com**](https://portarus.com) · [**Docs**](https://portarus.com/docs) · [hello@portarus.com](mailto:hello@portarus.com)

© 2026 Portarus. All rights reserved.

</div>
