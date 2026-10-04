# By source type

## Contents

- [Blogs and articles](#blogs-and-articles)
- [Video lectures and transcripts](#video-lectures-and-transcripts)
- [Books](#books)
- [At a glance](#at-a-glance)

## Blogs and articles

Already edited. Someone chose the headings, cut the tangents, and bolded what mattered — so the structure can be taken almost as-is, and the ratio is the gentlest of the three.

**First decide whether it needs a source note at all.** Most posts carry one idea. If so, there is nothing to index: skip the source note, and let the idea stand on its own with the URL recorded against it. Write a real source note when the post is long or dense enough that you'd want to find your way back around inside it.

Procedure:

1. Take the post's own headings, merging any that cover the same ground.
2. Thesis callout first — the argument in one or two sentences.
3. Two to five sections, a short paragraph each.
4. Anchor with section links where the post has them; the URL in properties covers the rest.

Worked example — Anthropic's *Building effective agents*:

````md
---
tags:
  - source/blog
  - llm/agents
author: Schluntz, Zhang
year: 2024
url: https://www.anthropic.com/engineering/building-effective-agents
status: processed
---

> [!abstract] Thesis
> Most teams succeed with simple composable patterns and fail with frameworks.
> Pick the least agentic thing that solves the problem.

## Workflows vs agents

Both are agentic systems; the split is autonomy. A workflow runs along code
paths written in advance, an agent decides its own path at runtime. A gradient
in practice — the useful question is how much control flow you're handing over.
→ [[Workflows and agents differ by who controls the flow]]

## The five workflow patterns

Everything builds on the augmented LLM — a model with retrieval, tools, memory.

- **Prompt chaining** — fixed sequential steps, gated between them
- **Routing** — classify, then dispatch to a specialist path
- **Parallelization** — sectioning (split work) or voting (same work, N times)
- **Orchestrator-workers** — a model picks the subtasks at runtime
- **Evaluator-optimizer** — generate, critique, revise in a loop

## On frameworks

They hide the prompts and responses, which makes debugging guesswork and makes
added complexity feel free. Advice: call the API directly until you understand
what a framework would be abstracting.

%% skipped appendix case studies — revisit if building a support agent %%
````

Note that the pattern list has no spin-out marker. A taxonomy taken from one source is reference material, not the user's idea, and belongs here permanently.

## Video lectures and transcripts

The hardest case and usually the most frequent. A transcript is unedited: no paragraphs, no emphasis, filler throughout, and the same point restated three times in slightly different words. Two consequences:

- **Emphasis is time.** Six minutes on one topic and ninety seconds on another is the speaker telling you what mattered. Nothing in the text says so.
- **Visuals don't transcribe.** The best diagram in the talk appears in the transcript as "as you can see here". Ask the user for a screenshot, or redraw it as a Mermaid diagram — redrawing is itself compression.

Procedure:

1. **Spine first.** Headings and timestamps only, nothing else. If the video has chapters, start from those and merge them down — twenty chapters should become six or seven headings. This is the fastest place to do the editorial work.
2. **Then fill.** The user's version of this step is writing each section from memory and consulting the transcript only for gaps. When generating, the equivalent discipline is to write each section without the transcript open in front of you as a sentence bank — compress to the claim, not the phrasing.
3. **Anchor every heading with a timestamp link**, which is what makes 20:1 compression safe: `[[12:30](https://youtu.be/VIDEO_ID?t=750)]`.

Worked example — spine stage for a one-hour talk:

```md
## What an LLM is [00:00–08:58]
## Training and the assistant step [08:58–21:05]
## Scaling laws [25:43]
## Tool use [27:43]
## LLM OS [42:15]
## Security [45:43–58:37]
```

Filled stage, one section:

```md
## What an LLM is [[00:00](https://youtu.be/zjkBMFhNj_g)]

Parameters file plus a run file. The parameters are lossy compression of a large
slice of the internet — framing it as compression makes hallucination the
expected behaviour rather than a bug. The model dreams documents; sometimes the
dream happens to be accurate.
→ [[LLMs are lossy compression of their training data]]
```

Four lines standing in for nine minutes of speech. The raw transcript does not go in the note — if it needs to be searchable, it goes in a sibling file linked from the note, or a collapsed callout at the very bottom, never competing with the user's own writing.

## Books

Read over weeks rather than in one sitting, which makes the note a living document with state.

**Hub plus chapter notes.** A twelve-chapter book will not fit in one usable file. The hub carries provenance, a chapter checklist, and a running judgement; chapter notes exist only for chapters actually worked through. Short books can stay a single file with `## Ch. 4 — ...` headings.

The hub's checklist is the distinctive part: it records chapters skimmed with no note, chapters deliberately skipped with a condition for returning, and where the reader currently is. Four chapters marked "skimmed, nothing new" is a healthy note, not an incomplete one.

```md
> [!info] Where I am
> Ch. 8, p. 230. Resume at dense retrieval.

## Chapters

**Part 2 — Using pretrained models**
- [x] 4. Text Classification — skimmed, no note
- [ ] 5. Text Clustering — skipped, return if I need BERTopic
- [x] 7. Advanced Text Generation → [[HOLLM 07 — Chains and agents]]
- [ ] 8. Semantic Search and RAG ← here
```

Properties on the hub carry `status: reading`, `started:`, and the code repo if there is one. Chapter notes carry `chapter:`, `pages:`, `read:`.

Abandonment is a legitimate end state. Set `status: abandoned` and record why in one line — a half-read book with a recorded stopping point stays useful, one that trails off becomes something the user avoids opening.

## At a glance

| | Blog | Transcript | Book |
|---|---|---|---|
| Structure from | Its headings | Chapters/timestamps, merged | Chapters |
| Anchor | URL | Timestamp links | Page numbers |
| Ratio | ~10:1 | ~20:1 | ~20:1 |
| Shape | One file, often skippable | One file | Hub + chapter notes |
| State | `processed` | `processed` | `reading` → `processed`/`abandoned` |
| Watch for | Link rot in code | Garbled code, lost visuals | Never finishing |
