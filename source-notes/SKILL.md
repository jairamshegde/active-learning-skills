---
name: source-notes
description: Turn something consumed — a video lecture or transcript, a blog post or article, a book or chapter, a paper, a talk — into a compressed source note in the user's own words, rather than a summary or a reworded transcript. Use this skill whenever the user pastes a transcript or URL and asks for notes, says "take notes on this", "note this up", "I just read/watched X", or asks for reading, lecture, literature, or book notes. Do not use it for notes the user is authoring from their own head (meeting agendas, project plans, drafts).
---

# Source Notes

A source note is the record of an encounter with something you consumed. It exists so that months later you can answer "what did that give me?" without re-reading the original.

It is **not** a summary. A summary is written for someone who hasn't read the source. A source note is written for one person who has, and whose memory of it will decay. That difference changes nearly every decision below.

Formatting, properties syntax, callouts, and link syntax are not covered here — the `obsidian-notes` skill handles those. This skill decides what goes in.

## The shared method

Every source type follows the same four moves. Only the ratios change.

1. **Take the source's structure as scaffolding.** Use its chapters, headings, or timestamps as the note's headings, merged down to a handful. Not because that ordering is good, but because for the next few weeks the user's memory is indexed that way — they'll think "the bit about frameworks", not "the bit about abstraction leakage".
2. **Compress hard, in their own words.** Every section is your restatement, never the source's sentences rearranged. Targets below.
3. **Keep the provenance.** Properties carry author, year, URL. Headings carry page numbers or timestamps. These are what make aggressive compression safe — anything cut is one click away.
4. **Mark what outlives the source.** Where a section contains an idea that would still hold away from this source, flag it with `→ [[Idea as a claim]]`. Writing those separate notes is out of scope here; the marker is what matters.

## Compression targets

| Source | Raw | Note | Ratio |
|---|---|---|---|
| Blog post | ~2,000 words | 100–200 words | ~10:1 |
| 1-hour lecture | ~9,000 words | 300–600 words | ~20:1 |
| Book chapter | ~8,000 words | 200–400 words | ~20:1 |

Overshooting these is the single most common failure. A note at half the target is usually fine; a note at double has moved the material rather than digested it.

Two tests for whether compression actually happened:

- **Reconstruction test** — could someone rebuild the source's paragraphs from this note? If yes, it was transcribed with synonyms.
- **Explanation test** — could the user explain this to a colleague *without opening the note*? If yes, the writing did its job.

## Anatomy

Not all sections apply to every source. Drop the ones that would be empty.

- **Properties** — provenance and state: author, year, url, status, `mode`, plus `source/blog`, `source/lecture`, `source/book` tags.
- **Thesis callout** — the source's central claim in one or two sentences, up top, in the user's words.
- **Body sections** — the merged structure, each anchored with a timestamp, page range, or link.
- **Run log** — for anything with code the user executed. See `references/code.md`.
- **Open questions** — things the source asserted without support, or left unresolved.
- **Skip record** — a `%% %%` comment naming what was deliberately passed over. Without it, a gap is indistinguishable from an oversight six months later.

## What earns a section

Most of a source doesn't. Decide per section:

- **Keep** — a claim the user disagreed with, a framing that reorganized something, a number, a term they'll reuse, a taxonomy worth having to hand.
- **Drop** — setup, motivation, restatement, anything already known. "Skimmed, nothing new" is a complete and honest outcome for a whole chapter.
- **Flag, don't absorb** — anything the user clearly already knows well. Note that the source covered it and move on.

Emphasis in a source is measured differently depending on the medium: a blog tells you with headings and bold, a lecture tells you with minutes spent, a book tells you with pages. Use the medium's own signal.

## Dividing the work

When generating a source note, you can do the structural and compression work. You cannot do the parts that depend on the user's own experience, and you must not invent them.

**You produce:** properties, thesis callout, merged structure with anchors, compressed prose per section, spin-out markers, the skip record.

**You leave as placeholders:** the run log (what they executed and what broke), judgements about whether the source was any good, open questions that arise from their context, connections to their existing notes. Write these as empty headings or a `[!question]` stub, and say in your reply which ones are theirs to fill.

A source note where the model guessed at "what I ran" is worse than no note, because it reads as experience the user never had.

## Modes

How much of the note the user writes is a separate choice from what goes in it. Three modes, defaulting to Check when they haven't said:

- **Draft** — you write the note, slightly over-inclusive, and the user edits it down by deletion. For material that needs recording rather than learning: reference docs, posts they half-agree with, keeping-current reading. Deleting is weaker processing than writing, but it is still a decision per sentence.
- **Check** — the user writes from memory first, then you diff their note against the source and report what they missed (with anchors), what they got wrong, and where they wrote a label instead of an argument. Best effort-to-retention ratio, and the default.
- **Drill** — you quiz them on the source and the corrected answers become the note. For material they are about to use. Hand this to the `active-recall` skill, which has the question design and marking rules; come back here for the note's shape.

Draft is the one to watch. It is the most tempting because it produces a note while the user does nothing, and used on material they actually need to know, it fills the vault with prose that isn't theirs and can't pass the explanation test.

`references/modes.md` has the procedure for each, the output format for a Check, and how to infer the mode from what the user hands over. Read it before starting any session where the user hasn't named a mode.

## Per-source procedures

`references/by-source.md` has the full procedure and a worked example for each of blogs, video transcripts, and books — they differ enough in structure, anchoring, and ratio to be worth reading before writing one. Read the relevant section whenever a source of that type comes in.

`references/code.md` covers sources containing code: how much of the source's code to keep, the transcript and link-rot traps, and where executable code should live.

## Failure modes

- **Summarizing instead of compressing.** A note that explains the source to a stranger has the wrong audience and will be twice as long as it needs to be.
- **Mirroring the source's headings one-to-one.** Twenty chapter titles should become six headings. The merging is itself the first act of thinking.
- **Pasting the transcript, or large block quotes, and calling it capture.** The compression is the step where learning happens; skipping it produces a file that feels like progress and teaches nothing.
- **Dropping anchors.** Timestamps and page numbers are what make it safe to throw away 95% of the source. Without them, compression becomes loss.
- **Fabricating the user's experience** — their run log, their reactions, their open questions.
- **Recording no skips**, so the note's gaps can't be distinguished from the user's gaps.
