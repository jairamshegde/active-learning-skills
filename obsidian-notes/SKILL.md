---
name: obsidian-notes
description: Write, restructure, and format notes as Obsidian-flavored Markdown (.md) files ready to drop into a vault — YAML properties, wikilinks, embeds, callouts, tags, tasks, block references, Mermaid, and math. Use this skill whenever the user mentions Obsidian, a vault, wikilinks, callouts, daily notes, zettelkasten, PARA, or asks for notes, meeting notes, lecture/book notes, a summary "as a note", or wants existing text turned into linked notes — even if they never say the word "Obsidian".
---

# Obsidian Notes

Produce `.md` files that render correctly in Obsidian and fit into a linked vault, rather than generic Markdown dumped into a file.

The core idea: an Obsidian note is **plain text that earns its place in a graph**. Formatting is cheap; the value comes from properties that can be queried, links that connect the note to the rest of the vault, and structure someone can scan six months later.

## Workflow

1. **Decide the note type** — capture (fleeting), source (book/paper/meeting/lecture), concept (atomic/evergreen), index/MOC, or project. The type determines what structure the note needs and which properties are worth setting.
2. **Pick a filename.** It becomes both the note title and the target every link points at, so make it specific and stable: `Spaced repetition.md`, not `notes-final-2.md`. Avoid `#`, `^`, `|`, `[`, `]`, `:`, `/`, and `\` — they break links. Dates use `YYYY-MM-DD`.
3. **Write the properties block, then the body.** The body opens straight into content; no `# H1` repeating the filename.
4. **Link while writing, not afterwards.** Connections made in the middle of a sentence reflect actual thinking. A links section bolted on at the end rarely does.

## Properties (YAML frontmatter)

Properties sit at the very top of the file between `---` fences, with nothing above them. They are what makes a note findable months later, so treat them as data rather than decoration.

```yaml
---
tags:
  - learning/memory
  - evergreen
created: 2026-10-04
source: https://example.com/article
status: seedling
---
```

Rules that matter:

- Tags here are written **without** the `#`; that prefix is only for tags in the body. `tags` and `cssclasses` are built-in Obsidian properties and both expect a list — use the block form above, which survives editing in the Properties UI better than inline `[a, b]`.
- A property name carries a single type across the whole vault. Once `status` holds text, it can't hold a number in a different note without Obsidian objecting.
- Write dates as `YYYY-MM-DD` so they sort and parse correctly.
- Keep relationships out of the properties block. Links belong in the body, where the surrounding sentence explains why two notes are connected.
- Keep the property set small and repeatable. Properties exist to be filtered on, so a key that appears in exactly one note is doing nothing.

## Body structure

- Start headings at `##`. The filename already supplies the title, so an H1 only duplicates it. If the user wants one anyway, follow them.
- Write headings in sentence case and make them descriptive enough to be worth linking to: `## Why spacing beats cramming`.
- Keep paragraphs short. A blank line separates paragraphs; a single newline does not. For a hard break inside a paragraph, end the line with two spaces.
- Use lists for things that enumerate and prose for things that reason. A note that is entirely bullets usually means the thinking stopped halfway.
- `==Highlight==` the one or two claims that matter most, `**bold**` for terms being introduced, `*italic*` for emphasis and titles.
- Tasks are `- [ ]` and `- [x]`. Any other character between the brackets is a valid custom state, which themes and plugins style differently: `- [-] dropped`, `- [?] unsure`.
- Wrap notes-to-self in `%% comment %%` so they stay out of reading view.
- Link with intent. `[[Spaced repetition|reviewing on a schedule]]` reads as part of the sentence; a wall of bare brackets doesn't. Link the terms a reader would plausibly want to follow, not every noun that happens to match a filename.
- Reach for a callout when something interrupts the flow — a caveat, a definition, the key takeaway, a collapsed source quote. If half the note is callouts, none of them stand out.
- End with connections: a `## Related` list, or links woven through the prose.

## Reference files

- `references/syntax.md` — full syntax for links, embeds, block IDs, tags, tables, Mermaid, math, footnotes, and escaping. Read it before writing a table that contains wikilinks or images, any diagram, or any math; that is where silent rendering breaks come from.
- `references/callouts.md` — callout syntax, the thirteen built-in types and their aliases, and how to choose between them. Read it whenever a note needs more than `note`, `tip`, or `warning`.

## Common failure modes

- Frontmatter not starting on line 1, or a `#` left on frontmatter tags — the properties silently fail to parse.
- A callout body line missing its `>`, which splits the block into a quote followed by loose text.
- An unescaped `|` inside a table cell, which splits the column. Wikilink aliases and image sizes both contain one.
- Inventing links to notes that don't exist without flagging them. Unresolved links are a legitimate Obsidian pattern — clicking one creates the note — but say which ones were created so the user isn't surprised by a cluster of empty nodes in the graph.
- Reproducing a source wholesale instead of condensing it. A literature note should be the user's own compression plus a pointer back, with quotations kept short and clearly attributed.
- Letting chat formatting leak into the file: emoji headers, "Here's your note!", trailing offers. The file should contain the note and nothing else.
