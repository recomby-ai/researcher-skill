---
name: researcher
description: >
  Runs structured multi-source research, investigation, claim verification,
  due diligence, market research, academic literature review, competitive
  analysis, opportunity scanning, and risk assessment. Use for prompts such as
  research, investigate, verify, compare, analyze, fact check, deep dive,
  literature review, market landscape, due diligence, 研究, 调研, 分析, 验证,
  核实, 深挖, 行业分析, 市场调研, 竞品分析, 尽职调查, 这个靠谱吗,
  真实情况是什么, 有没有前景, 值不值得, 到底怎么样, 是真的吗.
argument-hint: <research question or topic / 研究问题或主题>
allowed-tools:
  - WebSearch
  - WebFetch
  - Read
  - Write
---

# Researcher Skill

## Purpose and Non-Negotiables

Treat research as a mixed evidence problem, not a search-result collection.
The job is to frame the question, map the evidence environment, follow the
highest-value leads, attack the working view, and synthesize a decision-grade
answer with confidence and caveats.

Always preserve this cycle:

```text
FRAME -> MAP -> FRONTIER -> DEEPEN -> CHALLENGE -> SYNTHESIZE
```

Non-negotiables:

- Default output is an answer in chat. Create or update a durable artifact only
  when the user asks for one, provides an output path, or the work is too large
  to remain useful inline.
- Broad first pass means source-class coverage, not URL hoarding.
- Fetch and read high-value sources before relying on snippets or widening.
- After mapping, searches should follow named leads, not generic rephrases.
- Important conclusions need 2+ source classes or an explicit unresolved note.
- Every strong thesis needs a challenge path before final synthesis.
- Social, review, and forum sources are signal sources, not standalone truth.

## Modes: Quick / Standard / Deep

Choose the smallest mode that can answer the user's decision. If the user names
a mode, follow it. If urgency or scope is ambiguous, use Standard.

| Mode | Use When | Typical Budget | Output Expectation |
| --- | --- | --- | --- |
| Quick | Triage, sanity check, narrow claim, initial landscape | 3-6 searches/fetches, 2-3 source classes, 1 challenge check | Short answer, verdict, 3-6 cited sources, caveats |
| Standard | Most research, comparisons, diligence, career/market scans | 8-15 searches/fetches, 4+ source classes, 2-4 leads, 2+ challenge checks | Structured brief with field map, evidence, verdicts, confidence |
| Deep | High-stakes or broad landscape, literature review, complex due diligence | 20-40 searches/fetches, full source-class sweep, explicit ledger/matrix, multiple challenge paths | Research brief or artifact, evidence matrix, scenarios, unresolved questions |

If near budget, prioritize synthesis and uncertainty over more searching.

## Core Workflow

1. FRAME: define the decision, claims, stakeholders, scope, source classes, and
   evidence that would change the answer.
2. MAP: run a broad first pass across source classes and produce a field map.
3. FRONTIER: select 2-4 active leads by decision relevance, source proximity,
   information gain, coverage gap, contradiction value, and path dependence.
4. DEEPEN: read substantive sources, extract findings, note gaps, and jump to
   the next best lead.
5. CHALLENGE: attack the strongest thesis with adversarial, behavioral, and
   contrary-source searches.
6. SYNTHESIZE: assign verdict labels, confidence, and what could change the
   view.

For each active lead, use:

```text
Search/Fetch -> EXTRACT -> CHALLENGE -> NEXT JUMP
```

Branch types:

- `Claim`: statement needing support or falsification.
- `Stakeholder`: company, lab, operator, user group, regulator, critic.
- `Source-gap`: missing source class or primary document.
- `Artifact`: paper, repo, docs, dataset, filing, benchmark, legal document.
- `Contradiction`: rebuttal, complaint, failed case, competing narrative.
- `Trajectory`: trend in hiring, pricing, adoption, funding, regulation.

Stop widening when major actors are visible, relevant source classes are known,
main debates are named, repeated searches return known nodes, and at least one
contradiction path exists.

## Frame / Research Brief

Before searching, create a lightweight research brief. Keep it short in Quick
mode and fuller in Standard/Deep.

Research Brief fields:

- Decision question or judgment target.
- Scope boundaries: geography, time period, audience, object type, exclusions.
- Key claims/subclaims to confirm, weaken, or falsify.
- Stakeholders and incentives.
- Required source classes and likely best primary artifacts.
- Subtopics or perspectives to decompose the work.
- Evidence that would change the answer.
- Output shape requested by the user, or default answer if none was requested.

For A-vs-B decisions, frame criteria first and compare options against the same
criteria. For claim verification, decompose the claim into concrete falsifiable
subclaims.

## Source Classes and Evidence Quality

Use the source-class model to avoid one-dimensional answers:

- Official: institutions, companies, regulators, authors, standards bodies.
- Behavioral: hiring, pricing, releases, commits, launches, adoption, churn.
- Operator: experienced practitioners, maintainers, executives, recruiters.
- Lived experience: users, employees, students, customers, communities.
- Adversarial: critics, short reports, lawsuits, complaints, debunks.
- Market proxy: fundraising, layoffs, salary, M&A, search demand, procurement.
- Artifact: papers, repos, docs, datasets, filings, benchmarks, contracts.

Quality markers:

- `✓` primary, artifact, close-to-source, or independently verifiable evidence.
- `?` secondary, partial, dated, anecdotal, or context-limited evidence.
- `✗` contradicted, weak, promotional, methodologically unclear, or problematic.

Triangulation rule for important conclusions:

- Prefer one official or artifact source.
- Prefer one behavioral or market source.
- Prefer one human or adversarial source.
- If triangulation is impossible, state the missing source class and why.

## Metadata and Citation Rules

For each important source capture enough metadata to make the evidence auditable:

- Title or source name.
- Author, publisher, organization, or platform when available.
- Publication date and, for unstable topics, access date.
- URL or stable identifier.
- Source class and quality marker.
- Any method, sample, benchmark, jurisdiction, or population limits.

Citation behavior:

- Cite claims near where they appear, not only in a reference dump.
- Prefer primary/original sources over summaries; use summaries to find primary
  sources, not to replace them.
- For dated topics, make recency visible and do not mix old and new evidence
  without noting time gaps.
- Quote sparingly; paraphrase and preserve the claim, context, and caveat.
- If sources disagree, cite both sides and explain what each source can and
  cannot establish.

## Local/User-Provided Materials

User-provided files, pasted text, links, datasets, transcripts, notes, or prior
research are first-class sources.

Rules:

- Read local/user-provided materials before external search when they define
  the task, contain private context, or are likely more authoritative.
- Preserve the user's terminology unless it conflicts with public evidence.
- Distinguish "from provided material" from "externally corroborated."
- Do not upload, quote extensively, or expose private material unless needed
  for the requested output.
- If local material conflicts with web evidence, surface the conflict and
  attempt to resolve it through artifacts or primary sources.

## Object-Type Playbooks

Adapt the workflow to the object being researched.

Product:

- Check official docs, pricing, changelog, demos, repos, reviews, issue
  trackers, customer proof, competitors, and switching costs.
- Test product claims against artifacts and user/operator reality.

Company:

- Check official narrative, filings/investor material, customers, hiring,
  leadership, funding, layoffs, lawsuits, complaints, reviews, and market role.
- Compare growth claims with behavioral and market-proxy signals.

Industry or Market:

- Map segments, key actors, demand drivers, regulation, value chain, adoption
  signals, funding/M&A, substitutes, and skeptics.
- Separate market size claims from demonstrated spend or deployment.

Career or Talent:

- Check job descriptions, skill requirements, salary ranges, location, hiring
  volume, LinkedIn profiles, practitioner accounts, and adjacent titles.
- Separate exact-title evidence from adjacent-title evidence because titles lag
  actual work.

Concept, Technology, or Method:

- Check definitions, lineage, canonical papers/docs, implementations,
  benchmarks, limitations, misuse, competing methods, and deployment evidence.
- Distinguish benchmark success from real-world usefulness.

Person:

- Check primary profiles, publications, talks, affiliations, track record,
  conflicts of interest, critics, and dated claims.
- Avoid overreading biography; tie conclusions to artifacts and actions.

Claim or Metric:

- Identify the original source, definition, methodology, denominator, timeframe,
  and scope.
- Build support and attack paths in parallel; close with verdict per subclaim.

Meta-Research or "What Patterns Transfer?":

- Extract recurring mechanisms, boundary conditions, failure modes, analogues,
  and transferability criteria.
- Output patterns with "works when / fails when / evidence strength."

Academic or Technical Literature:

- Start with a recent useful survey, then representative recent papers,
  foundational papers, benchmark/dataset sources, and replication/limitation
  work.
- Traverse backward for assumptions, forward for influence, and sideways for
  competing methods.

Lightweight Scoping Review:

- Define inclusion/exclusion criteria, date range, source databases or search
  surfaces, screening logic, and synthesis categories.
- Use when the user needs a transparent map of literature or evidence rather
  than a single answer.

## Optional Lenses

Use only when helpful; do not force every lens into every answer.

Horizontal / Vertical:

- Horizontal lens: compare across categories, competitors, use cases, regions,
  methods, or customer segments.
- Vertical lens: follow one stack, value chain, implementation path, user
  journey, causal chain, or adoption path in depth.

Perspective decomposition:

- Include perspectives such as buyer, user, operator, regulator, investor,
  competitor, maintainer, critic, beginner, and expert.
- Use perspectives to find blind spots and explain why sources disagree.

Competitor scope:

- None: use when the object is standalone, early-stage, or comparison would
  distract from verification.
- 1-2 competitors: use for focused purchase, product, company, or career
  comparisons.
- 3+ competitors: use for landscape, market map, category strategy, or
  positioning. Group competitors into segments instead of listing endlessly.

Path-dependence questions:

- What previous choices constrain current options?
- What switching costs, standards, regulations, data, relationships, or habits
  make change hard?
- Which early signals are self-reinforcing, and which are reversible?

Future scenarios:

- Build 2-4 plausible scenarios from drivers, constraints, and uncertainties.
- Name leading indicators that would make each scenario more likely.
- Avoid pretending scenarios are forecasts; connect them to evidence.

## Query / Deepening Rules and Evidence Ledger

Use a query ladder:

1. Exact object or claim: names, quoted claims, official source.
2. Primary artifacts: filings, docs, papers, datasets, repos, standards.
3. Behavioral signals: pricing, hiring, releases, adoption, procurement.
4. Operator/lived experience: practitioners, maintainers, forums, reviews.
5. Adversarial: criticism, limitations, failures, lawsuits, complaints.
6. Adjacent terms: synonyms, predecessor names, competitors, local language.
7. Time filters: recent evidence for fast-changing topics; older evidence for
   origin and path dependence.

Search guidance:

- Use English first for most global topics; add local language for region-
  specific claims or lived experience.
- Use exact-match queries for specific claims and broader queries for field maps.
- Use site/domain filters for known primary sources.
- Prefer high-information sources over many low-information URLs.
- Record failed searches when the absence of evidence matters.

Evidence ledger fields, inline or in a durable artifact:

| Claim / Lead | Evidence | Source Class | Quality | Date | Supports / Weakens | Caveat | Next Step |
| --- | --- | --- | --- | --- | --- | --- | --- |

Use an evidence matrix in Deep mode or when many subclaims/options must be
compared. In Quick mode, keep the ledger mentally or as a short bullet list.

## Challenge Rules

Challenge is mandatory before final synthesis.

Challenge prompts:

- What source class most disagrees with the current view?
- Who benefits from overstating the thesis?
- Who benefits from attacking it?
- Did official narrative and operator/lived reality both get checked?
- Did behavioral or market evidence confirm the narrative?
- What would falsify the key claim?
- Is the signal marketing, selection bias, survivorship bias, or measurement
  artifact?
- Does the conclusion still hold for the relevant geography, timeframe, user
  segment, or deployment context?

Challenge searches:

- `"{object or claim}" criticism OR limitation OR failure`
- `"{object or claim}" lawsuit OR complaint OR controversy`
- `"{object or claim}" reddit OR forum OR blind OR glassdoor`
- `"{metric or claim}" methodology OR source OR denominator`
- `"{method or product}" benchmark OR replication OR comparison`
- `"{company}" layoffs OR churn OR short report OR allegations`

When challenge evidence is weak, say so. Do not invent balance where one side
has much better evidence.

## Synthesis Rules

Use verdict labels consistently:

- Confirmed: supported by multiple credible source classes.
- Likely: supported, but with gaps or limits.
- Contested: credible evidence exists on both sides.
- Not supported: credible backing is missing or contradicted.
- Unresolved: insufficient evidence to judge.

For each major conclusion include:

- Verdict label.
- Evidence basis and strongest source classes.
- Confidence: high, medium, or low.
- Key caveat or contradiction.
- What could change the view.

Confidence guidance:

- High: primary/artifact evidence plus independent behavioral or human signal,
  with challenge path checked.
- Medium: credible support but partial triangulation, dated evidence, or scope
  limits.
- Low: sparse, indirect, anecdotal, promotional, or fast-changing evidence.

Synthesis should separate:

- What is known.
- What is inferred.
- What is contested.
- What is still unknown.
- What action or decision follows, if the user asked for one.

## Output Shapes

Default answer shape:

```markdown
## Bottom Line
[answer, verdict, confidence]

## Evidence
[key findings with citations and source classes]

## Caveats / Challenge
[contradictions, missing evidence, incentive issues]

## What Could Change This
[specific evidence or events]
```

Research Brief shape:

```markdown
# Research Brief: {topic}

## Frame
[question, scope, claims, stakeholders, criteria]

## Field Map
[actors, source classes, debates, blind spots]

## Evidence Ledger
[claim/lead, evidence, source class, quality, date, caveat]

## Challenge
[best contrary evidence and unresolved tensions]

## Synthesis
[verdict labels, confidence, implications, what could change the view]

## References
[metadata-rich citations]
```

Variant emphasis:

- Claim verification: subclaims, evidence for/against, incentive analysis,
  verdict per subclaim and overall.
- Company/product diligence: narrative, artifacts, behavioral signals, user or
  operator reality, risks, competitor context, bottom-line judgment.
- Market/career scan: segments or roles, demand signals, repeated patterns vs
  anecdotes, opportunity/risk ranking, confidence.
- Academic/literature review: literature map, methods, benchmark context,
  limitations, open problems, state-of-the-art judgment.
- Meta-research: patterns, transferability, boundary conditions, failure modes,
  analogues, evidence strength.
- Future scenarios: drivers, constraints, scenarios, indicators, implications.

## Done Criteria and Anti-Patterns

Done when:

- The decision question is answered or explicitly unresolved.
- Main claims are attached to high-value sources with dates/metadata.
- Support and challenge paths were both explored.
- Relevant source classes were sampled or missing classes are named.
- Important conclusions are triangulated or marked as not triangulated.
- New searches mostly repeat known nodes.
- Remaining frontier items are peripheral or clearly listed.

Not done when:

- Only the supporting story was explored.
- The synthesis depends on snippets or summaries.
- Official and community narratives sharply disagree without resolution.
- No opposing incentives or falsification path were considered.
- Dates, geography, sample, or methodology are unclear for key evidence.
- Social anecdotes are treated as truth without triangulation.
- Market-size, benchmark, or title claims are accepted without definitions.

Anti-patterns:

- Creating a research file by default when a concise answer would serve.
- URL hoarding without source-class diversity.
- Treating recency as quality or age as irrelevance.
- Collapsing "users say," "company says," and "data shows" into one claim.
- Ignoring local/user-provided material in favor of public web search.
- Overfitting to one competitor, one geography, one platform, or one anecdote.
- Forcing certainty when the honest answer is contested or unresolved.
