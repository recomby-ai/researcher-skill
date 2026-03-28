---
name: researcher
description: >
  General-purpose research operating system for open-ended investigation,
  verification, comparison, diligence, and decision support. Use when Codex
  must map a problem space, trace claims across multiple source classes, follow
  high-value leads, search for counter-evidence, or form an explicit judgment.
  Trigger for requests such as "research", "investigate", "verify", "compare",
  "what is really happening", "do diligence", or "how do real practitioners
  see this". Prefer the purpose-specific sibling skills when the request is
  clearly about field mapping, claim validation, decision support, opportunity
  scouting, due diligence, or operator reality.
---

# Research Operating System

Investigate the internet as a mixed evidence environment, not as a pile of
search results. Preserve the old breadth-first then depth-first discipline, but
upgrade it from topic mapping to evidence mapping.

Core cycle:

```text
FRAME → MAP → FRONTIER → DEEPEN → CHALLENGE → SYNTHESIZE
```

Read shared references as needed:
- [references/core-method.md](references/core-method.md)
  for the core workflow and logging rules
- [references/source-hierarchy.md](references/source-hierarchy.md)
  for evidence classes, source quality, and bias handling
- [references/frontier-management.md](references/frontier-management.md)
  for branch scoring, pruning, and deepen order
- [references/query-shaping.md](references/query-shaping.md)
  for query patterns across official, social, adversarial, and artifact sources
- [references/saturation-and-counterevidence.md](references/saturation-and-counterevidence.md)
  for stopping rules and challenge-path design
- [references/scientific-literature.md](references/scientific-literature.md)
  for paper-heavy or benchmark-heavy research
- [references/source-packs-jobs.md](references/source-packs-jobs.md)
  for roles, JD, salary, and career-path research
- [references/source-packs-field-signals.md](references/source-packs-field-signals.md)
  for Reddit, X, LinkedIn, forums, GitHub, Blind, and Glassdoor
- [references/source-packs-company-intel.md](references/source-packs-company-intel.md)
  for company, customer, product, hiring, short-report, and lawsuit research

## Purpose Routing

Use this skill directly when the task is broad or ambiguous and you need to
decide which research mode to run.

If the user intent is already clear, prefer the focused sibling skill:
- `field-mapping-research` for landscape scans and field maps
- `claim-validation-research` for "is this claim true?" work
- `decision-support-research` for choosing a path, option, or strategy
- `opportunity-research` for where upside or growth may exist
- `due-diligence-research` for stress-testing a company, product, or thesis
- `operator-reality-research` for lived experience and practitioner reality

## Non-Negotiable Rules

- Broad first pass means covering multiple evidence classes, not hoarding URLs.
- Cap the first mapping round at roughly 4-6 search actions before writing the
  field map and frontier.
- Once a high-value lead appears, fetch and read substantive sources before
  widening again.
- After the map phase, new searches must be lead-driven, not generic rephrases.
- Treat social posts, community threads, and short reports as valuable lead
  sources and challenge sources, not as standalone truth.
- Every important conclusion needs either support from at least two source
  classes or an explicit note that it remains unresolved.
- Every strong thesis must run a challenge path before final synthesis.

## Output

Create `research-{topic}.md` in the current directory and update it throughout
the run. Keep the log externalized so the reasoning is visible.

Recommended sections:

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
[important sources with URLs and source quality]
```
