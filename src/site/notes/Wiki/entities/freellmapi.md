---
{"dg-publish":true,"permalink":"/wiki/entities/freellmapi/","title":"FreeLLMAPI","tags":["tool","agent","model","llm"],"created":"2026-08-11T00:00:00.000+08:00","updated":"2026-10-02T00:00:00.000+08:00","dg-note-properties":{"title":"FreeLLMAPI","created":"2026-08-11T00:00:00.000+08:00","updated":"2026-10-02T00:00:00.000+08:00","type":"entity","tags":["tool","agent","model","llm"],"sources":["github.com/tashfeenahmed/freellmapi README + docs (2026-10-02)","repo docs: architecture, compression pipeline","raw/articles/freellmapi-2026.md"],"confidence":"high"}}
---
# FreeLLMAPI

## What it is
An OpenAI-compatible gateway that stacks the free tiers of **~34 providers / 474 model
families / 635 free endpoints** behind ONE base_url. **34.4k★, MIT, TypeScript** (grew from
18k★ in Aug 2026). Claims **~7.4B tokens/month** aggregate. Self-host (Docker / desktop app /
npm) or hosted premium (**$19/yr** — the paid tier only affects catalog freshness).

**Endpoint:** local Express proxy on **:3001**, one `freellmapi-…` bearer token. Serves
`/v1/chat/completions`, `/v1/responses`, `/v1/messages` (Anthropic wire format → Claude Code
works), `/v1/completions`, `/v1/embeddings`, `/v1/models`, plus images/video/audio.
**~40 MB RSS at idle** on Node 20+ — runs on a Raspberry Pi ⇒ fits the planned home server.

## The token claim, decoded
~7.4B/month = the **sum of ~34 separate free-tier quotas**, each with its own monthly budget
and daily caps. A theoretical ceiling, not a spendable pool. **Daily caps reset at UTC
midnight = 8am Singapore time** → the pool is freshest in the morning and **degrades through
the day** as the good models exhaust. Practical: schedule batch work for the SG morning.

## ⚠️ Context and complex jobs — the honest verdict

**Context is not a number — it's whatever model the router happens to pick.** Selection is
**per request**, and models have different windows. Four things soften this, and one thing
makes it bite:

| Mechanism | What it does |
|---|---|
| **Sticky sessions** | Keeps a conversation on ONE model for **30 minutes**; after that a long thread can switch mid-flight |
| **Context handoff** | Optional compact handoff note keeps a thread coherent across a mid-chat switch |
| **Prompt compression** (opt-in, default OFF) | 4 modes: off/lossless/standard/aggressive. Dedups, filters tool output, compacts JSON, condenses old turns. **Fail-open + fidelity-gated** (numeric literals, diff hunks, error lines, ≥90% JSON keys must survive; invalid tool envelopes are discarded) |
| **Fusion model** | Virtual `fusion` fans a prompt to a panel in parallel + a judge synthesises one answer |
| Per-model windows & budgets | Listed at freellmapi.co/models |

**Why long agent sessions are the weak spot:**
1. Compression exists explicitly to *"keep more small-context models eligible"* — i.e. it widens
   the pool by shrinking your prompt, not by protecting quality
2. Token budgeting is an estimate (`chars / 4`) — imprecise for mixed code/prose
3. **A Hermes session with a big system prompt + tools + vault context is 20–60k tokens, which
   filters the pool down to large-context models — and those are the first to hit daily caps**
4. Compression is **off by default**, so out of the box there's no defence at all

**Complex/agentic jobs:** better than expected — **tool calls are handled properly**
(plain-text tool calls are *rescued* into real `tool_calls`, and tool requests only route to
models that support them). Vision input, structured outputs, `seed`/`logprobs` also pass
through. **But**: no frontier models + late-day degradation + 30-min sticky expiry ⇒
**quality can shift mid-task**. Not a substitute for a paid model on real work.

**Debugging aid:** every response carries **`X-Routed-Via: <platform>/<model>`** — so you can
see which model actually served each call. That's the tool for judging quality honestly
instead of assuming.

## Routing internals
Per request: pick the highest-priority model with (a) a healthy key under (b) all its rate
limits → decrypt the key in memory → call → on 429/5xx cool that key down and retry the next
model in the chain. A Thompson-sampling bandit scores reliability/speed/capability/headroom.
Ledger tracks RPM/RPD/TPM/TPD per (platform, model, key). **Up to 20 failover attempts** within
a wall-clock budget. Six routing strategies + named chain profiles (`auto:<profile>` — e.g. a
coding chain, a vision chain). Same model on several providers collapses into one entry with
strict in-group failover. *Regional pinning is on the roadmap, not shipped.*

## The privacy catches (unchanged, and still decisive)
1. **Self-hosted = keys local, requests go direct to providers. Hosted = every prompt passes
   through their servers.** Privacy only holds self-hosted
2. **Free tiers are not private** — providers commonly train on free-tier data
3. **Auto-failover can route prompts to providers you didn't pick** — including Chinese
   providers (Z.ai, ModelScope). Pin the chain if sovereignty matters
4. **ToS risk**: aggregating free tiers likely breaches provider terms; keys can be revoked
5. No frontier models · no SLA · weekly churn · free installs get new models **30 days late**
   (premium gets the live feed same-day)

**Verdict unchanged: non-private work only.** Benchmarking, bulk classification, public-text
summaries, experiments. **Never private vault/NS/finance content** — that stays on the local
[[Wiki/entities/ollama\|ollama]] stack or a paid API.

## Implementing it in Hermes
FreeLLMAPI is a drop-in OpenAI-compatible base_url, so Hermes can use it two ways:

1. **As a `custom` provider / alias** — `base_url http://127.0.0.1:3001/v1` + the
   `freellmapi-…` token (token belongs in `~/.hermes/.env`, never config.yaml). Then
   `/model <alias>` switches a session to the free pool on demand.
2. **As a fallback chain entry** (`hermes fallback add|remove|list`).

**⚠️ Recommended shape: a SEPARATE Hermes profile** (e.g. `hermes-free`). Reasons: a fallback
on the main profile could silently send private vault prompts to free providers, and profiles
give isolated sessions/skills/memory. Fits the existing multi-profile setup.
**Also:** free providers can be wrapped as the free layer of a cascade — cheap/free first,
escalate to the paid model when the task is hard (same pattern as [[Wiki/entities/jev\|jev]]'s System-One idea).
Bonus: its **"custom provider" slot can wrap the local Ollama**, so one endpoint fronts local
+ free-cloud.

## Related
**Source captures:** freellmapi-2026
- [[Wiki/concepts/agentic-ai\|agentic-ai]] — the ecosystem this plugs into
- [[Wiki/entities/ollama\|ollama]] — the private alternative for real work
- [[Wiki/entities/jev\|jev]] — the System-One/cascade-router idea this could front-end
- cost-per-capability and hosting-cost comparisons, kept in private notes