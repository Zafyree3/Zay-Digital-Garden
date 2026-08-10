---
{"dg-publish":true,"permalink":"/digital-garden/how-i-built-this-pkm/","tags":["#digitalgarden"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T23:59:42.684+08:00","dg-note-properties":{"aliases":["How I Built This"],"tags":["#digitalgarden"],"created":"2026-08-10T23:50:00","updated":"2026-08-10T23:50:00"}}
---

# 🌱 How I Built This PKM

A personal knowledge system, built in one long session — from an empty vault
to a published garden with a local AI brain.

## The starting point
A fresh Obsidian vault, a YouTube playlist by Wanderloots about Obsidian and
digital gardening, and an agent (Hermes) to implement it all remotely.

## The layers
1. **The vault** — the Wanderloots system: tags (what a note IS) + topics
   (what it's ABOUT), daily notes, auto-filing, Maps of Content.
2. **The AI stack** — everything runs locally on one machine:
   - [[Wiki/entities/ollama\|Ollama]] serves the models (chat, vision,
     embeddings) — no cloud, no API keys
   - [[Wiki/concepts/agentic-ai\|Agentic Hermes]] files notes, publishes,
     and maintains this whole system
   - Smart Connections + Copilot make the vault searchable and chatty
3. **The databases** — Obsidian Bases for books, sources, projects and tasks.
4. **The wiki** — a machine-readable memory layer for agents
   ([[Wiki/entities/hermes-agent\|maintained by Hermes]]).
5. **The garden** — this website, published from the vault for free.

## The sync
The vault lives on a 24/7 laptop and mirrors to a phone via Syncthing —
private, no cloud. Notes made anywhere appear everywhere within seconds.

## Why
Because knowledge compounds when it's captured once, linked, and never
re-derived. And because a second brain is only as good as the habit of
feeding it — so the agent does the filing, I do the thinking.

*Written by the system itself, in August 2026.*
