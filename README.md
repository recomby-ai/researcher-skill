# Researcher

A single standalone research skill for Claude Code / Codex.

One installable skill, three reference packs, composable by purpose.

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

One core engine + three domain packs loaded on demand:

```text
researcher/
├── SKILL.md                          ← core research engine
└── references/
    ├── business.md                   ← industry + company + career
    ├── academic.md                   ← papers + benchmarks + technical lineage
    └── claim-verification.md         ← cross-domain fact checking
```

**SKILL.md** contains the full research methodology: the six-phase cycle, source
class taxonomy, frontier management, saturation rules, challenge discipline,
tool usage, budget limits, and output templates.

**Reference packs** contain domain-specific tactics: where to search, what
queries to use, what to extract, domain-specific challenge paths, and output
templates tuned for that research type.

The agent loads SKILL.md for every task, then loads 1-2 reference packs based
on what the research is about.

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

### 4. Visible reasoning

The skill writes `research-{topic}.md` and updates it throughout the run, so
the research path is visible and auditable.

## Installation

Clone:

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
```

Install to Claude Code:

```bash
cp -R researcher-skill/researcher ~/.claude/skills/
```

Install to Codex:

```bash
cp -R researcher-skill/researcher ~/.codex/skills/
```

## Web Upload

Zip the `researcher/` folder and upload. It is self-contained.

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
