# Callouts reference

## Contents

- [Syntax rules](#syntax-rules)
- [Built-in types](#built-in-types)
- [Choosing a type](#choosing-a-type)
- [Patterns worth copying](#patterns-worth-copying)
- [Custom callouts](#custom-callouts)

## Syntax rules

A callout is a blockquote whose first line starts with a type identifier in brackets.

```md
> [!info] Optional title
> Body text. Supports **Markdown**, [[Wikilinks]], ![[embeds]], lists, and code blocks.
```

- Every body line needs its own `>`. A line without it ends the callout.
- Leave a blank line before and after the callout block.
- Blank lines *inside* a callout still need a `>` — write `>` alone on the line.
- The identifier is case-insensitive: `[!TIP]` == `[!tip]`.
- Unknown identifiers fall back to the `note` style rather than erroring, so a typo fails silently. Check spelling.
- Omit the title and the type name is used as the title.
- Omit the body for a title-only banner: `> [!tip] Ship it Friday`.

### Foldable

A `+` or `-` immediately after the identifier makes the callout foldable. `+` renders expanded, `-` renders collapsed.

```md
> [!faq]- Are callouts foldable?
> Yes. Collapsed by default here.
```

Collapsed callouts are the right home for long source quotes, raw data, and screenshots that would otherwise bury the note's actual content.

### Nested

Add a `>` level per depth.

```md
> [!question] Can callouts be nested?
> > [!todo] Yes, they can.
> > > [!example] Multiple layers work.
```

Two levels is usually the practical limit for readability.

### Lists and code inside callouts

````md
> [!example] Migration steps
> 1. Snapshot the database
> 2. Drain connections
>
> ```bash
> pg_dump -Fc app > app.dump
> ```
````

## Built-in types

| Type | Aliases | Typical use |
|---|---|---|
| `note` | — | Neutral aside; the fallback style |
| `abstract` | `summary`, `tldr` | Compression of what follows |
| `info` | — | Context the reader may not have |
| `todo` | — | Outstanding work inside a note |
| `tip` | `hint`, `important` | Advice, shortcut, the thing to remember |
| `success` | `check`, `done` | Confirmed result, passing state |
| `question` | `help`, `faq` | Open question, FAQ entry |
| `warning` | `caution`, `attention` | Risk that costs time |
| `failure` | `fail`, `missing` | Something that didn't work, gaps |
| `danger` | `error` | Risk that causes damage or data loss |
| `bug` | — | Known defect |
| `example` | — | Worked example, sample code, walkthrough |
| `quote` | `cite` | Source quotation with attribution |

## Choosing a type

The type is a signal, not decoration — it tells a future reader how to triage the block at a glance.

- **Opening a long note** → `[!abstract]` (or `[!tldr]`) with three to five lines. Good on MOCs, literature notes, and anything over ~500 words.
- **Definition of the note's core term** → `[!info]` or `[!note]` near the top.
- **The single most important takeaway** → `[!tip]`. One per note. Two tips means neither is the takeaway.
- **"This will bite you"** → `[!warning]` for lost time, `[!danger]` for lost data or money. Keeping the distinction makes `danger` mean something.
- **Unresolved thinking** → `[!question]`, foldable off. Open questions should be visible; that's what pulls you back to the note.
- **Source material** → `[!quote]` with attribution on the last line, usually collapsed: `> [!quote]- Author, *Title*, p. 42`.
- **Action items** → `[!todo]` holding a task list, so tasks stay queryable while staying visually separate from the notes.

## Patterns worth copying

**Note header block** — summary plus provenance in one glance:

```md
> [!abstract] In one line
> Spacing reviews over increasing intervals beats massed practice for retention.

> [!info]- Source
> [[Make It Stick]], ch. 4 — read 2026-09-28
```

**Decision record:**

```md
> [!success] Decision
> Move the job queue to Postgres `SKIP LOCKED`.

> [!failure]- Rejected alternatives
> - Redis streams — another system to operate
> - Keep Celery — the lock contention is the problem, not the worker
```

**Open loop:**

```md
> [!question] Unresolved
> Does interleaving help for motor skills, or only declarative recall?
> Follow up in [[Interleaving]].
```

## Custom callouts

Vaults can define their own types with a CSS snippet; the `data-callout` value is the identifier you then write in brackets.

```css
.callout[data-callout="hypothesis"] {
  --callout-color: 108, 92, 231;
  --callout-icon: lucide-flask-conical;
}
```

`--callout-color` takes an RGB triple or any valid CSS color; `--callout-icon` takes a [lucide.dev](https://lucide.dev) icon ID or an inline SVG. Other callout CSS variables (border width, title styling) are available too.

Only write a custom type into a note if the user confirms the snippet exists — otherwise it degrades to a plain `note` and the intent is lost.
