# Reference Pack: Academic Research

Load this pack when the question is paper-heavy, benchmark-heavy, or involves
technical lineage and state-of-the-art assessment.

## Source Priorities

Prioritize in this order:

1. Latest useful survey or review
2. Representative recent papers
3. Foundational papers
4. Benchmark, dataset, or evaluation sources
5. Replication, limitation, or competing-method papers

Companion artifacts (use alongside papers, not instead of):

- Project pages and code repos
- Benchmark docs and leaderboards
- Model cards and dataset cards
- Conference talks and workshop recordings

## Traversal Strategy

Map first, then traverse by citation graph:

- **Backward** — identify foundations and assumptions
- **Forward** — see what actually influenced the field
- **Sideways** — compare competing methods, benchmarks, and replications

## Query Patterns

Discovery:

- `site:arxiv.org "{topic}"`
- `site:arxiv.org "{topic}" survey OR review`
- `site:pubmed.ncbi.nlm.nih.gov "{topic}"`
- `site:ieee.org "{topic}"`
- `site:dl.acm.org "{topic}"`
- `site:paperswithcode.com "{topic}"`
- `"{topic}" state of the art OR SOTA`

Deep traversal:

- `"{paper title}" pdf`
- `"{method}" benchmark OR evaluation OR comparison`
- `"{method}" replication OR limitation OR fails`
- `"{dataset}" official`
- `site:github.com "{method or tool}"`
- `"{author}" google scholar`

## What to Extract

For each important technical conclusion record:

- The paper or artifact that supports it
- The benchmark or evaluation context
- What the result does not prove
- Whether a contrary paper or limitation path was checked

## Challenge Paths

Actively test for:

- Cherry-picked benchmarks (does the result hold on other datasets?)
- Replication failures
- Limitations acknowledged in the paper but ignored in citations
- Gap between benchmark performance and real-world deployment
- Competing methods achieving similar results with less complexity
- Recency bias — is the "breakthrough" actually incremental?

## Output Template

```text
- Research Question
- Literature Map (surveys, foundations, recent work, competing approaches)
- Key Findings And Evidence
- Benchmark And Evaluation Context
- Limitations And Open Problems
- Contrary Evidence
- Synthesis And State Of The Art
- References (with source quality markers)
```
