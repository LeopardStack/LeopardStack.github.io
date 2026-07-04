---
title: "Building a Personal Blog with Hugo + PaperMod"
date: 2026-07-04T10:00:00+08:00
draft: false
summary: "How this site was built, doubling as a formatting demo for tech posts."
categories: ["tech"]
tags: ["Hugo", "Blog"]
cover:
  image: "images/cover.png"
  alt: "Hugo + PaperMod"
  caption: "This site runs on Hugo + PaperMod"
  relative: true
---

This is the English translation of the first tech post, demonstrating common formatting elements.

## Why Hugo

Hugo is a static site generator written in Go. It builds the entire site in
seconds, and paired with the PaperMod theme you get dark mode, full-text
search, and archives out of the box.

## Code blocks

PaperMod ships with line numbers and a copy button:

```python
def fib(n: int) -> int:
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a

print([fib(i) for i in range(10)])
```

## Images

Images live in the post's own `images/` directory:

```markdown
![description](images/example.png)
```

## Video embeds

YouTube uses Hugo's built-in shortcode:

```markdown
{{</* youtube dQw4w9WgXcQ */>}}
```

Bilibili uses this site's custom shortcode (pass the BV id):

```markdown
{{</* bilibili BV1xx411c7mD */>}}
```

> Good notes are not about recording everything, but about recording
> the things your future self will thank you for.
