---
{"dg-publish":true,"permalink":"/wiki/entities/ollama/","title":"Ollama","tags":["#agent","#model","#local-ai","#tool"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T23:33:21.537+08:00","dg-note-properties":{"title":"Ollama","created":"2026-08-10","updated":"2026-08-10","type":"entity","tags":["#agent","#model","#local-ai","#tool"],"sources":["raw/articles/pod-shirt-business-2026.md"],"confidence":"high"}}
---

# Ollama

## What it is
Local LLM server on Zaf's laptop (RTX 3070, 8GB) — runs models privately at
`http://localhost:11434`, no cloud.

## Models in use
- **phi4-mini-stable** — chat (tuned, ~7.7GB/85% GPU, ~8s/turn)
- **qwen2.5vl:3b** — vision (reliable for names only; hallucinates details)
- **nomic-embed-text** — embeddings (768-dim) for vault Q&A
- Others: qwen3:4b, gemma3:4b

## Why it matters
The private inference backbone for [[Wiki/concepts/agentic-ai\|agentic-ai]]: Smart Connections
(Obsidian), Copilot vault Q&A, and Hermes auxiliary tasks all route through
Ollama so nothing leaves the machine.

## Related
- [[Wiki/concepts/agentic-ai\|agentic-ai]] — the system it powers
- [[Wiki/entities/hermes-agent\|hermes-agent]] — the orchestrator that calls it
