---
name: claim-validation-research
description: >
  Claim-checking research for contested statements, rumors, reports, metrics,
  or narratives. Use when Codex must test whether a concrete claim is true,
  false, exaggerated, or unresolved by tracing support and counter-evidence
  across multiple source classes. Trigger for requests such as "is this true",
  "verify this", "fact check", "does this report hold up", or "stress-test
  this thesis".
---

# Claim Validation Research

Turn a claim into a falsifiable investigation.

Read shared references:
- `../researcher/references/core-method.md`
- `../researcher/references/source-hierarchy.md`
- `../researcher/references/saturation-and-counterevidence.md`
- `../researcher/references/query-shaping.md`

## Workflow

1. Rewrite the claim into concrete subclaims that can be tested.
2. Build support and attack paths in parallel.
3. Prioritize primary, artifact, behavioral, and adversarial evidence.
4. If the claim is about a market, role, or category, test both exact-title and
   adjacent-title evidence before concluding.
5. Compare incentives, missing evidence, and contradiction patterns.
6. End with an explicit verdict, not a vague summary.

## Verdict Labels

Use one of:
- `confirmed`
- `likely`
- `contested`
- `not supported`
- `unresolved`

## Output

Create or update `research-{topic}.md` while working so the reasoning stays
externalized.

Prefer sections like:
- Claim Frame
- Evidence For
- Evidence Against
- Source Gaps
- Verdict
- What Would Change The Verdict
