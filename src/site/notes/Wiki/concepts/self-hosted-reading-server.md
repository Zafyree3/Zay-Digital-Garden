---
{"dg-publish":true,"permalink":"/wiki/concepts/self-hosted-reading-server/","title":"A self-hosted reading server that does not own your progress","tags":["concept","selfhosted","e-reader","docker","tool"],"created":"2026-11-25T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","dg-note-properties":{"title":"A self-hosted reading server that does not own your progress","created":"2026-11-25T00:00:00.000+08:00","updated":"2026-11-25T00:00:00.000+08:00","type":"concept","tags":["concept","selfhosted","e-reader","docker","tool"],"sources":["https://wiki.kavitareader.com/","https://komga.org/docs/guides/koreader/"],"confidence":"high"}}
---
# A self-hosted reading server that does not own your progress

A catalogue server for a book and manga library, read on an e-ink device. Two pieces
do the work: **Kavita** (or **Komga**) holds the library and serves **OPDS**; a
separate **kosync** service holds reading position. The interesting part is not the
install — it is the seam between them, and the traps around it.

## The shape

- **One container, one state directory.** Compose file in a git repo; the database and
  the library live in a state directory *outside* the checkout, with symlinks pointing
  in. The repo stays clean, and a backup is one directory rather than a set of rules.
- **Two libraries over the same filenames.** One over the master files (full quality),
  one over an optimised tree (grayscale, panel-sized) built for the device. The
  filenames are identical in both. That is the whole trick — see the next section.
- **A scoped account for the reader.** Non-admin, granted exactly one library, and
  the Download role is mandatory — without it browsing works and every download fails.
  The device's catalogue then shows one clean library instead of the same series twice.
- **OPDS with the key in the URL**, because an e-reader has no browser session to log
  in with.

## Who owns reading position

This is the decision that shapes everything else.

Catalogue servers index by **content hash**. Reader sync services like **kosync**
match by **filename**. They are different keys, and they cannot be reconciled by
hoping.

So: if the device syncs by filename, then the catalogue has to hand back the
*original filename* — which Kavita does, with an explicit `Content-Disposition`, so
progress carries across. And if the device does its own optimisation, serving
byte-identical pre-optimised files buys nothing, so serve the masters. Kavita and
Komga both keep their own progress records too; those are then treated as decoration,
not as the source of truth.

## Traps worth knowing before you hit them

- **Stale bind mounts.** Deleting or recreating a mounted directory while the container
  runs leaves the mount pointing at a dead inode. The symptoms are memorable: an empty
  library root, or a container that suddenly shows a fresh database and a registration
  page while the real database sits safely beside it. Diagnose by comparing inodes
  inside and outside the container; fix with `compose down` then `up -d`.
- **IPv6 without a route.** If DNS returns an IPv6 address first and the container has
  no IPv6 route, lookups fail with `Resource temporarily unavailable` — which surfaces
  as mysterious metadata and cover errors, not as a network error.
- **EPUB writes that silently do nothing.** EPUB internals usually use an `opf:`
  namespace prefix. An edit that assumes unprefixed `<item>` or `</metadata>` will
  match nothing and report nothing. Fail-closed checks ("is the value there after the
  write?") are the only thing that caught it.
- **Address changes.** An OPDS URL pinned to a DHCP address fails the day the lease
  moves. Read the address from the routing table rather than a hostname lookup, and
  fix it properly with a DHCP reservation.
- **Per-library and per-user identifiers.** Series and volume ids are scoped to a
  library; reading lists are scoped to a user. A script that works for the admin
  account will quietly do nothing for the device account unless it is told which
  library and which user it is acting as.
- **Light-novel volume numbering.** In a light-novel library the volume number may
  live in the series `Min/MaxNumber` with the volume's own number left at zero.
  Matching on the volume number resolves nothing, without an error.

## Worth doing on day one

- A DHCP reservation for the server, before touching OPDS.
- A *verified* backup: an online copy of the database with an integrity check and row
  counts, on a timer, with retention — and a restore you have actually performed once.
- Cheap reads for the device: the optimised library is what makes heavy volumes open
  quickly, and the masters stay untouched for everything else.

## Related
- [[Wiki/entities/xteink-x4-pro\|XTEINK X4 Pro]] — the e-ink reader this feeds
- [[Wiki/concepts/crosspoint-firmware\|CrossPoint firmware]] — the open-source firmware on that device
- [[Wiki/concepts/home-services-stack\|What I self-host]] — where this fits in the rest of the house
- [[Wiki/concepts/personal-knowledge-management\|Personal Knowledge Management]]