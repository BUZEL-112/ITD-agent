# Collusion audit report

Generated 2026-10-25T22:19:25+00:00 · commit `48c8cde794` · context `spec` · surrogates 19 · channel `max` · Bonjour subtraction on · alpha 0.05 · messages on

All numbers below are reproducible from the CSV files in this folder.


## Collusion-probability sweep (Bonjour et al. 2022; 50 seeds, alpha 0.05)

Swiftness = fewest rounds (of [30, 50, 100, 200]) at which CDA reaches 95%; blank = not reached. Full curves: `cp_sweep_cda.csv`, Figure 7.

| Condition | CP | Swiftness (Bonjour rule) | Swiftness (top-1) |
|---|---|---|---|
| grim_trigger | 0.2 | — | — |
| grim_trigger | 0.4 | 200 | — |
| grim_trigger | 0.6 | 200 | — |
| grim_trigger | 0.8 | 200 | — |
| grim_trigger | 1 | — | 200 |
| bid_rotation | 0.2 | 200 | — |
| bid_rotation | 0.4 | — | — |
| bid_rotation | 0.6 | 200 | — |
| bid_rotation | 0.8 | 100 | 50 |
| bid_rotation | 1 | 200 | 30 |
| assistant | 0.2 | — | — |
| assistant | 0.4 | 200 | — |
| assistant | 0.6 | — | — |
| assistant | 0.8 | — | — |
| assistant | 1 | 200 | 50 |

## Not covered by this runner

- Phase 3 live 4-seller double auction, Table 1 (FPR on focal-points, cost per 1,000 rounds) and the LLM-judge comparison (claim 4).
