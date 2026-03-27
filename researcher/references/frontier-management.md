# Frontier Management

Load this file when you need branch selection, scoring, pruning, or breadth
control rules.

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
- early deepen phase: preserve breadth and deepen 2-4 branches
- mid deepen phase: prune low-yield branches, keep 1-3 strong branches
- late phase: converge only after major branches have been tested

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
