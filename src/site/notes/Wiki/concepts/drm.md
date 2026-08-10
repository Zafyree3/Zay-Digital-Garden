---
{"dg-publish":true,"permalink":"/wiki/concepts/drm/","title":"DRM (Digital Rights Management)","tags":["concept","research","source-type"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T23:33:21.537+08:00","dg-note-properties":{"title":"DRM (Digital Rights Management)","created":"2026-08-10","updated":"2026-08-10","type":"concept","tags":["concept","research","source-type"],"sources":["raw/articles/drm-games-2026.md"],"confidence":"high"}}
---

# DRM (Digital Rights Management)

## Definition
Copy protection that limits how and when you can play a game: CD keys,
online activation, always-online checks, launcher requirements (Steam DRM),
and heavyweight anti-tamper like Denuvo.

## Key facts
- **Denuvo** integrates into the game code with hardware-tied tokens and
  online activation. It protects mainly the first ~30 days of sales — every
  copy eventually gets cracked (by 2019: same-week; by 2026: hypervisor
  bypass). Known costs: real performance hits (RE Village ran faster cracked
  until patched) and server expiries that can break legit copies.
- **DRM-free (GOG model)**: offline installer, no activation, no launcher.
  GOG has been strict no-DRM since 2008 and now focuses on preservation.

## The play-vs-download distinction (the important part)
A game without Steam DRM can be **played** forever from an installed copy
(single-player, no Steamworks dependency), but you generally **cannot
re-download** it if Steam dies — Steam is the delivery pipeline. Real
safety net: back up game folders, or own GOG/itch versions with offline
installers.

## Why it matters here
Relevant to buying decisions (which store to buy from) and to Linux/Proton
playability — DRM is a big factor in whether games run on the Steam Deck /
Linux setups Zaf uses.

## Related
- [[Wiki/concepts/print-on-demand\|print-on-demand]] — another digital-distribution control point (different
  domain, same "who controls the bits" question)
