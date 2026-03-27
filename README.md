# Researcher — Frontier-Driven ReAct Research Skill

Claude is already good at reasoning. The problem is that normal web research
often stops after one broad pass or turns into repeated query paraphrases.

This skill changes the search policy:

1. **Breadth-first field mapping first** — The first pass maps the field using
   the latest available overview sources, recent representative work,
   foundational sources, benchmarks, and counter-evidence.
2. **Multi-branch frontier after that** — Instead of locking onto one lead too
   early, Claude keeps several active branches and chooses which ones to deepen
   based on information gain and source value.
3. **ReAct deepening on each branch** — Every later round is driven by what the
   previous round uncovered: find leads, decide the next hop, chase primary
   sources, and stop only when the graph saturates.

Together, this makes research behave more like an investigator following a
graph of evidence than a search engine aggregating webpages.

Implementation note: the core workflow lives in
`researcher/SKILL.md`, while detailed heuristics for frontier scoring, source
hierarchy, and saturation live in
`researcher/references/research-heuristics.md`.

## What This Looks Like

```
Round 1: Map "LLM hallucination mitigation"
  → latest survey / benchmark / recent papers / foundational papers
  → branches found:
    A. retrieval-based methods
    B. decoding-time methods
    C. internal steering / representation methods
    D. criticism / limitations / benchmark validity

Round 2: Deepen A + C + D
  → A leads to benchmark papers and dataset details
  → C leads to a recent Science paper and its cited prior work
  → D leads to replication and evaluation-limit papers

Round 3: Jump to primary sources
  → read original papers, appendix, cited baselines, and forward citations
  → drop weak branches, keep high-yield ones active

Round 4+: Continue until saturation
  → no major new methods, evidence layers, or debates appear
  → key claims tied to primary or highest-value available sources
```

## Scientific Research Behavior

For scientific and technical queries, the skill is designed to preserve strong
research quality:

- It looks for the **latest available** overview source, not a hard-coded
  one-year window.
- If no formal review exists, it falls back to the best overview substitute:
  tutorial, benchmark paper, perspective, standards document, or seminal paper
  cluster.
- It keeps both ends of the field in view:
  newest representative work and foundational sources.
- It actively searches for criticism, limitations, replication, and competing
  approaches.

## Install

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
cp -r researcher-skill/researcher ~/.claude/skills/
```

Then use `/researcher your question` in Claude Code.

## Usage

```text
/researcher What are the current solutions to LLM hallucination?
/researcher CRISPR off-target detection methods — state of the art
/researcher Is solid-state battery mass production realistic by 2026?
```

## Core Rules

- Do not answer after one search round.
- Do not hard-code narrow time windows unless the user asks for one.
- Do not rely on overview sources alone for important claims.
- Do not collapse to one branch too early.
- Do not stop because a round count was reached; stop when the research graph
  saturates.

## Limitations

- Cannot access Google Scholar via WebSearch
- Cannot always fetch paywalled full text
- Depends on web-visible sources and what the search/fetch tools can reach

## License

MIT
