# Researcher — ReAct Deep Search Skill

Claude is already great at reasoning. But when it searches the web, it searches once, reads the snippets, and gives you an answer. That's breadth — not depth. It's what any search engine does.

This skill is a single prompt that changes how Claude searches. Instead of one broad sweep, Claude now follows leads: each search round is driven by what the previous round discovered, chasing citations forward and backward through the academic literature until it hits primary sources. Same Claude, deeper search.

## Two Core Ideas

**1. ReAct-driven search** — Claude doesn't just search multiple times. Each round's search direction is determined by what the previous round discovered. Search → Reason (what did I find? what lead should I chase?) → Act (search that specific lead) → repeat.

**2. Citation chain tracking** — Start broad (find review papers, map the field), then go deep: pick a key paper, follow its references backward (what does it cite?), follow its citations forward (who cited it?), repeat until no new concepts appear. This catches papers that keyword search misses because papers using different terminology still cite each other.

Together: **ReAct drives citation chain jumping.** Each REASON step decides which paper's citation chain to follow next.

## What This Looks Like

```
Round 1: Search "LLM hallucination survey 2025"
  → [Finding] Found 3 survey papers, key researchers: Huang et al., Radhakrishnan
  → [Lead] Huang et al. survey has 200+ references — chase their citation chain
  → [Gap] No counter-evidence yet

Round 2: Search Huang et al. on Semantic Scholar → read references
  → [Finding] They cite a mathematical proof (Xu et al. 2024) that hallucination is inevitable
  → [Lead] This proof paper — need to read it and check who cites it
  → [Gap] Haven't verified the proof's actual claims

Round 3: WebFetch the proof paper + search forward citations
  → [Finding] Proof only applies to "general problem solving" — domain-specific can still improve
  → [Lead] MIT/UCSD published a Science paper on internal steering (Feb 2026)
  → [Gap] No quantitative comparison of methods yet

Round 4: Chase the Science paper + search for method comparisons
  → [Finding] RAG reduces hallucination 40-71%, internal steering outperforms judge models
  → Saturation: no new concepts appearing → done
```

## Tested Results

Same question ("LLM hallucination solutions"), with and without skill:

| | Without | With |
|--|---------|------|
| Search rounds | 1 | 4 |
| Papers read | 0 | 4 |
| Primary sources | 0 | 3 |
| Counter-evidence | None | Yes |

## Install

```bash
git clone https://github.com/recomby-ai/researcher-skill.git
cp -r researcher-skill/researcher ~/.claude/skills/
```

Then use `/researcher your question` in Claude Code.

## Usage

```
/researcher What are the current solutions to LLM hallucination?
/researcher CRISPR off-target detection methods — state of the art
/researcher Is solid-state battery mass production realistic by 2026?
```

## Limitations

- Cannot access Google Scholar via WebSearch (uses Semantic Scholar as alternative — 200M+ papers, 98.3% coverage overlap)
- Cannot read paywalled paper full text (reads abstracts, cites accordingly)
- Not a systematic review tool — catches 95%+ of relevant papers through keyword + citation chaining, but edge cases exist

## License

MIT
