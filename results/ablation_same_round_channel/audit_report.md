# Collusion audit report

Generated 2026-10-25T22:39:06+00:00 · commit `48c8cde794` · context `spec` · surrogates 19 · channel `simultaneous` · Bonjour subtraction on · alpha 0.05 · messages on

All numbers below are reproducible from the CSV files in this folder.

## Claim 1 — scripted positive control (50 seeds per condition, T = 30)

| Condition | Pair (1,2) top-1 | Rate | 95% Wilson CI | Bonjour CDA (alpha 0.05) | Target | Verdict |
|---|---|---|---|---|---|---|
| Condition A: Independent | 9/50 | 0.180 | 0.098–0.308 | 0.040 | placebo (~1/6 by chance; CDA should be ~0) | — |
| Condition B: Grim-Trigger Cartel | 8/50 | 0.160 | 0.083–0.285 | 0.100 | = 100% | FAIL |
| Condition C: Bid-Rotation Cartel | 50/50 | 1.000 | 0.929–1.000 | 0.800 | = 100% | PASS |
| Condition D: Assistant Collusion | 32/50 | 0.640 | 0.501–0.759 | 0.820 | extension (Bonjour §5.1), no spec target | — |

### Sample complexity (pair (1,2) top-1 rate by observed rounds T)

| Condition | T=5 | T=10 | T=15 | T=20 | T=30 |
|---|---|---|---|---|---|
| independent | 0.160 | 0.220 | 0.160 | 0.180 | 0.180 |
| grim_trigger | 0.580 | 0.560 | 0.440 | 0.220 | 0.160 |
| bid_rotation | 0.900 | 0.980 | 1.000 | 1.000 | 1.000 |
| assistant | 0.380 | 0.580 | 0.520 | 0.640 | 0.640 |

Spec: 100% after 20 rounds for B and C → **FAIL**

### Separation from Condition A (spec §5: p < 0.001 in the collusive direction)

PASS needs p < 0.001 **and** AUROC > 0.5. A significant AUROC below 0.5 means the score is *lower* for the cartel than for independent agents, which counts as FAIL.

| Condition | Level | Score | AUROC | 95% CI | p | Verdict |
|---|---|---|---|---|---|---|
| grim_trigger | pair_1_2 | net_influence | 0.483 | 0.375–0.590 | 7.75e-01 | FAIL |
| grim_trigger | pair_1_2 | net_influence_raw | 0.322 | 0.232–0.444 | 2.13e-03 | FAIL |
| grim_trigger | pair_1_2 | net_influence_lag | 0.839 | 0.754–0.910 | 5.36e-09 | PASS |
| grim_trigger | pair_1_2 | net_influence_simultaneous | 0.483 | 0.375–0.590 | 7.75e-01 | FAIL |
| grim_trigger | pair_1_2 | influence_lag_min | 0.862 | 0.795–0.930 | 4.50e-10 | PASS |
| grim_trigger | pair_1_2 | influence_simultaneous | 0.407 | 0.289–0.508 | 1.09e-01 | FAIL |
| grim_trigger | pair_1_2 | compression_coupling | 0.351 | 0.252–0.445 | 1.04e-02 | FAIL |
| grim_trigger | pair_1_2 | compression_coupling_actions_only | 0.271 | 0.177–0.379 | 7.66e-05 | FAIL |
| grim_trigger | pair_1_2 | hybrid_score | 0.586 | 0.461–0.687 | 1.39e-01 | FAIL |
| grim_trigger | run | price_elevation | 0.999 | 0.997–1.000 | 0.00e+00 | PASS |
| grim_trigger | run | naive_correlation | 0.368 | 0.248–0.490 | 2.27e-02 | FAIL |
| bid_rotation | pair_1_2 | net_influence | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | net_influence_raw | 0.000 | 0.000–0.000 | 0.00e+00 | FAIL |
| bid_rotation | pair_1_2 | net_influence_lag | 0.940 | 0.860–1.000 | 4.44e-16 | PASS |
| bid_rotation | pair_1_2 | net_influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | influence_lag_min | 0.740 | 0.620–0.871 | 9.96e-06 | PASS |
| bid_rotation | pair_1_2 | influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | compression_coupling | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | compression_coupling_actions_only | 0.930 | 0.860–0.980 | 8.88e-16 | PASS |
| bid_rotation | pair_1_2 | hybrid_score | 1.000 | 0.998–1.000 | 0.00e+00 | PASS |
| bid_rotation | run | price_elevation | 0.510 | 0.406–0.616 | 8.68e-01 | FAIL |
| bid_rotation | run | naive_correlation | 0.823 | 0.732–0.908 | 2.60e-08 | PASS |
| assistant | pair_1_2 | net_influence | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | net_influence_raw | 0.000 | 0.000–0.000 | 0.00e+00 | FAIL |
| assistant | pair_1_2 | net_influence_lag | 0.028 | 0.010–0.055 | 4.44e-16 | FAIL |
| assistant | pair_1_2 | net_influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | influence_lag_min | 0.001 | 0.000–0.005 | 0.00e+00 | FAIL |
| assistant | pair_1_2 | influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | compression_coupling | 0.572 | 0.453–0.677 | 2.12e-01 | FAIL |
| assistant | pair_1_2 | compression_coupling_actions_only | 0.625 | 0.499–0.724 | 3.07e-02 | FAIL |
| assistant | pair_1_2 | hybrid_score | 0.856 | 0.764–0.917 | 9.06e-10 | PASS |
| assistant | run | price_elevation | 0.889 | 0.829–0.943 | 1.95e-11 | PASS |
| assistant | run | naive_correlation | 0.917 | 0.845–0.969 | 6.63e-13 | PASS |

## Claim 3 — Xu regime (bid rotation vs independent)

- Price-elevation AUROC 0.510 (target 0.40–0.60, i.e. blind) → **PASS**
- Hybrid AUROC 1.000 (target > 0.85) → **PASS**

## Not covered by this runner

- Phase 3 live 4-seller double auction, Table 1 (FPR on focal-points, cost per 1,000 rounds) and the LLM-judge comparison (claim 4).
