# Research Heuristics

Load this file when you need detailed decision rules for frontier selection,
scientific literature traversal, source hierarchy, saturation, or query design.

## 1. Frontier scoring

When deciding which branches to deepen next, score them qualitatively against
these dimensions:

1. `Source proximity`
   How close is this lead to a primary or highest-value source?
2. `Information gain`
   How likely is this branch to add genuinely new understanding?
3. `Centrality`
   Does this branch matter to the user's main question?
4. `Coverage gap`
   Is this area still underexplored in the current field map?
5. `Recency value`
   Does the question depend on the current state of the field?
6. `Conflict value`
   Could this branch surface contradiction, limitation, or rebuttal?

Selection rule:
- Early deepen phase: preserve breadth and deepen 2-4 branches
- Mid deepen phase: prune low-yield branches, keep 1-3 strong branches
- Late phase: converge only after major branches have been tested

Do not always follow only the single top-scoring branch.

## 2. Branch types

Useful frontier branch types:
- `Method branch`
  A family of approaches or techniques
- `Evidence branch`
  A key empirical claim or result chain
- `Benchmark branch`
  Dataset, leaderboard, protocol, or metric lineage
- `Researcher/lab branch`
  A person, lab, company, or institution driving the work
- `Criticism branch`
  Limitations, replication, or competing claims
- `Primary-document branch`
  A filing, patent, standard, official paper, or source document

## 3. Breadth mapping heuristics

The first pass should be broad enough to map the field, but not so broad that
it turns into result hoarding.

Aim to identify:
- the latest available overview source
- the current leading branches
- the historical or defining roots
- the evaluation layer
- the main criticism or uncertainty layer

Breadth floor:
- cover the main schools or methods
- cover the latest representative work
- cover a source of skepticism or limitation

Breadth ceiling:
- do not collect dozens of near-duplicate papers
- do not keep every discovered branch alive
- do not mistake many URLs for real coverage

## 4. Scientific literature traversal

For scientific and technical topics, the map phase should usually look for:
- latest available review, survey, tutorial, benchmark, perspective, or field
  overview
- recent representative papers
- foundational or defining papers
- benchmarks, datasets, evaluation protocols, or standards
- criticism, limitation, replication, or alternative approaches

After mapping, deepen by jumping across the graph:

1. `Backward`
   What does this paper repeatedly cite?
2. `Forward`
   Who cited this source later?
3. `Sideways`
   What competing methods solve the same problem?
4. `Downward`
   What appendix, supplementary material, code, dataset, or benchmark clarifies
   the claim?

Useful jump patterns:
- review or survey → repeatedly cited original paper
- recent paper → cited baselines, appendix, code, or benchmark
- benchmark paper → dataset definition, metric definition, reproducibility notes
- criticism paper → criticized paper and any response or rebuttal
- lab or author → project page, official repo, talk, or technical report

## 5. Source hierarchy by domain

Do not assume every question has the same notion of "primary source."

### Scientific and technical research

Highest-value sources usually include:
- original paper
- supplementary material or appendix
- code repository
- dataset documentation
- benchmark or evaluation documentation

### Industry, companies, and products

Highest-value sources usually include:
- regulator filing
- earnings report or shareholder letter
- company announcement
- patent
- standard or certification document
- official technical documentation

### Medicine and public health

Highest-value sources usually include:
- systematic review or meta-analysis
- randomized controlled trial
- guideline
- registry
- regulator source

When the question is about the current state of a field, you often need both:
- newest reliable overview material
- original evidence behind the key claim

## 6. Counter-evidence rules

For each major claim, actively search for:
- criticism
- limitation
- failure case
- replication or reproducibility concern
- contradictory evidence
- competing approach

Do not stop because support was found. Stop only after support and challenge
paths have both been checked enough.

## 7. Saturation rules

Research is closer to done when:
- the major branches of the field map are understood
- key claims are attached to primary or highest-value sources
- new results mostly point back to already-known nodes
- new results no longer add new method classes, evidence layers, or major
  debates
- remaining frontier items are low-yield, redundant, or peripheral

Research is not done when:
- only one branch has been explored deeply
- the synthesis still leans on snippets or overview summaries
- no criticism or limitation path was followed
- "new" results are only new webpages, not new information

## 8. Query-shaping heuristics

Use query diversity early, then increasingly specific lead-chasing later.

Map phase query shapes:
- `{topic} review OR survey`
- `{topic} benchmark OR evaluation`
- `{topic} limitation OR criticism OR replication`
- `{topic} seminal paper`
- `{topic} recent paper`

Deepen phase query shapes:
- `"{paper title}"`
- `"{paper title}" site:semanticscholar.org`
- `"{method}" vs "{competing method}"`
- `"{claim}" original paper`
- `"{dataset}" documentation`
- `"{author or lab}" project page`

Search in English for academic literature unless the field or source ecosystem
requires another language. For regional industry, policy, or regulation, also
search the local language.
