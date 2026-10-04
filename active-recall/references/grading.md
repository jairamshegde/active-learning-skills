# Marking answers

## Contents

- [Verdicts](#verdicts)
- [Probing](#probing)
- [Tone](#tone)
- [Closing the session](#closing-the-session)
- [Turning answers into a note](#turning-answers-into-a-note)

Mark every answer before asking the next question. Keep each mark to a few lines — verdict, correction if needed, anchor. Long explanations mid-drill replace retrieval with reading.

## Verdicts

Five outcomes. Name which one applies rather than offering a vague reaction.

**Right, and extends it.** The user said something the source didn't. Say so explicitly — this is the most valuable thing that can happen in a drill, and it is note material almost verbatim. Don't correct it toward the source; the source isn't the ceiling.

**Right.** Confirm briefly and move on. Nothing to add.

**Right, wrong reason.** The conclusion is correct, the mechanism given isn't. Easy to miss and important to catch, because the user will carry the broken mechanism to the next problem. Mark it as partially wrong, not as correct.

**Thin.** A label where an argument was needed. "It's about autonomy" to a question about where the workflow/agent line sits. Usually means the idea was recognized rather than retrieved. Probe once (below) before marking.

**Wrong.** Say so directly, give the correction with its anchor, and when the answer was stated confidently, name that too: "that was stated firmly and it isn't what the source says — worth flagging, because confident wrongness is the thing you can't catch on your own."

## Probing

One follow-up on thin or wrong-reason answers. Never two — a second probe becomes an interrogation and the user starts performing rather than thinking.

A good probe takes the user's own words and pushes on the weakest joint:

- They said "it's about autonomy" → "autonomy over what, exactly? Tool choice, or the control flow?"
- They said "chunking matters a lot" → "what specifically breaks when a chunk is too large?"
- They said "reranking improves quality" → "what is the cross-encoder seeing that the bi-encoder couldn't?"

If the probe lands, upgrade the verdict and say the probe is what produced it — the user should see that the second attempt is where the retrieval actually happened. If it doesn't land, give the answer and move on.

Never probe a "right" answer looking for more. That punishes a correct response.

## Tone

Blunt and specific, never harsh. The drill's entire output is signal about where understanding is weak; inflating marks destroys it. Avoid opening every mark with praise, and don't soften a wrong answer into "close".

Equally, don't editorialize about the user's overall ability. Mark the answer, not the person.

## Closing the session

End with a short, concrete readout:

- **Gaps** — questions answered "don't know", with anchors. These are re-read targets, not re-quiz targets.
- **Broken mechanisms** — the right-wrong-reason answers. The most important list, because these feel like knowledge.
- **Strong** — what came back cleanly, briefly. Confirms what doesn't need revisiting.
- **Carried forward** — anything the user said that extended the source, or any open question they raised.

Suggest a second pass only when gaps clustered in one section. Rerunning a whole source immediately isn't spacing, it's repetition.

## Turning answers into a note

The user's corrected answers are already compressed, already in their own words, already filtered to what they could actually retrieve. That makes better note material than anything generated straight from the source.

Rules for assembly:

- Use their phrasing, not the source's. Tidy grammar, don't rewrite.
- Include corrections as corrections, not as if the user had said them: a `[!warning]` noting the thing they had backwards is more useful than silently fixing it.
- Anything they answered "don't know" on stays out of the note, or goes in as an open question. A note should reflect what they hold, not what the source contains.
- Their extensions and critiques are the highest-value content — give them their own sections.
- Follow the `source-notes` skill for the note's shape and the `obsidian-notes` skill for formatting, where available.
