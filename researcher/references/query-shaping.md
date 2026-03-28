# Query Shaping

Load this file when default search behavior is not enough and the task needs
better query patterns across different source classes.

## 1. Phase-aware query strategy

Use broad evidence coverage early, then lead-chasing later.

Map phase patterns:
- `{topic} overview OR landscape`
- `{topic} key players OR leading companies OR leading labs`
- `{topic} criticism OR controversy OR failure OR limitations`
- `{topic} hiring OR jobs OR salary OR skills`
- `{topic} reddit OR forum OR x OR linkedin`
- `{topic} short report OR lawsuit OR complaint`

Deepen phase patterns:
- `"{claim}" source`
- `"{company or lab}" hiring OR careers`
- `"{product or repo}" documentation OR github`
- `"{person}" linkedin`
- `"{thesis}" rebuttal OR criticism`
- `"{report title}" pdf`
- `"{dataset or benchmark}" official`

## 2. Query by evidence class

Official and primary:
- `site:company.com`
- `site:sec.gov`
- `site:arxiv.org`
- `site:pubmed.ncbi.nlm.nih.gov`
- `site:ieee.org`
- `site:dl.acm.org`

Behavioral and market:
- `{company} careers`
- `{role} salary`
- `{topic} job description`
- `{product} pricing`
- `{company} customers case study`

Field signals and lived experience:
- `{topic} reddit`
- `{topic} forum`
- `{role} "day in the life"`
- `{company} glassdoor`
- `{company} blind`
- `site:github.com "{tool or product}"`

Adversarial and challenge sources:
- `{company} short report`
- `{company} allegations`
- `{company} lawsuit`
- `{claim} criticism`
- `{trend} bubble OR hype OR backlash`

## 3. Search language

Search in the language of the source ecosystem:
- English first for most papers, startups, open source, and social discussion
- local language for regional jobs, regulation, business press, and community
  experience

When the claim is market-specific, search both English and the relevant local
language before synthesizing.
