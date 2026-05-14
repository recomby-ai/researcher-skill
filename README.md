# Researcher

A single standalone research skill for Claude Code / Codex.

One self-contained skill file built around a single research spine.

```text
VERTICAL history + HORIZONTAL comparison -> CROSS-AXIS judgment
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
└── skills.md                         ← horizontal-vertical research method
```

**skills.md** contains the full method: preparation, information collection,
vertical history, horizontal comparison, cross-axis insight, object-type
adaptation, evidence and citation rules, output structure, writing standards,
and a final quality checklist.

The skill body is written in Chinese for readability. The YAML metadata keeps
English trigger terms so English research prompts can still route to it.

## Core Design

### 1. One Core Method

The skill is not a pile of research tactics. Every investigation follows one
structure:

- Vertical axis: how the object became what it is.
- Horizontal axis: where it stands now among peers, substitutes, users, and
  incentives.
- Cross-axis judgment: what the combination reveals.

### 2. Evidence Supports the Axes

Evidence work is organized around the two axes instead of accumulated for its
own sake. The skill still distinguishes official, behavioral, operator, lived
experience, adversarial, market proxy, and artifact sources.

### 3. Challenge Before Judgment

Every strong thesis must be attacked before synthesis: criticism, failed cases,
methodology issues, adversarial sources, incentives, and behavioral evidence
all matter.

### 4. Adaptive Output

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
Use $researcher to do a horizontal-vertical analysis of this product.
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
