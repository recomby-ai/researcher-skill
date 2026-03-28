# Reference Pack: Business Research

Load this pack for industry landscape, company or product diligence, career and
job market research, opportunity scouting, or operator reality investigation.

These topics form a natural research chain: an industry contains companies,
companies contain roles, roles contain practitioners. Move along this chain as
the investigation demands.

## Source Priorities and Query Patterns

### Industry and Market

Best sources:

- Industry reports, analyst coverage, market maps
- Company career pages and hiring patterns (proxy for real investment)
- Fundraising, M&A, partnership announcements
- Reddit, X, and forums for practitioner sentiment on trends
- Short reports and critics for hype checks

Queries:

- `{industry} overview OR landscape OR market map`
- `{industry} key players OR leading companies OR leading labs`
- `{industry} criticism OR controversy OR limitations OR bubble`
- `{industry} hiring OR jobs OR salary`
- `{industry} reddit OR forum`
- `{industry} short report OR lawsuit`

### Company and Product

Best sources:

- Official narrative (website, press, investor materials)
- Product docs, demos, repos, release cadence
- Customer and partner evidence (case studies, reviews, testimonials)
- Hiring and org shape (career pages, LinkedIn, headcount trends)
- Adversarial material (short reports, lawsuits, complaints, whistleblowers)
- User and operator commentary (forums, issue trackers, social)

Queries:

- `site:{company}.com`
- `"{company}" customers case study`
- `"{company}" careers OR hiring`
- `"{company}" glassdoor OR blind`
- `"{company}" short report OR allegations OR lawsuit`
- `"{product}" documentation OR github`
- `"{product}" review OR comparison`

**Internal consistency test** — check whether the story holds across:

- Product claims vs customer evidence
- Hiring patterns vs growth narrative
- Pricing and GTM behavior vs market positioning
- Technical artifacts vs marketing language

### Career and Talent

Best sources:

- Job descriptions and career pages
- LinkedIn profiles and role trajectories
- Salary ranges, compensation reports, location data
- Recruiter or hiring manager commentary
- Practitioner posts about day-to-day work
- GitHub or portfolio artifacts (for technical roles)

Queries:

- `"{role}" job description`
- `"{role}" salary OR compensation`
- `"{role}" "day in the life" OR "what it's like"`
- `"{role}" reddit OR blind OR glassdoor`
- `"{role}" career path OR trajectory`
- `"{company}" {role} linkedin`

What to extract:

- Repeated skill requirements
- Seniority mismatches hidden under titles
- Regional differences
- Adjacent entry paths
- Whether the role is real, inflated, or evolving

**Title rule:** Separate exact-title evidence from adjacent-title evidence.
Titles lag the work itself. A role is not unreal merely because the exact title
is rare.

## Field Signals and Lived Experience

Best places:

- Reddit and specialist forums — detailed pain points
- X — fast-moving narratives, operator commentary
- LinkedIn — role descriptions, trajectories, professional norms
- GitHub issues and repos — real technical friction
- Blind and Glassdoor — employer-specific internal sentiment

Usage rules:

- Treat as signal and friction sources, not standalone truth
- Look for repeated patterns across people, platforms, and time
- Extract: repeated complaints, hidden requirements, day-to-day reality,
  "what outsiders get wrong", beginner vs experienced operator disagreement

## Adversarial Intelligence

For short reports, complaints, and lawsuits:

1. Identify the concrete allegations
2. Separate factual allegations from rhetoric
3. Verify each against other source classes
4. Record what remains unresolved — do not force closure

## Challenge Paths

Actively test for:

- Hype vs real adoption (marketing narrative ahead of reality?)
- Title inflation in job markets
- "Entry level" roles requiring senior experience
- Claimed growth vs actual hiring volume
- Official narrative vs operator sentiment mismatch
- Revenue or traction claims vs behavioral evidence

## Output Templates

### Industry or Market

```text
- Problem Frame
- Field Map (branches, actors, debates, blind spots)
- Key Actors And Positions
- Source Landscape
- Active Frontier
- Open Questions
```

### Company or Product Diligence

```text
- Diligence Frame
- Official Narrative
- Evidence That Supports It
- Evidence That Challenges It
- Risk Register
- Bottom-Line Judgment
```

### Career or Talent

```text
- Population Frame
- Role Reality (day-to-day, hidden requirements)
- Market Signals (demand, salary, trajectory)
- Repeated Patterns vs Anecdotes
- Mismatch With Public Narrative
- Confidence And Caveats
```

### Opportunity Scouting

```text
- Opportunity Frame
- Candidate Opportunities
- Evidence Of Real Demand
- Risks And Hype Checks
- Ranked Opportunities
- Recommended Next Bets
```
