---
name: researcher
description: >
  Runs multi-source investigations using a structured evidence-mapping cycle.
  Routes between business research, academic research, and claim verification.
  Triggers on: "research", "investigate", "verify", "compare", "analyze",
  "look into", "dig into", "fact check", "due diligence", "deep dive",
  "what is really happening", "how do real practitioners see this",
  "is this true", "is this legit", "what's the real story",
  "market landscape", "state of the art", "literature review",
  "competitive analysis", "opportunity scan", "risk assessment",
  "研究", "调研", "调查", "分析", "验证", "核实", "深挖", "摸底",
  "行业分析", "市场调研", "竞品分析", "尽调", "尽职调查",
  "这个靠谱吗", "真实情况是什么", "帮我查查", "帮我看看",
  "有没有前景", "值不值得", "到底怎么样", "是真的吗",
  "论文调研", "文献综述", "技术选型", "机会分析".
argument-hint: <research question or topic / 研究问题或主题>
allowed-tools:
  - WebSearch
  - WebFetch
  - Read
  - Write
---

# Research Operating System

Investigate the internet as a mixed evidence environment, not as a pile of
search results. Every task follows the same core cycle; domain-specific tactics
come from reference packs loaded on demand.

## Core Cycle

```text
FRAME → MAP → FRONTIER → DEEPEN → CHALLENGE → SYNTHESIZE
```

### 1. FRAME

Define the task before searching:

- Decision question or judgment target
- Key claims that may need confirmation or falsification
- Important stakeholders and their incentives
- Source classes likely to matter
- What would change the answer

**Load reference packs by task type:**

| Task signal | Load |
|-------------|------|
| Industry, company, career, opportunity, operator reality | [references/business.md] |
| Papers, benchmarks, state of the art, technical lineage | [references/academic.md] |
| "Is this true?", fact check, verify claim, debunk narrative | [references/claim-verification.md] |
| Mixed task | Load multiple packs |

When the task is a **decision between options** (choose A vs B), use the core
cycle but frame everything around decision criteria — see the Decision Support
output variant at the end of this file.

### 2. MAP

Run a broad first pass across multiple evidence classes using **WebSearch**.

Aim to surface:

- Official narrative
- Behavioral reality (what actors do, not just say)
- Operator or expert view
- Lived experience
- Adversarial or contradiction path

**Budget: 4-6 searches.** Stop and write a field map before going deeper.

Search in English first for most topics. When the claim is region-specific,
search both English and the relevant local language before synthesizing.

### 3. FRONTIER

Convert the map into 2-4 active leads. For each lead record:

1. What it is
2. Why it matters
3. Which source class it touches
4. Next action
5. What claim it could confirm or weaken

**Branch types:**

- `Claim` — a statement needing support or falsification
- `Stakeholder` — a company, lab, recruiter, operator, or critic that matters
- `Source-gap` — a missing source class or primary document
- `Artifact` — code, docs, dataset, filing, benchmark, or legal document
- `Contradiction` — a rebuttal, complaint, failed case, or competing narrative
- `Trajectory` — a trend in hiring, pricing, adoption, or regulation

**Scoring criteria** (qualitative, not numeric):

- Source proximity — how close to a primary or artifact source?
- Decision relevance — does resolving this change the answer?
- Information gain — new understanding vs more of the same?
- Coverage gap — blind spot in current map?
- Contradiction value — could it weaken the thesis?

**Selection rules:**

- Early: keep 2-4 branches for coverage
- Middle: prune branches that no longer change the answer
- Late: converge only after both support and challenge branches were checked
- Always keep at least one branch that could weaken the working thesis

**Breadth ceiling:** Stop widening and start deepening when the major actors are
visible, relevant source classes are known, main debates are named, and at
least one contradiction path exists. Many URLs is not coverage. Repeated
narratives are not independent evidence.

### 4. DEEPEN

For each active branch:

```text
WebSearch / WebFetch → EXTRACT → CHALLENGE → NEXT JUMP
```

Use **WebFetch** to read substantive sources (articles, docs, reports) rather
than relying on search snippets. After each step log:

- Finding
- Source and quality
- Contradiction or caveat
- Gap
- Next jump

**Budget: 2-3 fetches per branch.** Do not keep widening with generic searches
once lead-driven work has started.

### 5. CHALLENGE

For every strong thesis, actively search for:

- Direct rebuttal or criticism
- Failed example or contradictory user experience
- Short report, lawsuit, or adversarial analysis
- Competing explanation
- Evidence that the signal is marketing rather than reality

**Minimum challenge coverage before synthesis:**

- What source class most disagrees with the current view?
- Which stakeholder has incentives to overstate this thesis?
- Which stakeholder has incentives to attack this thesis?
- Were both operator reality and official narrative checked?
- Was behavioral evidence checked?

**Budget: 2-3 searches.**

### 6. SYNTHESIZE

Use **Write** to create `research-{topic}.md` in the current directory. Update
it throughout the run so reasoning is visible.

Separate findings into:

- **Confirmed** — supported by 2+ source classes
- **Likely** — supported but with gaps
- **Contested** — sources disagree
- **Unresolved** — insufficient evidence
- **What could change the view**

Mark source quality: `✓` primary/artifact `?` secondary/incomplete
`✗` contradictory/problematic

## Source Classes

Use multiple classes, not a single ranking:

| Class | What it is | Best for |
|-------|-----------|----------|
| Official | What institutions, companies, regulators say | Stated intent |
| Behavioral | What they actually do: hiring, pricing, commits, launches | Reality checks |
| Operator | What experienced practitioners say in long posts, talks | Expert view |
| Lived experience | Reddit, X, LinkedIn, forums, Blind, Glassdoor | Friction, day-to-day |
| Adversarial | Short reports, critics, lawsuits, complaints | Challenge paths |
| Market proxy | Fundraising, layoffs, salary, adoption, search demand | Economic weight |
| Artifact | Papers, repos, docs, datasets, filings, benchmarks | Hard evidence |

**Default triangulation** for important conclusions — try to combine:

- One official or artifact source
- One behavioral or market source
- One human or adversarial source

If triangulation is impossible, say so explicitly.

## Saturation Rules

Research is done when:

- Main claims are attached to high-value sources
- Support and challenge paths were both explored
- Relevant source classes were sampled, not just one ecosystem
- New searches mostly repeat known nodes
- Remaining frontier items are peripheral

Research is **not** done when:

- Only the supporting story was explored
- Community and official narratives sharply disagree without resolution
- Synthesis still depends on snippets or summaries
- No opposing incentives were considered

## Budget

| Phase | Tool | Limit |
|-------|------|-------|
| MAP | WebSearch | 4-6 |
| DEEPEN | WebSearch + WebFetch | 2-3 per branch |
| CHALLENGE | WebSearch | 2-3 |
| SYNTHESIZE | Write | 1 |
| **Total** | all | ~20 tool calls |

If approaching budget, prioritize synthesis over more searching.

## Non-Negotiable Rules

- Broad first pass means covering evidence classes, not hoarding URLs.
- Once a high-value lead appears, fetch and read it before widening again.
- After the map phase, new searches must be lead-driven, not generic rephrases.
- Social posts and community threads are valuable lead and challenge sources,
  not standalone truth.
- Every important conclusion needs support from 2+ source classes or an
  explicit note that it remains unresolved.
- Every strong thesis must run a challenge path before final synthesis.

## Output Template

```markdown
# Research: {topic}

## Frame
[decision question, target claims, stakeholders, evidence classes]

## Field Map
[main branches, actors, debates, source ecosystem, blind spots]

## Active Frontier
[2-4 active leads, why they matter, next action]

## Branch Log
### Branch A
[finding, source, contradiction, gap, next jump]

## Challenge Log
[what was used to attack the current thesis]

## Synthesis
[confirmed, likely, contested, unresolved, what could change the view]

## References
[important sources with URLs and source quality markers]
```

### Decision Support Variant

When the task is choosing between options, replace the output template with:

```markdown
# Decision: {question}

## Decision Frame
[options, constraints, time horizon, what matters most]

## Evidence By Criterion
[evidence gathered per decision criterion, not per random topic]

## Tradeoffs
[what you gain and lose with each option]

## Recommendation
[preferred path with explicit confidence level]

## What Would Change The Call
[conditions that would flip the recommendation]
```
