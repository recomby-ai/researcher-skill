---
name: researcher
description: >
  Horizontal-Vertical Research skill for systematic investigation of a product,
  company, market, concept, technology, person, career path, academic topic, or
  factual claim. Use when the user asks to research, investigate, analyze,
  compare, verify, fact check, do due diligence, map a field, review literature,
  understand the real story, or judge whether something is worth believing or
  pursuing. Also trigger on 研究, 调研, 分析, 深挖, 横纵分析, 竞品分析,
  尽职调查, 核实, 验证, 这个靠谱吗, 真实情况是什么, 有没有前景,
  值不值得, 到底怎么样, 是真的吗.
argument-hint: <research object or question / 研究对象或问题>
allowed-tools:
  - WebSearch
  - WebFetch
  - Read
  - Write
---

# Horizontal-Vertical Research

This skill has one core method:

```text
VERTICAL history + HORIZONTAL comparison -> CROSS-AXIS judgment
```

The vertical axis explains how the object became what it is. The horizontal
axis explains where it stands now among peers, substitutes, users, incentives,
and evidence classes. The cross-axis section is the point of the work: explain
how history shaped the current position, what is real vs overstated, and what
is likely to happen next.

Do not turn research into source hoarding. Every search, note, and source must
serve one of the two axes or the final judgment.

## 0. Preparation

Before searching, identify:

1. Research object: product, company, concept, technology, person, market,
   career path, academic topic, or claim.
2. User intent: understand, compare, decide, verify, invest, join, buy, build,
   or write a report.
3. Scope: geography, timeframe, audience, depth, exclusions, and output form.
4. Known focus: what the user cares about most.
5. Evidence that would change the answer.

If the object and intent are already clear, do not ask. Start.

User-provided files, links, notes, transcripts, or datasets are primary context.
Read them before broad web search when they define the task. Distinguish facts
from provided material, facts externally corroborated, and facts contradicted by
external evidence.

Default output is a chat answer. Create a durable Markdown artifact only when
the user asks for one, gives an output path, or the research is too large to be
useful inline.

## 1. Information Collection

Collect information in three lanes. Keep them separate until synthesis.

### Lane A: Vertical Information

Find the object's origin and development:

- Who created or first proposed it?
- What problem, theory, market gap, or personal background produced it?
- What was the first public version, founding moment, or canonical statement?
- What major versions, funding events, papers, releases, controversies,
  personnel changes, pivots, or regulatory shifts changed its path?
- Which early decisions locked in later constraints?

### Lane B: Horizontal Information

Find the current comparison set:

- Direct competitors or peers.
- Indirect substitutes and older ways of solving the same problem.
- Adjacent concepts, methods, companies, roles, or communities.
- User/operator sentiment and actual usage patterns.
- Market, hiring, pricing, adoption, benchmark, or deployment signals.

### Lane C: Challenge Information

Actively seek what could weaken the emerging story:

- Criticism, failed cases, lawsuits, complaints, short reports, rebuttals.
- Benchmark limitations, replication failures, stale data, bad methodology.
- Incentives to exaggerate, hide problems, or attack unfairly.
- Evidence that the public narrative is marketing rather than reality.

### Source Priority

Prefer source-proximate evidence:

| Information Need | Strong Sources |
| --- | --- |
| Product changes | Official docs, changelog, release notes, GitHub commits/issues |
| Company/business facts | Filings, official announcements, investor material, pricing, hiring |
| User reality | Forums, reviews, GitHub issues, Reddit, X, LinkedIn, Blind, interviews |
| Technical or academic claims | Papers, benchmarks, datasets, repos, model/dataset cards |
| Market or career claims | Job posts, salary data, procurement, adoption, layoffs, profiles |
| Controversy or risk | Lawsuits, complaints, short reports, regulator actions, rebuttals |

One source class is not enough for an important conclusion. Try to combine:

- One official or artifact source.
- One behavioral or market source.
- One human or adversarial source.

If triangulation is impossible, state which evidence class is missing.

### Search Discipline

Use a query ladder:

1. Exact object or claim.
2. Official source and primary artifacts.
3. History, origin, founder, first release, old names.
4. Competitors, alternatives, comparisons, market maps.
5. User reviews, issues, forums, practitioner posts.
6. Criticism, limitation, lawsuit, complaint, failure, debunk.
7. Local-language and date-filtered searches when region or recency matters.

Search in English first for global topics. For region-specific topics, search
in English and the relevant local language before concluding.

### Sufficiency Check

Do not proceed to final synthesis until you can answer:

- Vertical: can the history be told as causal stages rather than a timeline?
- Horizontal: is the comparison set complete enough for the user's decision?
- Challenge: what is the strongest reason the emerging thesis may be wrong?
- Evidence: are key facts supported by reliable sources with dates?

## 2. Vertical Analysis

The vertical axis is a causal story, not a chronology dump.

Cover:

- Origin background: era, market, technical context, social context.
- Founders, authors, maintainers, or early advocates and why they mattered.
- Initial form: what it was at birth and how that differs from today.
- Key timeline: events that changed direction, not every minor update.
- Stage division: natural phases with their core feature and core tension.
- Decision logic: why A was chosen over B at important moments.
- Path dependence: what became hard to reverse because of early choices.
- Missing history: unresolved gaps or information that could not be found.

Use this structure internally:

```text
Origin -> Birth -> Key Nodes -> Phases -> Decisions -> Path Dependence
```

Good vertical writing explains why each step made the next step more likely.
Avoid "in 2022 this happened, in 2023 that happened" unless the causal link is
clear.

## 3. Horizontal Analysis

The horizontal axis is a current-time comparison. It explains what the object
is competing with, replacing, joining, or being confused with.

First decide competitor scope:

- No direct peer: explain why. Is it too new, too niche, legally protected, too
  small, or not actually a standalone category? Compare substitutes and likely
  future entrants instead.
- 1-2 peers: compare each deeply.
- 3+ peers: choose the 3-5 most representative and group the rest by segment.

Compare on dimensions that matter for the object type:

- Core method, product form, business model, technical route, or theory.
- Target user, buyer, community, geography, and use case.
- Pricing, distribution, funding, ecosystem, data, regulation, or switching
  cost.
- Strengths, weaknesses, adoption signals, user complaints, and operator view.
- Gap between official positioning and actual use.

Do not write a parameter table in prose. Explain what each peer has "become" in
practice and why users, buyers, researchers, or employers choose it.

## 4. Cross-Axis Insight

This is the most important section. It must not summarize the vertical and
horizontal sections. It must combine them.

Answer:

1. Which historical decisions created today's position?
2. Which current strengths have historical roots?
3. Which current weaknesses are old decisions becoming liabilities?
4. How did competitors' different histories produce different positions?
5. What public narrative is contradicted by user behavior or artifacts?
6. Which risks are structural, and which are temporary?
7. What evidence would change the judgment?

For future judgment, produce 2-4 scenarios only when useful:

- Most likely scenario.
- Most dangerous scenario.
- Most optimistic scenario.
- Leading indicators that would make each scenario more likely.

Scenarios are not forecasts. Tie each to evidence from the vertical and
horizontal axes.

## 5. Object-Type Adaptation

Keep the double-axis method unchanged, but shift emphasis by object type.

Product:

- Vertical: version history, technical route, UX decisions, distribution,
  pricing, customer adoption, major incidents.
- Horizontal: feature fit, user experience, pricing, switching cost, ecosystem,
  issue trackers, reviews, competitors and substitutes.

Company:

- Vertical: founding team, financing, pivots, leadership, org changes, growth,
  layoffs, strategic partnerships, crises.
- Horizontal: business model, customers, market role, hiring reality, revenue
  signals, legal risk, competitor positioning.

Concept or Technology:

- Vertical: origin, theoretical lineage, early debates, diffusion path,
  canonical papers/docs, implementation history.
- Horizontal: adjacent concepts, competing methods, benchmarks, real-world
  deployment, limitations, misuse.

Person:

- Vertical: background, career stages, key decisions, public statements,
  output, affiliations, turning points.
- Horizontal: peers, influence, track record, incentives, critics, concrete
  artifacts and actions.

Market or Career:

- Vertical: how the field or role emerged, what changed demand, which titles or
  skills are new vs renamed.
- Horizontal: segments, employers, compensation, hiring volume, adjacent roles,
  real day-to-day work, entry paths, hidden requirements.

Academic or Literature Review:

- Vertical: foundational work, method lineage, major papers, benchmark history,
  paradigm shifts.
- Horizontal: current methods, datasets, leaderboards, replications,
  limitations, deployment gap.

Claim or Metric:

- Vertical: where the claim originated, how it spread, what context was lost.
- Horizontal: independent data, methodology, denominator, comparable metrics,
  rebuttals, incentives.
- Verdict must be one of: Confirmed, Likely, Contested, Not supported,
  Unresolved.

## 6. Evidence and Citation Rules

For every important source, capture:

- Title or source name.
- Author, organization, or platform.
- Publication date; access date for unstable topics.
- URL or local file path.
- Source class: official, behavioral, operator, lived experience, adversarial,
  market proxy, or artifact.
- What the source proves and what it does not prove.

Quality markers:

- `✓` primary, artifact, close-to-source, or independently verifiable.
- `?` secondary, partial, dated, anecdotal, or context-limited.
- `✗` contradicted, promotional, weak, or methodologically unclear.

Citation behavior:

- Cite claims near where they appear.
- Prefer original sources over summaries.
- Do not cite snippets as if they were full sources.
- If sources disagree, cite both sides and explain why.
- Mark unavailable information explicitly. Never invent.

## 7. Output Structure

For quick tasks, answer in compact form:

```markdown
## Bottom Line
[judgment, confidence, and why it matters]

## Vertical Signal
[history or origin pattern that matters]

## Horizontal Signal
[current comparison / alternatives / user reality]

## Cross-Axis Judgment
[what the combination reveals]

## Caveats
[missing evidence, contradictions, what would change the view]

## Sources
[key citations with quality markers]
```

For deep research, use:

```markdown
# Research: {object}

## One-Sentence Definition
[what it is and why it matters]

## Research Frame
[object type, user intent, scope, focus, evidence standard]

## Vertical Analysis: How It Got Here
[origin, birth, key nodes, phases, decisions, path dependence]

## Horizontal Analysis: Where It Stands Now
[comparison set, dimensions, user/operator reality, competitive position]

## Cross-Axis Insight
[history shaping position, strengths/weaknesses roots, contradictions, scenarios]

## Verdict
[confirmed/likely/contested/not supported/unresolved claims, confidence]

## Sources
[metadata-rich citations with quality markers]
```

## 8. Writing Standards

Write like a rigorous research report that a real decision-maker can finish.

- Use concrete details instead of generic consulting language.
- Put facts before judgment; mark inference as inference.
- Prefer causal explanation over list-making.
- Do not hide uncertainty behind polished prose.
- Avoid filler phrases such as "it is worth noting", "in today's fast-changing
  world", "empower", "closed loop", "obviously", or "in summary".
- Use specific names, dates, numbers, documents, and examples when available.
- If something cannot be found, say it is not found.

## 9. Quality Checklist

Before final output, check:

- Is there a clear vertical story with causal stages?
- Are key events and decisions sourced?
- Is the horizontal comparison set appropriate, not arbitrary?
- Did user/operator reality get checked, not just official narrative?
- Did at least one challenge path run against the main thesis?
- Are source dates visible for time-sensitive claims?
- Are important conclusions triangulated or explicitly marked as not
  triangulated?
- Does the cross-axis section produce new judgment instead of repeating earlier
  sections?
- Are confidence and "what would change the view" explicit?
- Did the answer avoid inventing missing facts?
