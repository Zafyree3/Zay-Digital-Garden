---
{"dg-publish":true,"permalink":"/books/library/","tags":["library"],"created":"1970-01-01T07:30:00.000+07:30","updated":"2026-08-10T17:47:15.553+08:00","dg-note-properties":{"tags":["library"],"topic":["[[Topics/Organisation]]"],"created":"2026-08-10T04:30:00","updated":"2026-08-10T17:50:00"}}
---

# 📚 Library

All my books in one place. Reading status: unread → reading → done.


```base
---
views:
  - name: All Books
    type: table
    filter:
      operator: and
      conditions:
        - field: tags
          operator: contains
          value: book
    sorts:
      - field: file.name
        direction: asc
    columns:
      - field: file.link
        name: Book
      - field: author
        name: Author
      - field: category
        name: Category
      - field: pages
        name: Pages
      - field: tags
        name: Tags
  - name: Unread
    type: table
    filter:
      operator: and
      conditions:
        - field: tags
          operator: contains
          value: book
        - field: tags
          operator: contains
          value: unread
    columns:
      - field: file.link
        name: Book
      - field: author
        name: Author
      - field: category
        name: Category
  - name: Reading
    type: table
    filter:
      operator: and
      conditions:
        - field: tags
          operator: contains
          value: book
        - field: tags
          operator: contains
          value: reading
    columns:
      - field: file.link
        name: Book
      - field: author
        name: Author
  - name: Done
    type: table
    filter:
      operator: and
      conditions:
        - field: tags
          operator: contains
          value: book
        - field: tags
          operator: contains
          value: completed
    columns:
      - field: file.link
        name: Book
      - field: author
        name: Author
  - name: Covers
    type: cards
    filter:
      operator: and
      conditions:
        - field: tags
          operator: contains
          value: book
    columns:
      - field: cover
        name: Cover
      - field: file.link
        name: Book
      - field: author
        name: Author
      - field: status
        name: Status

```


## Static list (for the web version)
| Book | Author | Category | Pages | Status |
| --- | --- | --- | --- | --- |
| [[Books/📕 First Aid Manual 11th Edition\|📕 First Aid Manual 11th Edition]] | DK | Health & Fitness | 296 | unread |
