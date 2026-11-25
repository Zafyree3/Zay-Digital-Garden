---
{"dg-publish":true,"permalink":"/wiki/entities/jev/","title":"JEV","tags":["model","local-ai","agent","tool","decision-model"],"created":"2026-09-28T00:00:00.000+08:00","updated":"2026-09-28T00:00:00.000+08:00","dg-note-properties":{"title":"JEV","created":"2026-09-28T00:00:00.000+08:00","updated":"2026-09-28T00:00:00.000+08:00","type":"entity","tags":["model","local-ai","agent","tool","decision-model"],"sources":["HF papers: Jev in the Wild / JEV-as-a-Judge / Visual Jev / Just Ask Jev (Sep 2026)","jevstyle.com","HF model cards (chaoliangUNSW Jev-Style, autotrust/JEV-9B)"],"confidence":"medium"}}
---
# JEV

**JEV is a *decision* model, not a chat model.** You give it a **state**, a **question**
and a **list of options**; it returns the choice **with calibrated probabilities**, read
from a single token position. It **does not write text.**

Trained with **RLCD** — Reinforcement Learning for **Calibrated** Decisions. That word is
the whole point: the output isn't a guess, it's a *calibrated* confidence (`is cat? → 0.95`).

## The idea — "System One" for AI

Most agent pipelines spend a full generative pass on every small decision. JEV's pitch is to
make those decisions **cheap and fast**, and reserve expensive deliberative models for the
hard cases:

> **accept when confident, escalate when unsure**

## Evidence (all September 2026)

| Claim | Number |
|---|---|
| As a judge vs a SOTA LLM judge | within **3 points** at **0.36% of the cost** |
| StarCraft II control | **$0.15/game** (JEV) vs **$3.56** (GPT-6); 0.42 s median |
| Visual Jev (batched questions per image) | 70.6% → **76.1%** accuracy; **8.9× faster** at N=32 |
| Ecosystem | **2,170 public JEV projects** on GitHub as of 22 Sep 2026 |

**Definition from the source:** *"Jev is a fast, low-cost decision model that answers
natural-language questions with choices, binary judgments, and scores."*

## What you can actually run (open models)

**Community "Jev-Style" line** — Qwen3.5-based, **GGUF**, runs in **llama.cpp / LM Studio**:

| Version | Size | Typed-decision score |
|---|---|---|
| **v3 (0.8B)** | tiny | **79.2%** on 2,000 decisions — 25,600-token inputs, 51 languages, 77 options |
| v2 (2B) Q4_K_M | **1.3 GB** | 82.4% accuracy on 500 held-out |
| v2 (2B) Q8_0 / BF16 | 2.1 GB / 3.9 GB | 81.6% |

*The line's own history is the honesty check: v1 53.4% → v2 73.5% → v3 79.2%. v1 was poor.*

**Other ports:** Open-Jev (2B / 9B / 27B), autotrust JEV-9B/27B — Apache-2.0 distills of a
proprietary teacher ("TypeSafe Jev 1.13"). Hub: **jevstyle.com**.

## ⚠️ Honest caveats

- Papers are **days old and HF-hosted** → not peer-reviewed
- Benchmarks are GLUE / AG News / BoolQ / SST-5 — **standard datasets, not your tasks**. Verify on your own data first
- Open models are **students of a proprietary teacher** → quality is capped by it
- Calibration claims (Brier / ECE) need independent replication
- **Weak spot is reasoning:** the judge paper says gaps widen when a judgment needs *checking a derivation* or *resisting an elaborate wrong answer*

## Why it matters here

- It's **not a replacement for [[Wiki/entities/ollama\|phi4-mini]]** — phi4 *generates*, JEV *decides*. Different jobs
- The natural role is a **cascade router**: let a local 0.8–2B model decide whether a task needs the cloud model at all → **cost control + privacy** (the common case never leaves the machine)
- Other candidates: spend-transaction categorisation, content triage (is this worth analysing?), note classification
- 8GB GPU: JEV is 1.3 GB (or far less at 0.8B) — it fits, but **not simultaneously with phi4's ~7.7 GB**, so it's a load-instead-of, not load-alongside

## Deferred — the test plan (decided 2026-09-22: not yet run)

Standing plan if this is ever picked up (user deferred after this research — they
have the picture, no experiment needed yet):

1. Download the **Jev-Style 0.8B v3 GGUF** (or 2B Q4, 1.3 GB)
2. Import into **Ollama** via a Modelfile (Hermes already talks to `localhost:11434`)
3. Test on **one real task with known ground truth** — spend-transaction
   categorisation is ideal (the 22 Sep statement analysis gives the labels)
4. Compare **JEV vs phi4-mini vs one cloud call** on accuracy, latency and cost
5. Expand only if it wins on a task actually performed; otherwise drop it

**Why it's not a phi4 swap:** phi4 *generates*, JEV *decides* — and they can't both
be GPU-resident on an 8 GB card (phi4 ≈ 7.7 GB), so it's a load-instead-of swap.

## Links
- [[Wiki/concepts/agentic-ai\|agentic-ai]] — the System-One / System-Two division of labour
- [[Wiki/entities/ollama\|ollama]] — where local models run
- Repo Watchlist — the pointers list