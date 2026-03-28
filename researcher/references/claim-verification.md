# Reference Pack: Claim Verification

Load this pack when the task is to verify whether a specific claim, narrative,
metric, or report is true, exaggerated, false, or unresolved. Works across all
domains.

## Workflow

1. **Decompose** — rewrite the claim into concrete, falsifiable subclaims
2. **Build parallel paths** — support and attack simultaneously
3. **Prioritize hard evidence** — primary, behavioral, artifact, and adversarial
   sources over opinion or narrative
4. **Test scope** — for market or role claims, check both exact-match and
   adjacent evidence before concluding
5. **Compare incentives** — who benefits from this claim being believed?
6. **Close with verdict** — explicit, not hedged into uselessness

## Source Priorities

For each subclaim try to find:

- Primary source (the original data, filing, paper, or artifact)
- Behavioral evidence (does reality match the claim?)
- Independent corroboration (a second source class agreeing)
- Adversarial evidence (who disagrees and why?)

## Query Patterns

- `"{exact claim}" source OR original`
- `"{claim subject}" data OR statistics OR report`
- `"{claim}" criticism OR rebuttal OR debunk`
- `"{claim}" reddit OR forum`
- `"{claim subject}" lawsuit OR complaint OR controversy`
- `"{metric}" methodology OR how measured`

## Challenge Discipline

For each subclaim ask:

- Is the original source identifiable and readable?
- Is the metric well-defined and independently verifiable?
- Who funded or published this, and what are their incentives?
- Does the claim survive outside its original context?
- What would falsify it?

## Verdict Labels

Use exactly one per subclaim and one overall:

- **Confirmed** — multiple independent source classes agree
- **Likely** — supported but with gaps or limited sources
- **Contested** — credible evidence on both sides
- **Not supported** — claim lacks credible backing
- **Unresolved** — insufficient evidence to judge either way

## Output Template

```text
- Claim Frame (original claim, decomposed subclaims)
- Evidence For
- Evidence Against
- Source Gaps
- Incentive Analysis
- Verdict (per subclaim + overall)
- What Would Change The Verdict
```
