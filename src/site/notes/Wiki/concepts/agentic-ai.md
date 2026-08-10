---
{"dg-publish":true,"permalink":"/wiki/concepts/agentic-ai/","title":"Agentic AI","tags":["concept","agent","automation"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T23:33:21.537+08:00","dg-note-properties":{"title":"Agentic AI","created":"2026-08-10","updated":"2026-08-10","type":"concept","tags":["concept","agent","automation"],"sources":["raw/articles/pod-shirt-business-2026.md"],"confidence":"high"}}
---

# Agentic AI

## Definition
AI systems that don't just answer — they **act**: run tools, maintain
knowledge, execute multi-step tasks, and operate on schedules. The pattern
Zaf runs on his laptop: a gateway agent ([[Wiki/entities/hermes-agent\|hermes-agent]]) orchestrating
local models ([[Wiki/entities/ollama\|ollama]]) for private, offline work.

## The stack at a glance
- [[Wiki/entities/hermes-agent\|hermes-agent]] — the always-on assistant (Telegram gateway, cron jobs,
  file/tool access, this wiki)
- [[Wiki/entities/ollama\|ollama]] — local model server on the 8GB GPU (phi4-mini-stable for chat,
  qwen2.5vl for vision, nomic-embed-text for embeddings)
- Obsidian vault as the knowledge layer — of which this wiki is the
  machine-readable core

## Open threads (Zaf's ideas)
- "Orchestra of agents" — parallel subagents for research + coding
- Agentic trading bot — alerts → paper → real (data pipeline already exists
  via the daily S&P briefing)
- LLM Wiki as the shared memory layer for all of the above

## Related
- [[Wiki/entities/ollama\|ollama]] — the local inference backbone
- [[Wiki/entities/hermes-agent\|hermes-agent]] — the orchestrator that runs everything
