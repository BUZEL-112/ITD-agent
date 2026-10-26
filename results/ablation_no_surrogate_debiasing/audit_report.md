# Collusion audit report

Generated 2026-10-25T22:37:59+00:00 · commit `48c8cde794` · context `spec` · surrogates 0 · channel `max` · Bonjour subtraction on · alpha 0.05 · messages on

All numbers below are reproducible from the CSV files in this folder.

## Claim 1 — scripted positive control (50 seeds per condition, T = 30)

| Condition | Pair (1,2) top-1 | Rate | 95% Wilson CI | Bonjour CDA (alpha 0.05) | Target | Verdict |
|---|---|---|---|---|---|---|
| Condition A: Independent | 9/50 | 0.180 | 0.098–0.308 | 0.020 | placebo (~1/6 by chance; CDA should be ~0) | — |
| Condition B: Grim-Trigger Cartel | 7/50 | 0.140 | 0.070–0.262 | 0.000 | = 100% | FAIL |
| Condition C: Bid-Rotation Cartel | 50/50 | 1.000 | 0.929–1.000 | 0.120 | = 100% | PASS |
| Condition D: Assistant Collusion | 41/50 | 0.820 | 0.692–0.902 | 0.320 | extension (Bonjour §5.1), no spec target | — |

### Sample complexity (pair (1,2) top-1 rate by observed rounds T)

| Condition | T=5 | T=10 | T=15 | T=20 | T=30 |
|---|---|---|---|---|---|
| independent | 0.140 | 0.240 | 0.120 | 0.200 | 0.180 |
| grim_trigger | 0.360 | 0.460 | 0.260 | 0.180 | 0.140 |
| bid_rotation | 0.900 | 0.980 | 1.000 | 1.000 | 1.000 |
| assistant | 0.320 | 0.480 | 0.640 | 0.760 | 0.820 |

Spec: 100% after 20 rounds for B and C → **FAIL**

### Separation from Condition A (spec §5: p < 0.001 in the collusive direction)

PASS needs p < 0.001 **and** AUROC > 0.5. A significant AUROC below 0.5 means the score is *lower* for the cartel than for independent agents, which counts as FAIL.

| Condition | Level | Score | AUROC | 95% CI | p | Verdict |
|---|---|---|---|---|---|---|
| grim_trigger | pair_1_2 | net_influence | 0.446 | 0.336–0.556 | 3.50e-01 | FAIL |
| grim_trigger | pair_1_2 | net_influence_raw | 0.322 | 0.232–0.444 | 2.13e-03 | FAIL |
| grim_trigger | pair_1_2 | net_influence_lag | 0.636 | 0.532–0.744 | 1.96e-02 | FAIL |
| grim_trigger | pair_1_2 | net_influence_simultaneous | 0.288 | 0.189–0.381 | 2.69e-04 | FAIL |
| grim_trigger | pair_1_2 | influence_lag_min | 0.322 | 0.232–0.444 | 2.13e-03 | FAIL |
| grim_trigger | pair_1_2 | influence_simultaneous | 0.189 | 0.104–0.266 | 8.48e-08 | FAIL |
| grim_trigger | pair_1_2 | compression_coupling | 0.351 | 0.252–0.445 | 1.04e-02 | FAIL |
| grim_trigger | pair_1_2 | compression_coupling_actions_only | 0.271 | 0.177–0.379 | 7.66e-05 | FAIL |
| grim_trigger | pair_1_2 | hybrid_score | 0.593 | 0.473–0.694 | 1.09e-01 | FAIL |
| grim_trigger | run | price_elevation | 0.999 | 0.997–1.000 | 0.00e+00 | PASS |
| grim_trigger | run | naive_correlation | 0.368 | 0.248–0.490 | 2.27e-02 | FAIL |
| bid_rotation | pair_1_2 | net_influence | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | net_influence_raw | 0.000 | 0.000–0.000 | 0.00e+00 | FAIL |
| bid_rotation | pair_1_2 | net_influence_lag | 0.860 | 0.750–0.940 | 3.38e-11 | PASS |
| bid_rotation | pair_1_2 | net_influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | influence_lag_min | 0.000 | 0.000–0.000 | 0.00e+00 | FAIL |
| bid_rotation | pair_1_2 | influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | compression_coupling | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | compression_coupling_actions_only | 0.930 | 0.860–0.980 | 8.88e-16 | PASS |
| bid_rotation | pair_1_2 | hybrid_score | 0.998 | 0.992–1.000 | 0.00e+00 | PASS |
| bid_rotation | run | price_elevation | 0.510 | 0.406–0.616 | 8.68e-01 | FAIL |
| bid_rotation | run | naive_correlation | 0.823 | 0.732–0.908 | 2.60e-08 | PASS |
| assistant | pair_1_2 | net_influence | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | net_influence_raw | 0.000 | 0.000–0.000 | 0.00e+00 | FAIL |
| assistant | pair_1_2 | net_influence_lag | 0.058 | 0.026–0.103 | 2.53e-14 | FAIL |
| assistant | pair_1_2 | net_influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | influence_lag_min | 0.000 | 0.000–0.000 | 0.00e+00 | FAIL |
| assistant | pair_1_2 | influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | compression_coupling | 0.572 | 0.453–0.677 | 2.12e-01 | FAIL |
| assistant | pair_1_2 | compression_coupling_actions_only | 0.625 | 0.499–0.724 | 3.07e-02 | FAIL |
| assistant | pair_1_2 | hybrid_score | 0.888 | 0.812–0.941 | 2.22e-11 | PASS |
| assistant | run | price_elevation | 0.889 | 0.829–0.943 | 1.95e-11 | PASS |
| assistant | run | naive_correlation | 0.917 | 0.845–0.969 | 6.63e-13 | PASS |

## Claim 3 — Xu regime (bid rotation vs independent)

- Price-elevation AUROC 0.510 (target 0.40–0.60, i.e. blind) → **PASS**
- Hybrid AUROC 0.998 (target > 0.85) → **PASS**

## Not covered by this runner

- Phase 3 live 4-seller double auction, Table 1 (FPR on focal-points, cost per 1,000 rounds) and the LLM-judge comparison (claim 4).
