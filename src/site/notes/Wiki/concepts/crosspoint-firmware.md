---
{"dg-publish":true,"permalink":"/wiki/concepts/crosspoint-firmware/","title":"CrossPoint Firmware","tags":["#concept","#tool","#source-type"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T23:59:42.627+08:00","dg-note-properties":{"title":"CrossPoint Firmware","created":"2026-08-10","updated":"2026-08-10","type":"concept","tags":["#concept","#tool","#source-type"],"sources":["raw/articles/crosspoint-firmware-2026.md"],"confidence":"high"}}
---

# CrossPoint Firmware

## Definition
Open-source, community-built firmware for the Xteink [[Wiki/entities/xteink-x4-pro\|xteink-x4-pro]]
(ESP32-C3 e-readers). Free, hackable, revertible — replaces the limited stock
firmware with a modern reader + wireless toolkit.

## Key benefits
- **Stock firmware is minimal**: Chinese/English only, basic file browser,
  limited fonts, no wireless transfer. CrossPoint replaces it wholesale.
- **Better reading**: EPUB 2/3 with embedded styles, hyphenation, kerning,
  footnotes, bookmarks, StarDict dictionary lookups, KOReader progress sync,
  auto page turn, focus reading.
- **Wireless everything**: browser file-transfer UI, Calibre wireless, OPDS
  catalog browser (8 servers), WebDAV, WebSocket uploads, OTA updates —
  books arrive over Wi-Fi, no cable juggling.
- **Customization**: custom fonts, themes, button remapping, sleep screens,
  refresh cadence; 24 UI languages.
- **Safety**: fully revertible to official firmware via the same web flasher.

## Install
Web flasher at crosspointreader.com/#flash-tools (USB-C + browser, no
software) — or esptool CLI. Revert via the same tools.

## Caveats
- Third-party-store units may be USB-locked → need the Xteink Unlocker first;
  on locked devices only CrossPoint/CrossInk are safe to flash (others can
  permanently brick).
- Verify the latest release supports the X4 Pro specifically (X4 support is
  confirmed; Pro is the same-generation refresh).

## Why it matters here
Zaf owns an [[Wiki/entities/xteink-x4-pro\|xteink-x4-pro]] — this is the upgrade path that makes it a
proper reading device, and a great example of the open-vs-locked debate in
[[Wiki/concepts/drm\|drm]].

## Related
- [[Wiki/entities/xteink-x4-pro\|xteink-x4-pro]] — the device it runs on
- [[Wiki/concepts/drm\|drm]] — the locked-firmware context
