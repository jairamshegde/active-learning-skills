# Sources containing code

Blogs, lectures, and books all come with code. The rule is the same across them: keep very little of the source's code, and all of the user's own run log.

## Three buckets

**Code only read.** Most of it. Link to the repo, gist, notebook, or timestamp and describe in a sentence what it does. Pasting twenty lines nobody executed is the code equivalent of pasting a transcript — it feels like capture and teaches nothing.

**Code that is the idea.** Sometimes prose can't carry it: an API shape, a prompt structure, the one config flag that changes behaviour. Keep the smallest version that encodes the decision, usually three to eight lines, stripped well below what the source wrote.

**Code the user ran.** Full log. This is the only bucket where the note beats the original, because what broke on their data exists nowhere else.

The test for the middle bucket: **if this block were deleted, would the paragraph above it still be actionable?** If yes, delete it. If the paragraph becomes meaningless, keep it.

## The run log

Where the value is. Record the artifact's location, what was changed, what broke, and numbers wherever possible.

````md
## What I ran

Notebook: `chapter08/semantic_search.ipynb`, against our own 4k-doc corpus
instead of their dataset.

> [!bug] Their chunking broke on our docs
> Fixed-size splitting cut mid-table in the API reference pages, so retrieval
> returned half a parameter list with no header. Switched to splitting on
> markdown headings — recall@5 went from roughly 0.6 to 0.85 by eyeball.
> The chapter doesn't warn you about this.

> [!warning] Cost
> Reranking is 3x the calls for maybe 20% better output. Worth it for the
> weekly job, not per-request.
````

"Reranking helped" is a feeling. "180ms added, visibly better top-3" is something the user can act on in six months. Push for numbers.

**Never generate this section.** It is the user's experience. Leave the heading with a stub and say so in the reply.

## Per-source traps

**Transcripts garble code.** Auto-captions turn method calls into prose and lose indentation entirely. Never reconstruct code from a transcript — take it from the repo or gist in the description. If there is none, an embedded screenshot is more honest than a retyped guess the user will later trust.

**Blog code rots.** A post from two years ago will have an import path or parameter name that no longer exists. The modifications needed to get it running today are the most valuable thing the user will write about that post, and they are nowhere on the internet.

**Book code is notebook-shaped.** Clean, happy-path, small data. Expect it to break on a real corpus, and expect that breakage to be the actual lesson.

## Where executable code lives

Not in the vault. Notebooks and scripts belong in a repo or scratch directory; the note links to them by path or URL. The vault holds conclusions, the repo holds things that run — mixing them means notes get versioned by git and code gets synced by Obsidian, and neither tool does the other's job well.

If a long block should stay retrievable anyway, collapse it so it doesn't dominate the note:

`````md
> [!example]- Full pipeline as I ended up running it
> ```python
> ...
> ```
`````
