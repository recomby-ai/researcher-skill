# Scientific Literature Traversal

Load this file when the topic depends on papers, technical reports, benchmarks,
or citation-graph traversal.

## 1. Map phase defaults

For scientific and technical topics, the map phase should usually look for:
- latest available review, survey, tutorial, benchmark, perspective, or field
  overview
- recent representative papers
- foundational or defining papers
- benchmarks, datasets, evaluation protocols, or standards
- criticism, limitation, replication, or alternative approaches

Do not hard-code a one-year or two-year window unless the user asks for one.
"Latest" means newest relevant material available in that field.

If no formal review exists, fall back to the best overview substitute:
- tutorial
- benchmark paper
- perspective
- workshop survey
- field overview from a reputable venue

## 2. Graph jumps

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
- review or survey -> repeatedly cited original paper
- recent paper -> cited baselines, appendix, code, or benchmark
- benchmark paper -> dataset definition, metric definition, reproducibility
  notes
- criticism paper -> criticized paper and any response or rebuttal
- lab or author -> project page, official repo, talk, or technical report

## 3. Primary-source completion

For important claims, do not stop at the overview layer. Follow enough of the
graph to reach:
- original paper
- appendix or supplementary material
- code or project page when the claim depends on implementation details
- dataset or benchmark documentation when the claim depends on evaluation

If a primary source cannot be located, say so explicitly.
