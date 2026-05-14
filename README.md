# Researcher

A single standalone research skill for Claude Code / Codex.

One self-contained skill file, with all research modes and tactics consolidated.

```text
FRAME → MAP → FRONTIER → DEEPEN → CHALLENGE → SYNTHESIZE
```

English | [中文](README.zh-CN.md)

## What This Skill Does

`researcher` is for research tasks that are:

- open-ended
- multi-source
- judgment-heavy
- vulnerable to hype, weak summaries, or one-sided narratives

It is designed for work like:

- mapping a new industry or field
- investigating a company or product
- validating a claim or narrative
- comparing paths and making decisions
- finding real opportunities vs loud narratives
- understanding practitioner reality and hidden friction
- reviewing academic literature and state of the art

## Architecture

One consolidated research skill:

```text
researcher/
└── skills.md                         ← full research engine + playbooks
```

**skills.md** contains the full research methodology: the six-phase cycle,
quick/standard/deep modes, source-class taxonomy, citation and metadata rules,
local-material handling, object-type playbooks, optional horizontal/vertical
lenses, evidence ledger, challenge discipline, synthesis rules, and output
templates.

## Core Design

### 1. Evidence-first, not webpage-first

The skill treats the internet as a mixed evidence environment:

- official — what institutions say
- behavioral — what they actually do
- operator — what experienced people say
- lived experience — what practitioners report in forums and social
- adversarial — short reports, critics, lawsuits, complaints
- market proxy — hiring, pricing, adoption, fundraising signals
- artifact — papers, repos, docs, datasets, filings

### 2. Broad first pass, then controlled depth

The first round is not "search until you can summarize." It is:

- a controlled breadth-first map (4-6 searches)
- followed by a frontier of 2-4 active leads
- followed by lead-driven deepening

### 3. Mandatory challenge paths

Every strong thesis must run a challenge path before synthesis. The skill
requires checking opposing incentives, adversarial sources, and behavioral
evidence before concluding.

### 4. Adaptive output

The skill defaults to a concise chat answer. It creates a durable research
artifact only when the user asks for one, provides an output path, or the work
is too large to remain useful inline.

## Installation

Clone:

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
```

Install to Claude Code:

```bash
mkdir -p ~/.claude/skills/researcher
cp researcher-skill/researcher/skills.md ~/.claude/skills/researcher/SKILL.md
```

Install to Codex:

```bash
mkdir -p ~/.codex/skills/researcher
cp researcher-skill/researcher/skills.md ~/.codex/skills/researcher/SKILL.md
```

## Web Upload

If your runtime requires the entry file to be named `SKILL.md`, rename
`researcher/skills.md` to `SKILL.md` before uploading. The file is otherwise
self-contained.

## Example Prompts

```text
Use $researcher to map the AI agent engineering job market.
Use $researcher to verify whether this industry claim is actually true.
Use $researcher to compare quant, AI infrastructure, and applied ML for a math undergraduate.
Use $researcher to find the strongest opportunities in vertical AI.
Use $researcher to stress-test this startup before I take the offer.
Use $researcher to find what practitioners really complain about in production agent systems.
Use $researcher to review the literature on retrieval-augmented generation.
Use $researcher to do due diligence on this company's Series B narrative.
```

## Limitations

- Still limited by the public web and available search/fetch tools
- Some sources remain behind logins or paywalls
- Social and community sources are signals, not automatic truth
- This skill improves research behavior; it does not replace domain expertise

## License

MIT
