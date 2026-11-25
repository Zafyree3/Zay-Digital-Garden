---
{"dg-publish":true,"permalink":"/wiki/log/","title":"Wiki Log","tags":["wiki","log","system"],"created":"2026-08-10T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","dg-note-properties":{"title":"Wiki Log","type":"reference","tags":["wiki","log","system"],"created":"2026-08-10T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00"}}
---
# Wiki Log

> Chronological record of all wiki actions. Append-only.
> Format: `## [YYYY-MM-DD] action | subject`
> Actions: ingest, update, query, lint, create, archive, delete
> Rotate at 500 entries (rename to log-YYYY.md, start fresh).

> **Redaction rule — this log is published.** Private notes are logged by
> category and count only: never by title, path, or content. Write
> "3 private training notes", not the note names. If a detail would identify a
> private note, leave it out. Content already public elsewhere (the concepts and
> comparisons pages) may be described normally.

## [2026-08-10] create | Wiki initialized
- Domain: Zaf's personal knowledge (projects, AI/agent stack, research)
- Structure: SCHEMA.md, index.md, log.md, raw/, entities/, concepts/, comparisons/, queries/
- Located at Zaf's PKM/Wiki/ inside the Obsidian vault; WIKI_PATH set in ~/.hermes/.env

## [2026-08-10] ingest | POD / print-on-demand research
- raw: raw/articles/pod-shirt-business-2026.md
- created: concepts/print-on-demand.md, entities/cottony.md
- sources: cottony.sg, Printful/Printify 2026 guides (session research)

## [2026-08-10] ingest | DRM research
- raw: raw/articles/drm-games-2026.md
- created: concepts/drm.md

## [2026-08-10] create | agentic-ai concept
- concepts/agentic-ai.md — frames Zaf's Hermes/Ollama stack as an agentic system

## [2026-08-10] create | AI stack entities
- entities/ollama.md, entities/hermes-agent.md — the agentic stack documented
- index.md updated to 6 pages; WIKI_PATH set in ~/.hermes/.env

## [2026-08-10] ingest | CrossPoint firmware research
- raw: raw/articles/crosspoint-firmware-2026.md
- created: entities/xteink-x4-pro.md, concepts/crosspoint-firmware.md
- index.md updated to 8 pages

## [2026-08-11] ingest | Xteink firmware landscape + Reddit sentiment
- raw: raw/articles/xteink-firmware-landscape-2026.md
- created: 1 private comparison note — the firmware landscape (stock,
  CrossPoint, CrossInk, Papyrix, SUMI, Microreader, CrumBLE + safety + verdict)
- index.md updated to 9 pages

## [2026-08-11] update | Bionic Reading + flash steps
- the private firmware comparison: Bionic Reading explained (evidence
  caveat), verdict → CrossInk
- a private how-to note: full step-by-step (unlock check, full-flash backup,
  flash, verify, revert, golden rules)
- index.md updated to 10 pages

## [2026-08-11] ingest | FreeLLMAPI research
- raw: raw/articles/freellmapi-2026.md
- created: entities/freellmapi.md (token claim decoded, privacy catches,
  verdict: benchmark-only)
- index.md updated to 11 pages

## [2026-08-11] ingest | OmniRoute research
- raw: raw/articles/omniroute-2026.md
- created: entities/omniroute.md (honest token math, ToS flags, verdict:
  benchmark-only, more trustworthy than FreeLLMAPI)
- index.md updated to 12 pages

## [2026-08-11] create | Tailscale setup guide
- a private setup note: no-sudo install steps, tailnet auth, dashboard
  bind to tailnet IP (deferred — not yet implemented)
- raw: raw/articles/tailscale-hermes-2026.md
- index.md updated to 13 pages

## [2026-08-11] create | Hermes memory providers guide
- a private guide: memory stack, Mnemosyne vs Hindsight, install flow
  (deferred)
- raw: raw/articles/hermes-memory-providers-2026.md
- index.md updated to 14 pages

## [2026-08-11] create | E-reader book sync guide
- a private guide: WebDAV push (rclone) as the sync path, OPDS pull
  alternative, SD fallback; do after the firmware flash
- raw: raw/articles/xteink-book-sync-2026.md
- index.md updated to 15 pages

## [2026-08-22] update | SD card guidance corrected
- the private firmware comparison + a private how-to note:
  max 512GB (64GB fine); format exFAT first, FAT32 fallback if invisible
  (sources conflict — firmware-version dependent); no USB-C data transfer
  → use a microSD card reader; retire the bundled 16GB card

## [2026-08-24] create | First Aid entity set (course prep)
- created: entities/cpr.md, aed.md, recovery-position.md, choking-fbao.md,
  bleeding-control.md, burns.md, first-aid-moc.md
- sources: BCLS manual (REV 1.2 2022), SFA manual (Rev 1 2020), SCDF QRG
- all tagged #first-aid; MOC carries the key numbers (995/999/1777) and the
  airway→breathing→circulation connective thread
- index.md updated to 15 pages

## [2026-08-24] create | Training notes, batch 1 (private)
- created: 4 private training notes (one lesson each)
- source: lesson summaries 2026-08-24; terminology fact-checked against public sources
- NOT published to the garden

## [2026-09-01] create | Training notes, batch 2 (private)
- created: 2 private notes on the same topic — a cheat sheet and a flashcard deck
- linked from the batch-1 notes; index updated
- NOT published to the garden

## [2026-09-05] create | Private decision record
- created: 1 private decision record (council verdict, 5 advisors)
- index: a "Decisions (private)" section; NOT published

## [2026-09-05] create | Private tooling setup note
- created: 1 private setup note — venv CLI install, skill files, cookie hygiene,
  rollback, pitfalls
- index updated; NOT published

## [2026-09-05] create | Private reading list (root note)
- created: 1 private root note tracking repos discussed in chat, with status
  and links to related wiki pages
- rule: every repo discussed gets added (date + status)

## [2026-09-09] publish | First Aid + BCLS+AED course notes → digital garden
- Made PUBLIC (user decision): Study/First Aid Course/ (17 notes incl. 237-card
  deck) + Study/BCLS + AED Course/ (6 notes incl. flashcards)
- pushed to garden repo (Zay-Digital-Garden main) → Netlify auto-deploy live

## [2026-09-22] review + decision | Paper-trading bot review (private)
- reviewed the paper bot across its run; a coverage audit found the sample had
  gaps, so per-week figures were not trustworthy
- created: 1 private decision record — chose to ACCEPT the gaps; measure the
  sample in COVERED time, per-trade stats primary, never quote weekly P/L from
  gapped weeks
- conclusion: the positive live result sits in a favourable window and is not a
  proven edge; paper-only unchanged
- index updated (17 pages)

## [2026-09-22] cleanup | Vault linking pass — dead links + gaps (batch 2)
- created: concepts/personal-knowledge-management.md (type: concept, public) — PKM
  explained; resolves the 6 dangling tutorial links to "Personal Knowledge Management"
- fixed unresolved wikilinks: Topics/Plugins, Topics/Obsidian Starter Kit Tutorial,
  Topics/Topics, Topics/Canvas (de-linked Markdown/Folders/Flowchart/Wanderloots to
  plain text), and a broken link into a private study note
- wired linking gaps across private book, study, project and idea notes (names
  withheld), plus drm.md → a private idea note
- orphan count 81 → 44 (of which ~28 are correctly unlinked: raw sources, templates,
  meta files, daily notes)
- index updated (18 pages)

## [2026-09-22] create | JEV — calibrated decision model (entity)
- created: entities/jev.md — JEV defined from primary sources (HF papers Sep 2026:
  "Jev in the Wild", "JEV-as-a-Judge", "Visual Jev", "Just Ask Jev" + jevstyle.com
  and the Jev-Style GGUF model cards)
- key finding: JEV is a **decision** model (state + question + options → choice with
  calibrated probabilities, single token position). It does NOT write text — so it is
  NOT a phi4 replacement; it's the missing System-One layer (cascade router).
- runnable locally: Jev-Style v3 0.8B (79.2% typed decisions) or 2B Q4 at 1.3 GB,
  GGUF via llama.cpp / LM Studio
- also recorded in a private reading list + backlinked from ollama, agentic-ai
- index updated (19 pages)

## [2026-10-24] cleanup | Vault hygiene pass — orphans, dead links, dates

- **raw articles wired in**: all 9 `Wiki/raw/articles/*` captures had **0 inbound links**. Added a
  `## Raw articles` section to `Wiki/index.md` (total pages → 42) and cited each source from its
  entity's `## Related` (freellmapi, omniroute, xteink-x4-pro, hermes-agent, cottony)
- **dead links fixed**: two links (one in a private reading list, one in freellmapi) pointed
  at notes that never existed → unwrapped to plain text. **Unresolved links 2 → 0**
- **orphans 27 → 17** — the 17 remaining are by design (8 templates, 5 daily notes, 3 Wiki
  structural files, 1 garden post now linked from the MoC)
- **junk removed**: an empty canvas file; a stale Syncthing conflict file in the spaced-repetition
  plugin (9 Sep). `.gitignore` now covers `*sync-conflict*` and `.obsidian/workspace*.json`;
  `workspace-mobile.json` untracked (per-device layout shouldn't be versioned)
- **a private index of study tracks** was renamed and committed as a rename (it had been moved on
  disk but never committed)
- **⚠️ date correction**: notes written today were stamped **19 Oct — wrong**. The real date is
  **24 Oct**; a first `date` call returned a stale value. Six notes corrected. *Lesson: verify the
  date against `git log` timestamps, not just `date`.*
- **`Map of Content`** (published): replaced leftover scaffolding with a proper intro, linked the
  garden post

## [2026-10-26] decision | Cloud-GPU migration deferred — staying on the API

- Researched renting a GPU (Runpod RTX 3090 $0.50/hr; 30B model ≈ $6–11/mo at 10–20 h).
  Verified prices 26 Oct 2026, incl. the storage trap (idle volume disk $0.20/GB/mo vs network
  storage $0.07).
- **Verdict: not worth it now.** The only genuine privacy tier is owned hardware — inference needs
  the prompt in plaintext, so whoever runs the model can read it. A rented host removes the AI
  *vendor* but keeps root access; that bar needs a deliberate contract break, which is acceptable
  for non-work content.
- **Hard line unchanged:** work content stays on the local `work` profile (Ollama, zero API keys).
- Provider balance checked: enough credit to reach the next payday at the measured daily spend.
  **No top-up needed.**
- Gap found: **no fallback provider configured** — the agent hard-fails when credit runs out.

## [2026-11-07] create | Reading-server comparison (private)
- New private comparison page: a self-hosted reading server — Kavita vs Komga, plus
  the KOReader sync modes
- Verdict: **Kavita** for light-novel EPUBs (series/volume model, better EPUB
  progress handling); **Komga** only for comics-heavy use (lighter, fully free,
  Tachiyomi/Kobo integration).
- Key finding: the optimised EPUBs hash **differently** from the vault masters
  (KOReader partial-MD5 over 1024-byte samples), so a server library must hold the
  exact bytes the device opens or KOReader sync fails silently — and every
  re-optimise orphans existing progress.
- Both speak standard kosync; base URLs differ (`/api/koreader/<token>` vs `/koreader`).
- Sources: Komga + Kavita official docs, Kavita-vs-Calibre-Web comparison. Confidence: high.
- Also recorded: Jellyfin over Plex for video (Plex paywalled remote streaming Apr 2025;
  lifetime Pass now US$749.99) — Jellyfin/Kavita are separate containers, no overlap.

## [2026-11-07] update | Reading-server comparison — sync-mode correction
- **Correction (Zaf caught it):** the X4 Pro ⇄ Pixel sync works on **FILENAME** matching
  (`MD5(filename)`), the firmware default (`primaryMatchMethod(DocumentMatchMethod::FILENAME)`),
  NOT content hashing. That is why optimised (X4) and master (Pixel) files stay in sync.
- Therefore Kavita/Komga — which generate their own **content** hashes — cannot serve that
  same sync. Recommending they stay out of the progress path: kosync keeps progress,
  Kavita is catalogue/OPDS/phone reading only.
- Added: FILENAME mode is fragile to **renames** (OPDS download naming, importers,
  comma-cleanup), while content mode is fragile to **re-encodes**. Neither is free.

## [2026-11-25] cleanup | Log redacted — published-note rule applied
- The log is published, and older entries named private notes (training notes,
  decision records, reading list, an index of study tracks, a trading review) in their titles
  and bodies. Rewritten to category-and-count only; the technical findings that are
  already public stay.
- Rule added to the header above and to `SCHEMA.md`: private notes are never logged
  by title, path or content.
- Afterwards: run the publishing transform on this page again so the live copy picks
  up the redaction.

## [2026-11-25] publish | four concept pages + topic/home cleanup
- New: `concepts/homelab-to-cloud` — the home→cloud translation table, plus what
  transfers and what doesn't from a cloud-security curriculum.
- New: `concepts/self-hosted-reading-server` — catalogue/OPDS design, and why the
  indexer must not own reading progress (content hash vs filename matching).
- New: `concepts/home-services-stack` — what I self-host, the six rules, and a
  deliberate list of what the page *leaves out* (no addresses, ports or paths).
- Published: `concepts/personal-knowledge-management` — had been flagged for
  publication for months but never pushed, so it existed only in the vault.
- `topics/organisation` — added a Tags-vs-topics section; the Dataview table was
  replaced with a static list restricted to **published** notes, so the live page no
  longer links to private titles or dead paths.
- Garden home: Knowledge section now links the new pages; scaffolding text removed.
- Tooling: `~/hermes-pipelines/garden-publish/publish_notes.py` — deterministic
  transform (JSON frontmatter, slugified permalinks, root-relative wikilinks) with a
  link-resolution check that fails the run on any dead target.

## [2026-11-25] reconcile | Garden drift: flags vs what is live
- Audited every `dg-publish: true` flag against the garden repo. Two directions found.
- **Flagged but not live (10)** — published: the First Aid entity set (cpr, aed,
  recovery-position, choking-fbao, bleeding-control, burns, first-aid-moc),
  `Topics/First Aid`, and two research entities (freellmapi, jev). All clean;
  the first-aid notes had been public in the flag but dead on the site.
- **Live but not flagged (1)** — a private book index page and its cover images were
  removed from the garden; the vault note is `dg-publish: false` and lists the whole
  library, so the site should never have had it.
- **Dead links (14 targets, 6 pages)** — legacy pages rendered from Dataview tables
  that pointed at private or never-created notes. Fixed two ways: the transform now
  rebuilds Dataview as a list of *published* notes, and links that resolve to a
  private note degrade to plain text (`--allow-dead`) instead of shipping a 404.
- This log had no frontmatter at all despite being live since August; it now carries
  a proper published flag.
- `~/hermes-pipelines/garden-publish/reconcile.py` — repeatable audit: flags vs live,
  plus every dead wikilink in the garden.