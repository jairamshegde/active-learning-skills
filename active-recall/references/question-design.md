# Question design

## Contents

- [The 20% — anchor questions](#the-20--anchor-questions)
- [The 80% — thinking questions](#the-80--thinking-questions)
- [Anti-patterns](#anti-patterns)
- [Calibrating to purpose](#calibrating-to-purpose)

Examples below use three sources seen across these skills: Anthropic's *Building effective agents*, Karpathy's *Intro to LLMs* talk, and *Hands-On Large Language Models*.

## The 20% — anchor questions

Plain recall. Their job is to establish that the raw material landed before testing whether it can be used, and to give the user an early win that isn't hollow.

Two or three per session. Place one near the start and scatter the rest; three in a row turns the session into a vocabulary test.

Worth asking when the fact is load-bearing — a term that will be reused, a distinction everything else rests on, a number that drives a decision:

- "What two things is an LLM, in the two-files framing?"
- "Bi-encoder and cross-encoder — which goes where in the retrieval pipeline?"

Not worth asking: author names, publication dates, how many patterns were listed, anything retrievable by opening the source for five seconds.

## The 80% — thinking questions

Eight types. Mix them; running the same type repeatedly becomes predictable and the user starts answering to the form rather than the content.

### 1. Transfer — apply it to their own work

The strongest type, and only possible with stated purpose.

- Weak: "What is the evaluator-optimizer pattern?"
- Strong: "Your changelog generator retries on failure. Which pattern is that closest to, and what would evaluator-optimizer actually add?"

### 2. Discrimination — separate two things that look alike

Tests whether the boundary is understood or just the vocabulary.

- Weak: "What's the difference between workflows and agents?"
- Strong: "A router picks between three prompt chains at runtime. Workflow or agent? Defend the line you're drawing."

### 3. Failure mode — when does it break

Sources describe things working. Knowing where they fail is the mark of actually holding the idea.

- "Dense retrieval returns something confidently wrong where keyword search would return nothing. Why does that asymmetry exist?"
- "When would prompt chaining be the wrong choice despite the task being obviously sequential?"

### 4. Causal — why does it hold

Pushes past the what into the mechanism. Pairs well with a probe.

- Weak: "What are scaling laws?"
- Strong: "Why does predictable loss scaling let a lab commit to a training run before knowing what the model will be good at?"

### 5. Counterfactual — change one variable

Cannot be answered by recall at all. The user has to hold the model and run it.

- "If chunk size doubled, which part of the retrieval pipeline degrades first, and why that one?"
- "If prompt injection were solved tomorrow, which of the three security problems in the talk would still remain?"

### 6. Critique — where is the source weak

Trains reading against the grain rather than absorbing.

- "Which claim in that post is asserted without evidence?"
- "He spends five minutes on jailbreaks and ninety seconds on data poisoning. Is that the right ratio? Argue the other side."

### 7. Construction — design something with it

Highest difficulty. Best saved for material the user is about to use.

- "Design the smallest agentic system for triaging your support inbox. Which pattern, and what would make you upgrade it?"
- "You have 4k documents and a latency budget of 300ms. What retrieval architecture, and what did you trade away?"

### 8. Connection — span two sections, or two sources

Recent memory of a single section cannot answer these, which is precisely the point.

- "The two-files framing from the opening and the LLM OS analogy at the end — do they agree? Where do they pull apart?"
- "How does that chunking argument sit against what you wrote in [[Chunking is the highest-leverage choice in retrieval]]?"

The second form requires access to the user's existing notes. When available it is the most valuable question type in the set, because it surfaces contradictions the user cannot see — nobody remembers every note they've written.

## Anti-patterns

Each of these can look like a real question while still being answerable without understanding.

- **Phrase-matching.** If the answer is a string from the source, it tests search, not retrieval. The tell: you could answer it with ctrl-F.
- **Giveaway stems.** "Why does reranking with a cross-encoder improve precision?" contains its own answer. Ask "why rerank at all, given the cost?"
- **Yes/no and binary.** A coin flip gets it half right. If a binary is genuinely the question, always attach "and why" — the reasoning is the answer being marked.
- **Compound questions.** Two questions in one stem lets the user answer the easy half and ignore the other. Split them.
- **Leading questions.** "Don't you think the framework advice is overstated?" produces agreement, not thought.
- **"Explain X."** An invitation to recite. Convert into a situation: "when would X be the wrong call?"
- **Answerable without the source.** If general knowledge covers it, it tests nothing about this material.
- **Trivia.** Names, dates, counts, and figures, unless the number is carrying an argument.

## Calibrating to purpose

The same source generates different question sets depending on why the user consumed it.

| Purpose | Weight toward | Example |
|---|---|---|
| Building something next week | Transfer, construction, failure mode | "What breaks first when you put this on your corpus?" |
| General understanding | Causal, discrimination, connection | "Why does that mechanism produce that behaviour?" |
| Interview or exam prep | Anchor ratio rises, add discrimination | "Define it, then distinguish it from the neighbouring concept" |
| Evaluating a technology choice | Critique, counterfactual | "What would have to be true for this to be the wrong pick?" |

When the user hasn't given a purpose, ask once. The alternative is a session of competent, well-formed, useless questions.
