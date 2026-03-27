# Researcher

Frontier-driven ReAct research skill for Claude Code.

This skill is built for one job: turn web research from "search once, summarize
snippets" into "map the field, follow leads, and keep digging until the answer
is anchored in primary sources or the evidence graph saturates."

English | [中文](README.zh-CN.md)

## Quick Nav

- [What This Skill Does](#what-this-skill-does)
- [Search Strategy](#search-strategy)
- [Why This Is Different](#why-this-is-different)
- [Scientific Research Behavior](#scientific-research-behavior)
- [Repository Structure](#repository-structure)
- [Installation](#installation)
- [Usage Examples](#usage-examples)
- [Core Rules](#core-rules)
- [Limitations](#limitations)

## At a Glance

| | Ordinary "deep search" | This skill |
|---|---|---|
| First round | Search and summarize | Breadth-first field mapping |
| Search structure | Many pages, weak structure | Explicit evidence graph |
| Lead selection | Query reformulation | Frontier-driven branch selection |
| Search depth | Often broad but shallow | Multi-branch ReAct deepening |
| Recency logic | Often fixed windows | Latest available source in-field |
| Stop rule | Round count or token limit | Saturation of the research graph |
| Research style | Aggregator | Investigator |

## What This Skill Does

Most so-called "deep search" systems are still broad aggregators. They search a
lot, fetch a lot of pages, and compress them into a summary. That is useful,
but it is not how a good investigator works.

This skill changes the search policy in three ways:

1. `Breadth-first mapping first`
   The first round does not try to answer immediately. It maps the field:
   overview sources, representative recent work, foundational sources,
   benchmarks, and criticism.
2. `Multi-branch frontier after that`
   Instead of collapsing onto one lead too early, it keeps several active
   branches and chooses which ones to deepen next.
3. `ReAct deepening on each branch`
   Every later round is driven by what the last round discovered:
   `SEARCH / FETCH -> REASON -> NEXT JUMP`.

The result is closer to an investigator following an evidence graph than a
search engine aggregating webpages.

## Search Strategy

The core cycle in the skill is:

```text
MAP -> BUILD FRONTIER -> DEEPEN -> REFLECT -> repeat
```

### Phase 1: Map the field

The first pass is explicitly breadth-first. Its job is to build a field map, not
to answer.

The skill tries to cover:
- the latest available overview source
- recent representative work
- foundational or defining sources
- benchmarks, datasets, standards, or evaluation layers
- criticism, limitations, replications, or competing schools

Important detail: it does **not** hard-code a one-year window. It looks for the
latest *available* overview source for that field. In a slow-moving field that
may be older; in a fast-moving field it may be very recent.

### Phase 2: Build a frontier

After mapping, the skill creates a frontier of candidate leads rather than
choosing one thread immediately.

Typical branch types include:
- method branch
- evidence branch
- benchmark branch
- researcher or lab branch
- criticism branch
- primary-document branch

This is the core difference from single-thread citation chasing: the skill keeps
enough diversity to avoid tunnel vision.

### Phase 3: Deepen via ReAct

For each active branch, the skill runs:

```text
SEARCH / FETCH -> REASON -> NEXT JUMP
```

After each step it records:
- `[Finding]` what was confirmed or falsified
- `[Lead]` what new source or clue appeared
- `[Gap]` what still lacks a primary source
- `[Next Jump]` why the next hop is worth taking

That means later searches are not generic reformulations of the original query.
They are graph-driven jumps based on newly discovered structure.

### Phase 4: Stop on saturation

The skill does not stop because it reached a fixed number of rounds.

It stops when the research graph is close to saturated:
- the main branches are understood
- key claims are tied to primary or highest-value sources
- new searches mostly return known nodes or low-value repetition
- remaining branches are low-yield or redundant

## Why This Is Different

The skill is designed to avoid three common failure modes in "deep research"
agents:

1. `Broad but shallow`
   Fetching many pages without following the most important leads.
2. `Narrow too early`
   Picking one promising thread and missing the rest of the field.
3. `Fake recency rules`
   Hard-coding "last year" or "recent" in ways that break for slower fields.

Instead, this skill combines:
- breadth-first field mapping
- multi-branch frontier management
- ReAct-style lead chasing
- domain-aware source hierarchy
- saturation-based stopping

## Scientific Research Behavior

For scientific and technical queries, the skill is intentionally optimized to
stay useful for literature review and research synthesis.

It tries to preserve both ends of the field:
- the newest edge
- the deepest roots

It prefers:
- the latest available review, survey, tutorial, benchmark, or perspective
- recent representative papers
- foundational papers
- benchmarks and evaluation protocols
- criticism, limitation, and replication work

It also allows the notion of "primary source" to change by domain:
- scientific research: original paper, appendix, code, dataset, benchmark docs
- industry: filings, earnings reports, patents, standards, official docs
- medicine: systematic reviews, RCTs, guidelines, registries, regulator sources

## Repository Structure

```text
researcher-skill/
├── README.md
├── README.zh-CN.md
└── researcher/
    ├── SKILL.md
    └── references/
        ├── frontier-management.md
        ├── scientific-literature.md
        ├── source-hierarchy.md
        ├── saturation-and-counterevidence.md
        └── query-shaping.md
```

- `researcher/SKILL.md`
  The core workflow and hard constraints.
- `researcher/references/frontier-management.md`
  Frontier scoring, branch types, breadth floors, and pruning rules.
- `researcher/references/scientific-literature.md`
  Literature traversal, overview-source selection, and graph-jump patterns.
- `researcher/references/source-hierarchy.md`
  What counts as a primary or highest-value source in each domain.
- `researcher/references/saturation-and-counterevidence.md`
  Challenge-path rules and saturation criteria.
- `researcher/references/query-shaping.md`
  Query templates for map-phase and deepen-phase search.

The split is intentional: the core prompt stays lean, and detailed rules are
broken up by decision type so they can be loaded only when needed.

## Example

```text
Round 1: Map "LLM hallucination mitigation"
  -> review / benchmark / recent papers / foundational papers / criticism
  -> branches found:
     A. retrieval-based methods
     B. decoding-time methods
     C. internal steering methods
     D. benchmark validity / limitations

Round 2: Deepen A + C + D
  -> A leads to benchmark papers and dataset details
  -> C leads to recent representation-steering work
  -> D leads to replication and evaluation-limit papers

Round 3+: Jump to primary sources
  -> follow citations backward, forward, sideways, and downward
  -> read original papers, appendices, code, and benchmark docs
  -> prune weak branches, keep high-yield ones alive

Stop:
  -> no major new method classes, evidence layers, or debates appear
```

## Installation

Clone the repository:

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
```

Install the skill into Claude Code:

```bash
cp -r researcher-skill/researcher ~/.claude/skills/
```

Then use:

```text
/researcher your question
```

## Usage Examples

```text
/researcher What are the current solutions to LLM hallucination?
/researcher CRISPR off-target detection methods — state of the art
/researcher Is solid-state battery mass production realistic by 2026?
/researcher Verify whether this industry claim traces back to a primary source
```

## Core Rules

- Do not answer after one search round.
- Do not rely on overview sources alone for important claims.
- Do not hard-code narrow time windows unless the user asks for one.
- Do not collapse to one branch too early.
- Do not widen again with generic search unless the field map has a real blind
  spot.
- Search for counter-evidence, not just supporting evidence.
- Stop on saturation, not round count.

## Limitations

- It cannot access Google Scholar through the normal web search tool.
- It cannot always fetch paywalled full text.
- It still depends on what the search and fetch tools can reach on the open web.
- It is not a formal systematic review engine.

## License

MIT
