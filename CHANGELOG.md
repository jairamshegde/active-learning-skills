# Changelog

All notable changes to these skills are documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html). Because these skills encode opinions rather than an API, versions mean: **major** for a change in how a skill behaves by default, **minor** for new capability, **patch** for wording and fixes.

## [Unreleased]

## [0.1.0] - 2026-10-04

Initial release. Three skills, split so that formatting rules and thinking method can change independently.

### Added

- **`obsidian-notes`** — Obsidian-flavoured Markdown. Properties, wikilinks and embeds, the 13 built-in callout types, tables, Mermaid, math, escaping. Body conventions default to no H1, sentence-case headings, and relationships kept in the body rather than in properties.
- **`source-notes`** — processing a consumed source into a note. Compression targets of ~10:1 for blogs and ~20:1 for lectures and book chapters, per-source procedures for blogs, video transcripts and books, rules for sources containing code, and Draft/Check/Drill modes with Check as the default.
- **`active-recall`** — retrieval drills. 80% applied questions to 20% recall anchors, eight thinking-question types, free recall only with no multiple choice, questions never asked in source order, and five marking verdicts including right-for-the-wrong-reason.
- `README.md` with install instructions for Claude Code, claude.ai and the API, plus a table of which files to edit to change defaults.

### Notes

- The run log, judgements about a source, and open questions are never generated — they are left as placeholders. This is a deliberate constraint, not a limitation.
- Skills do not sync across surfaces. Uploading to claude.ai does not make a skill available in Claude Code or the API.

[Unreleased]: https://github.com/jairamshegde/active-learning-skills/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/jairamshegde/active-learning-skills/releases/tag/v0.1.0