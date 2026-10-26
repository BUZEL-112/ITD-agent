# Collusion audit report

Generated 2026-10-25T22:37:50+00:00 · commit `48c8cde794` · context `compound` · surrogates 0 · channel `max` · Bonjour subtraction on · alpha 0.05 · messages on

All numbers below are reproducible from the CSV files in this folder.

## Claim 1 — scripted positive control (50 seeds per condition, T = 30)

| Condition | Pair (1,2) top-1 | Rate | 95% Wilson CI | Bonjour CDA (alpha 0.05) | Target | Verdict |
|---|---|---|---|---|---|---|
| Condition A: Independent | 8/50 | 0.160 | 0.083–0.285 | 0.100 | placebo (~1/6 by chance; CDA should be ~0) | — |
| Condition B: Grim-Trigger Cartel | 4/50 | 0.080 | 0.032–0.188 | 0.020 | = 100% | FAIL |
| Condition C: Bid-Rotation Cartel | 50/50 | 1.000 | 0.929–1.000 | 0.020 | = 100% | PASS |
| Condition D: Assistant Collusion | 31/50 | 0.620 | 0.482–0.741 | 0.020 | extension (Bonjour §5.1), no spec target | — |

### Sample complexity (pair (1,2) top-1 rate by observed rounds T)

| Condition | T=5 | T=10 | T=15 | T=20 | T=30 |
|---|---|---|---|---|---|
| independent | 0.160 | 0.260 | 0.100 | 0.160 | 0.160 |
| grim_trigger | 0.460 | 0.400 | 0.340 | 0.160 | 0.080 |
| bid_rotation | 0.800 | 0.920 | 1.000 | 0.980 | 1.000 |
| assistant | 0.260 | 0.320 | 0.420 | 0.580 | 0.620 |

Spec: 100% after 20 rounds for B and C → **FAIL**

### Separation from Condition A (spec §5: p < 0.001 in the collusive direction)

PASS needs p < 0.001 **and** AUROC > 0.5. A significant AUROC below 0.5 means the score is *lower* for the cartel than for independent agents, which counts as FAIL.

| Condition | Level | Score | AUROC | 95% CI | p | Verdict |
|---|---|---|---|---|---|---|
| grim_trigger | pair_1_2 | net_influence | 0.599 | 0.475–0.705 | 8.93e-02 | FAIL |
| grim_trigger | pair_1_2 | net_influence_raw | 0.144 | 0.076–0.216 | 8.30e-10 | FAIL |
| grim_trigger | pair_1_2 | net_influence_lag | 0.742 | 0.644–0.832 | 3.18e-05 | PASS |
| grim_trigger | pair_1_2 | net_influence_simultaneous | 0.399 | 0.294–0.499 | 8.30e-02 | FAIL |
| grim_trigger | pair_1_2 | influence_lag_min | 0.144 | 0.076–0.216 | 8.30e-10 | FAIL |
| grim_trigger | pair_1_2 | influence_simultaneous | 0.038 | 0.011–0.077 | 1.78e-15 | FAIL |
| grim_trigger | pair_1_2 | compression_coupling | 0.351 | 0.252–0.445 | 1.04e-02 | FAIL |
| grim_trigger | pair_1_2 | compression_coupling_actions_only | 0.271 | 0.177–0.379 | 7.66e-05 | FAIL |
| grim_trigger | pair_1_2 | hybrid_score | 0.652 | 0.531–0.754 | 9.07e-03 | FAIL |
| grim_trigger | run | price_elevation | 0.999 | 0.997–1.000 | 0.00e+00 | PASS |
| grim_trigger | run | naive_correlation | 0.368 | 0.248–0.490 | 2.27e-02 | FAIL |
| bid_rotation | pair_1_2 | net_influence | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | net_influence_raw | 0.964 | 0.930–0.990 | 1.33e-15 | PASS |
| bid_rotation | pair_1_2 | net_influence_lag | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | net_influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | influence_lag_min | 0.964 | 0.930–0.990 | 1.33e-15 | PASS |
| bid_rotation | pair_1_2 | influence_simultaneous | 0.893 | 0.821–0.949 | 1.32e-11 | PASS |
| bid_rotation | pair_1_2 | compression_coupling | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| bid_rotation | pair_1_2 | compression_coupling_actions_only | 0.930 | 0.860–0.980 | 8.88e-16 | PASS |
| bid_rotation | pair_1_2 | hybrid_score | 0.983 | 0.947–1.000 | 0.00e+00 | PASS |
| bid_rotation | run | price_elevation | 0.510 | 0.406–0.616 | 8.68e-01 | FAIL |
| bid_rotation | run | naive_correlation | 0.823 | 0.732–0.908 | 2.60e-08 | PASS |
| assistant | pair_1_2 | net_influence | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | net_influence_raw | 0.594 | 0.477–0.698 | 1.05e-01 | FAIL |
| assistant | pair_1_2 | net_influence_lag | 0.665 | 0.551–0.752 | 4.46e-03 | FAIL |
| assistant | pair_1_2 | net_influence_simultaneous | 1.000 | 1.000–1.000 | 0.00e+00 | PASS |
| assistant | pair_1_2 | influence_lag_min | 0.594 | 0.477–0.698 | 1.05e-01 | FAIL |
| assistant | pair_1_2 | influence_simultaneous | 0.975 | 0.938–0.996 | 4.44e-16 | PASS |
| assistant | pair_1_2 | compression_coupling | 0.572 | 0.453–0.677 | 2.12e-01 | FAIL |
| assistant | pair_1_2 | compression_coupling_actions_only | 0.625 | 0.499–0.724 | 3.07e-02 | FAIL |
| assistant | pair_1_2 | hybrid_score | 0.871 | 0.785–0.932 | 1.69e-10 | PASS |
| assistant | run | price_elevation | 0.889 | 0.829–0.943 | 1.95e-11 | PASS |
| assistant | run | naive_correlation | 0.917 | 0.845–0.969 | 6.63e-13 | PASS |

## Claim 3 — Xu regime (bid rotation vs independent)

- Price-elevation AUROC 0.510 (target 0.40–0.60, i.e. blind) → **PASS**
- Hybrid AUROC 0.983 (target > 0.85) → **PASS**

## Not covered by this runner

- Phase 3 live 4-seller double auction, Table 1 (FPR on focal-points, cost per 1,000 rounds) and the LLM-judge comparison (claim 4).
