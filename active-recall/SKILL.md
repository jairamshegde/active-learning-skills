---
name: active-recall
description: Run a retrieval-practice drill on something the user has consumed — a lecture, transcript, blog post, paper, book chapter, or documentation — by holding the source and asking questions the user answers from memory, then marking those answers against the source. Use when the user says quiz me, test me, drill me, check my understanding, "did I get this right", or wants to study, revise, or prepare for an interview or exam on specific material. Also use when a source-note session calls for Drill mode. Not for generating a quiz for someone else, and not for answering questions about a source — that is ordinary explanation.
---

# Active Recall

The user consumed something. You hold the source; they hold a decaying, lossy memory of it. The drill exploits that asymmetry: they answer from memory, you mark against the source.

Two things only an external quizzer can do, and they are the entire justification for this skill:

- **Ask about what they forgot.** A gap is invisible from the inside — material dropped entirely doesn't announce itself, so self-quizzing systematically tests what least needs testing.
- **Catch confident wrongness.** Crisp recall of something the source didn't say survives every internal review process. Only something holding the source catches it.

The output is corrected answers in the user's own words, which become the raw material for a source note. The drill is the work; the note is a byproduct.

## The mix

**80% thinking questions, 20% anchor questions.** Hold this ratio deliberately — left alone, question generation drifts toward what is salient in the text (definitions, names, taxonomies) rather than what is load-bearing for the user.

- **Anchor (20%)** — did the raw material land at all. Two or three per session, no more. They are a warm-up and a floor check, not the drill.
- **Thinking (80%)** — require the user to apply, discriminate, predict, or criticize. A correct answer should be impossible without having actually understood the thing.

`references/question-design.md` has the eight thinking-question types with worked examples, plus the anti-patterns that make a question look deep while still being answerable by phrase-matching. Read it before generating questions.

## Purpose is a required input

Without knowing what the user is building or why they consumed the source, questions degrade into a vocabulary test. "What are the five workflow patterns?" is a weak question; "your changelog job retries on failure — which pattern is that, and what would evaluator-optimizer add?" is a strong one, and only the second is possible with context.

If the user hasn't said, ask once, in one line, before starting. One question, then begin — don't interrogate them about their goals.

## Session protocol

1. **Confirm scope and purpose.** Which source, what they're using it for. One exchange, not a negotiation.
2. **Ask one question at a time.** Never present the full list. Seeing upcoming questions lets the user pattern-match across them and primes the answers.
3. **Free recall only.** No multiple choice — recognition is a different and much weaker operation than retrieval, and it is exactly the instinctive answering this skill exists to defeat. Do not use quiz-card tooling for this.
4. **Never ask in source order.** Following the source's sequence lets the user ride its narrative instead of retrieving. Jump around, and favour questions that span two distant sections.
5. **Mark each answer before the next question.** Verdict, the correction if any, and the anchor (timestamp or page) so they can go back. See `references/grading.md`.
6. **Probe thin answers once.** If they gave a label where an argument was needed, push a single follow-up — "you said it's about autonomy; autonomy over what, specifically?" One probe, never two. This is the recursive step that separates retrieval from recitation.
7. **Close with a weak-spot list** and the material that should become a note.

Eight to twelve questions for an hour of source material. Short sessions beat exhaustive ones.

## Defeating recency

The failure this skill most needs to avoid is the user answering from short-term memory of the last thing they read rather than retrieving a consolidated idea.

- Suggest a delay if they finished the source minutes ago. A day later is far more valuable than immediately after. Suggest once; respect their answer.
- Order questions against the source's sequence, never with it.
- Prefer questions that require combining two sections, because recent memory of either one alone won't answer them.
- Ask about implications the source never stated. Those cannot be answered by recall at all, only by holding the model and running it forward.

## Answering "I don't know"

A valid and useful answer. Give the correct answer immediately with its anchor, mark it as a gap, and move on. Do not hint toward it, do not ask a leading sub-question, and do not make the user guess — guessing from no knowledge builds nothing and wastes the question.

Flag it for a second pass later in the session, phrased differently.

## After the drill

The user's corrected answers are already compressed, already in their own words, and already filtered to what they could retrieve. That is better note material than anything generated from the source directly.

Offer to assemble them into a source note. If the `source-notes` skill is available, follow it for the note's shape; if `obsidian-notes` is available, follow it for formatting. Never fold in material the user never answered on — a note should reflect what they actually hold.

## Failure modes

- **Praise inflation.** Marking everything "good" destroys the signal the drill exists to produce. Say plainly when an answer was wrong or thin.
- **Trivia drift.** Names, dates, and numbers are only worth asking about when they carry an argument.
- **Giving away the answer in the question stem**, or in the previous question.
- **Teaching mid-drill.** Mark, correct briefly, move on. Explanation at the end, after the retrieval has happened — explaining first replaces retrieval with reading.
- **Too many questions.** Twelve hard questions answered properly beat thirty skimmed.
- **Quizzing on material the user never consumed.** If they skipped a section, that's a reading gap, not a memory gap; note it and don't test it.
