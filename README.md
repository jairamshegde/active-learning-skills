# Active Learning Skills

Three Claude Agent Skills for turning things you read and watch into notes you actually retain — in Obsidian-flavoured Markdown.

They are deliberately separate. Formatting rules change when you switch tools; the way you process a source doesn't. Keeping them apart means you can swap one without rewriting the others.

| Skill | Answers | Changes when |
|---|---|---|
| **`obsidian-notes`** | How do I write this so it renders and links correctly? | Obsidian's syntax changes |
| **`source-notes`** | What belongs in this note, and what do I throw away? | Your method changes |
| **`active-recall`** | Do I actually know this? | Rarely |

## The idea

An LLM has complete coverage of a source and zero context about you. You have deep context and a decaying memory of what you just consumed. Neither can do the other's half.

So the model does the drudgery — cleaning transcripts, merging twenty chapters into six headings, recovering code from repos, flagging unsupported claims — and you keep the two things that produce learning: deciding what matters, and retrieving it from your own head.

The one place this goes beyond saving time is quizzing. You can't quiz yourself on what you forgot, because the gap is invisible from the inside, and you'll never catch yourself remembering something confidently and wrongly. Something holding the source can do both.

## Repository layout

```
.
├── README.md
├── obsidian-notes/
│   ├── SKILL.md              # properties, body conventions, failure modes
│   └── references/
│       ├── syntax.md         # links, embeds, tables, Mermaid, math, escaping
│       └── callouts.md       # 13 built-in types, when to use which
├── source-notes/
│   ├── SKILL.md              # the method, compression targets, anatomy
│   └── references/
│       ├── by-source.md      # blog / transcript / book procedures
│       ├── modes.md          # Draft, Check, Drill — and how to pick
│       └── code.md           # sources containing code
└── active-recall/
    ├── SKILL.md              # session protocol, the 80/20 mix
    └── references/
        ├── question-design.md # 8 question types, anti-patterns
        └── grading.md         # verdicts, probing, session close
```

## Install

**Claude Code** — copy the folders in; no upload step.

```bash
git clone https://github.com/<you>/obsidian-learning-skills.git
cp -r obsidian-learning-skills/{obsidian-notes,source-notes,active-recall} ~/.claude/skills/
```

Use `.claude/skills/` inside a repo instead if you want them scoped to one project.

**claude.ai / Claude Desktop** — zip each skill folder and upload it in Settings, under the Skills section. The ZIP must contain the folder itself at the root, not just `SKILL.md`. Requires a paid plan with code execution enabled.

```bash
for s in obsidian-notes source-notes active-recall; do zip -r "$s.zip" "$s"; done
```

The exact menu path has moved between releases (Features / Capabilities / Customize), so follow the current [official instructions](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview). Surfaces don't sync — a skill uploaded to claude.ai isn't available in Claude Code or the API.

**API** — upload via the `/v1/skills` endpoints and reference the returned `skill_id` with the code execution tool.

## Using them

You don't invoke skills by name. Describe what you want and the right ones load.

### Taking notes on something

```
Here's the transcript of [talk]. I'm building a RAG pipeline for internal docs.
Take notes on this.
```

Stating what you're building is not optional flavour — it's what separates useful questions and useful emphasis from a vocabulary test.

Three modes decide how much of the note you write:

| Mode | Who writes | Use for | Triggered by |
|---|---|---|---|
| **Draft** | Claude, over-inclusive; you cut it down | Reference material you need recorded, not learned | Source alone |
| **Check** | You, from memory; Claude diffs it against the source | Default. Best effort-to-retention ratio | Source + your notes |
| **Drill** | Claude quizzes you; your answers become the note | Material you'll use next week | "quiz me" |

A Check returns three lists in severity order — **Wrong** (statements your note makes that the source doesn't support), **Thin** (a label where the source made an argument), **Missed** (capped at five or six, ordered by what's load-bearing). It reports; it won't rewrite your note, because that would take the work off you.

### Getting drilled

```
Quiz me on that lecture. I'm implementing retrieval next sprint.
```

What happens: one question at a time, free recall only, never in source order, 8–12 questions. 80% require you to apply, discriminate, predict or criticise; 20% are plain recall anchors. Thin answers get one follow-up probe, never two. Sessions close with your gaps, your broken mechanisms, and what to re-read.

The verdict to watch for is **right, wrong reason** — correct conclusion, broken mechanism. It feels like knowledge and you'll carry it into the next problem.

### Writing a note by hand

`obsidian-notes` loads on its own whenever a note is being written, so properties, callouts, wikilinks and tables come out correct without being asked for.

## What stays yours

The skills will not generate, and will leave as explicit placeholders:

- **The run log** — what you executed, what broke, what you changed. On a hands-on source this is the only section that beats the original.
- **Judgements** about whether the source was any good.
- **Open questions** arising from your context.

A note where the model invented "what I ran" is worse than no note, because it reads as experience you never had.

## Compression targets

| Source | Raw | Note | Ratio |
|---|---|---|---|
| Blog post | ~2,000 words | 100–200 words | ~10:1 |
| 1-hour lecture | ~9,000 words | 300–600 words | ~20:1 |
| Book chapter | ~8,000 words | 200–400 words | ~20:1 |

Two tests for whether compression happened: could someone rebuild the source from your note (bad), and could you explain it to a colleague without opening the note (good).

## Making them yours

These encode specific opinions. The most likely things to change:

| Want to change | Edit |
|---|---|
| Property names, tag taxonomy | `obsidian-notes/SKILL.md` → Properties |
| Wikilinks → Markdown links, or H1 at top | `obsidian-notes/SKILL.md` → Body structure |
| Compression ratios | `source-notes/SKILL.md` → Compression targets |
| Add a source type (papers, podcasts, courses) | `source-notes/references/by-source.md` |
| The 80/20 question mix | `active-recall/SKILL.md` → The mix |
| Question types | `active-recall/references/question-design.md` |

Defaults worth knowing before you change them: no H1 (the filename is the title), wikilinks over Markdown links, and relationships live in the body rather than in properties, where a link has no surrounding sentence to explain it.

## Design notes

- **Progressive disclosure.** Each `SKILL.md` stays short because it's always in context; detail lives in `references/` and loads only when relevant.
- **No multiple choice in drills.** Recognition is a weaker operation than retrieval, and it's exactly the instinctive answering the drill exists to defeat.
- **Questions never follow source order.** Otherwise you ride the source's narrative instead of retrieving.
- **Blunt marking.** Praise inflation destroys the only signal a drill produces.

## License

MIT.