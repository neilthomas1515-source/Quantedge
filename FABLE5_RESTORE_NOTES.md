# QuantEdge Fable 5 Restore Notes
## Created: June 15, 2026

### Why this file exists
Fable 5 was suspended by US government directive on June 12, 2026.
Claude Sonnet 4-6 is being used as a temporary replacement.
This file documents exactly what to restore when Fable 5 returns.

---

## What to change back in quantedge-v4.html

### 1. Display label (line ~1579)
CURRENT (Sonnet):
  <div style="font-size:10px;color:var(--t3)">claude-sonnet-4-6 ✦</div>

RESTORE TO:
  <div style="font-size:10px;color:var(--t3)">claude-fable-5 ✦</div>

### 2. AI Chat API call (line ~6851)
CURRENT (Sonnet):
  model: "claude-sonnet-4-6",

RESTORE TO:
  model: "claude-fable-5",

---

## What to change back in Cloudflare Worker (hidden-snow-d9ff)
Any Worker-side context trimming added during the Sonnet period should be removed.
The Worker should pass the full system prompt and full message history to Anthropic unchanged.

---

## Design intent (DO NOT change)
- chatState.history accumulates ALL day — this is intentional for brain learning
- No message history limits anywhere in v4
- Full masterPlaybook + strategyBible injected into every chat message
- Fable 5 was chosen specifically because it handles large context all day without 400 errors
