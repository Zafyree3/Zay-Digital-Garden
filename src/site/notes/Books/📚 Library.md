---
{"dg-publish":true,"permalink":"/books/library/","tags":["library"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T17:47:15.553+08:00","dg-note-properties":{"tags":["library"],"topic":["[[Topics/Organisation]]"],"created":"2026-08-10T04:30:00","updated":"2026-08-10T17:50:00"}}
---

# 📚 Library

All my books in one place. Reading status: unread → reading → done.


```base
filters:
  or:
    - and:
        - file.name.contains("📕")
        - file.ext == "md"
views:
  - type: table
    name: All Books
    order:
      - file.name
    columns:
      - property: file.link
        width: 260
      - property: title
        width: 180
      - property: author
        width: 120
      - property: category
        width: 140
      - property: pages
        width: 70
      - property: tags
        width: 120
  - type: table
    name: Unread
    filters:
      and:
        - file.hasTag("unread")
    columns:
      - property: file.link
        width: 260
      - property: author
        width: 140
  - type: table
    name: Reading
    filters:
      and:
        - file.hasTag("reading")
    columns:
      - property: file.link
        width: 260
      - property: author
        width: 140
  - type: table
    name: Done
    filters:
      and:
        - file.hasTag("completed")
    columns:
      - property: file.link
        width: 260
      - property: author
        width: 140
  - type: cards
    name: Covers
    order:
      - file.name
      - tags
    imageProp: cover
    imageFit: contain
    imageAspectRatio: 1
    image: note.cover

```


## Static list (for the web version)
| Book | Author | Category | Pages | Status |
| --- | --- | --- | --- | --- |
| [[Books/📕 First Aid Manual 11th Edition\|📕 First Aid Manual 11th Edition]] | DK | Health & Fitness | 296 | unread |
