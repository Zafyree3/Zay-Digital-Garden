---
{"dg-publish":true,"permalink":"/wiki/concepts/home-services-stack/","title":"What I self-host, and the rules that keep it safe","tags":["concept","selfhosted","homelab","privacy"],"created":"2026-11-25T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","dg-note-properties":{"title":"What I self-host, and the rules that keep it safe","created":"2026-11-25T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","type":"concept","tags":["concept","selfhosted","homelab","privacy"],"sources":[],"confidence":"high"}}
---
# What I self-host, and the rules that keep it safe

A small always-on machine at home, running services for one person. The list is less
interesting than the rules around it — but the list is what makes the rules concrete.

## The services

| Service | Job | Why not a subscription |
| --- | --- | --- |
| **Kavita** | Book and manga catalogue, served to an e-ink reader over OPDS | The library is mine; no store decides what I can read or when a book is removed |
| **Jellyfin** | Media library, transcoded on the GPU | No per-household device limits, no "this title left the catalogue" |
| **Actual Budget** | Personal budgeting, synced between my own devices | Bank-level data never leaves the house |
| **Ollama** | Local language models for private text work | Nothing sent to a provider; works with the network down |
| **Hermes** | The always-on assistant: schedules, files, notes, automations | Long-running automation on hardware I control |
| **A paper-trading bot** | Testing a strategy against live data, **paper money only** | Real money can wait until the paper record is honest |

## The rules

1. **No inbound ports.** Everything sits on a private overlay network
   (WireGuard-based), and access is granted per device, not per network. Nothing at
   home answers a request from the open internet, so there is no login page to protect.
2. **Secrets are never in git.** Not in the compose file, not in a note, not in a
   comment. A service gets exactly the secret it needs, from outside the repo.
3. **Backups are verified, not assumed.** An online database copy with an integrity
   check and row counts, on a timer, with retention — and a restore performed once so
   the backup is known to work rather than believed to.
4. **Media is deleted after analysis.** Anything fetched to watch or read is temporary
   unless it is being kept deliberately.
5. **Paper before money.** Trading automation runs on paper until its record is better
   than chance, measured properly.
6. **Services get containerised, daily tools stay native.** Containers for anything I
   would want to move between machines; the editor, the browser and the GUI tools stay
   installed normally.

## What this page deliberately leaves out

Addresses, ports, hostnames and file paths. A services list is a target list, and the
details are exactly what an attacker would want. The access layer is the thing doing
the work here — an encrypted tunnel alone proves *transport*, not *authorisation*,
which is the distinction worth keeping straight.

## Related
- [[Wiki/concepts/self-hosted-reading-server\|A self-hosted reading server]] — the reading server in detail
- [[Wiki/concepts/homelab-to-cloud\|Homelab → cloud]] — the same jobs, renamed, when rented by the hour
- [[Wiki/entities/ollama\|ollama]] · [[Wiki/entities/hermes-agent\|hermes-agent]] — the local AI stack
- [[Wiki/entities/xteink-x4-pro\|XTEINK X4 Pro]] — the device the book server feeds