# Modes

Who writes the note. Orthogonal to what goes in it — a Draft note and a Drill note contain the same kinds of content, they differ in how much of the deciding the user did.

## Contents

- [Choosing the mode](#choosing-the-mode)
- [Draft](#draft)
- [Check](#check)
- [Drill](#drill)
- [Recording the mode](#recording-the-mode)
- [Mixing modes](#mixing-modes)

## Choosing the mode

Infer it from what the user hands over. Ask only when genuinely ambiguous, and ask in one line offering the two plausible modes rather than all three.

| What arrives | Mode |
|---|---|
| Source alone, "take notes on this" | Draft |
| Source + the user's own notes | Check |
| "Quiz me", "test me", "drill me on this" | Drill |
| Source + "I'll write it up" | Check — wait for their note, don't pre-empt it |
| Source + "I'm building X with this" | Offer Drill; purpose that specific signals material they'll use |

Default to Check when the signal is weak. Never silently switch modes mid-session.

If the user asks for Draft on material they've said they need to learn, write it, but note in one line that Check or Drill would retain better. Say it once; it's their call, and repeating it is nagging.

## Draft

You write the note; the user edits it down by deletion.

Procedure:

1. Write to roughly **twice** the compression target from SKILL.md — deliberately over-inclusive. The user's cut is the processing step, and there's nothing to cut from a note already at target length.
2. Flag the genuinely marginal material rather than burying it. A trailing `%% cut candidates: sections 3 and 5 are background you likely know %%` gives them a starting point.
3. Leave the user's sections — run log, judgements, open questions — as empty headings. Never fill them.
4. Hand over with one line naming what to cut first, not a summary of what you wrote.

What makes Draft safe is that the user still touches every sentence. If they accept it unedited, the note is a summary with their name on it, and it will fail the explanation test in a month. When a user repeatedly accepts Draft output untouched on material they care about, say so once.

## Check

The user writes from memory. You diff their note against the source.

This is the mode with the best effort-to-retention ratio, and the one where your coverage of the source is doing work the user cannot do for themselves.

Output exactly three lists, in this order — severity first:

**Wrong** — statements their note makes that the source doesn't support. The highest-value output, because misremembering is invisible from the inside. Give the correction and the anchor. Name it plainly when the note states it confidently.

**Thin** — where they wrote a label and the source made an argument. "Covers chunking" against four pages on why chunk size trades context against topic coherence. Usually means the section was recognized rather than understood. Quote their phrase, say what's missing beneath it.

**Missed** — significant material absent from their note, each with an anchor. Cap this at five or six items and order by how load-bearing they are, not by where they appear. A long missed list is noise: most omissions are correct editorial decisions, and the point of the cap is to force you to pick the ones that actually matter.

Then one line: what to add, what to fix, what to leave alone.

Rules:

- **Don't rewrite their note.** Report, and let them edit. Handing back a corrected version turns Check into Draft and takes the work away.
- **Don't flag correct omissions.** A section they consciously skipped isn't a miss. If the note has a `%%` skip record, respect it.
- **Don't mark style.** Their note being terse, fragmentary, or oddly organized is not a finding.
- **Say when the note is good.** A short "nothing wrong, nothing thin, two things missed" is a legitimate and useful result.

## Drill

Handed to the `active-recall` skill: it holds the question design, the 80/20 mix, and the marking rules. Return here for the note's shape once the drill is done, and build the note from the user's corrected answers rather than from the source.

## Recording the mode

Add a `mode` property to the note: `draft`, `check`, or `drill`.

It matters later. A note produced in Draft mode is a summary the user approved; a Drill note is material they demonstrably retrieved. Six months on, that difference decides whether they trust the note or re-read the source — and nothing else in the note reveals it.

```yaml
mode: drill
status: processed
```

## Mixing modes

Modes are per-session, not per-source. A twelve-chapter book can reasonably get Draft for the reference chapters, Check for the ones the user read closely, and Drill for the two they're about to build on.

When modes differ across chapter notes, record each chapter's own mode, and leave the hub without one.
