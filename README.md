# Stop Slop

A skill for removing AI tells from prose.

<img width="3840" height="2160" alt="G-Yg4RVbIAAhVxW" src="https://github.com/user-attachments/assets/902afc15-1f40-4a9d-af24-8cd67afb8ebf" />

## What this is

AI writing has patterns. Predictable phrases, structures, rhythms. This skill teaches Claude (or any LLM) to catch and remove them.

This fork extends [Hardik Pandya's original](https://github.com/hardikpandya/stop-slop) with two layers the phrase and structure checks miss: a voice layer (prose can pass every phrase check and still read as machine writing) and an editorial layer for attribution and framing.

## Skill Structure

```
stop-slop/
├── SKILL.md              # Core instructions (18 rules + quick checks)
├── references/
│   ├── phrases.md        # Phrases to remove
│   ├── structures.md     # Structural patterns to avoid
│   ├── voice.md          # Cadence, author presence, literalness (fork)
│   └── examples.md       # Before/after transformations
├── CHANGELOG.md
├── README.md
└── LICENSE
```

## Quick start

**Claude Code:** `git clone https://github.com/MarshallK2022/stop-slop.git ~/.claude/skills/stop-slop`

**Claude Projects:** Upload `SKILL.md` and reference files to project knowledge.  The easiest way to do it is by selecting the green Code button above, opening the chevron in it, selecting zip file, downloading that, then opening and putting both skill.md and the contents of the reference files folder into a new Claude.ai Project you set up for writing.

**Custom instructions:** Copy core rules from `SKILL.md`.

**API calls:** Include `SKILL.md` in your system prompt. Reference files load on demand.

## What it catches

**Banned phrases** - Throat-clearing openers, emphasis crutches, business jargon, all adverbs, vague declaratives, meta-commentary. See `references/phrases.md`.

**Structural clichés** - Binary contrasts, negative listings, dramatic fragmentation, rhetorical setups, false agency, narrator-from-a-distance voice, passive voice. See `references/structures.md`.

**Sentence-level rules** - No Wh- sentence starters, no em dashes, no staccato fragmentation, no lazy extremes, active voice required.

**Machine cadence** (fork) - Verbless fragment stacks, aphoristic closers, uniform declaratives, symmetric scaffolding, every paragraph landing a mini-conclusion. See `references/voice.md`.

**Missing author** (fork) - First person where the form allows it, judgment and priority on the page, honest hedging. An authored piece with no author in it is an AI tell.

**Audience and literalness** (fork) - Every term of art defined at first use, no insider asides, mechanism-hiding metaphors replaced with what concretely happens.

**Attribution and framing** (fork) - Company claims hedged with attributive phrasing ("says it is") or credited as "Author Name (Publication)", quote attribution varied instead of repeating the company name, no redundant framing verbs, unfamiliar companies introduced with a descriptor, contrasts joined with an explicit conjunction, sections opened with a plain sentence framing the tension.

**The override rule** (fork) - The rules serve the prose. If a rule-driven rewrite reads worse than the original, keep the original.

## Scoring

Rate 1-10 on each dimension:

| Dimension | Question |
|-----------|----------|
| Directness | Statements or announcements? |
| Rhythm | Varied or metronomic? |
| Trust | Respects reader intelligence? |
| Authenticity | Sounds human? |
| Density | Anything cuttable? |
| Presence | Is there an author in the prose? |
| Clarity | Could an outsider to this field follow every sentence? |

Below 49/70: revise.

## Authors

Original skill by [Hardik Pandya](https://hvpandya.com).

Fork additions (voice, audience, literalness, attribution, and framing layers) by [Marshall Kirkpatrick](https://github.com/MarshallK2022).

## License

MIT. Use freely, share widely.
