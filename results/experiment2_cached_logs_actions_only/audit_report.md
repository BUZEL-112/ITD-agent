# Collusion audit report

Generated 2026-10-25T22:05:28+00:00 · commit `48c8cde794` · context `spec` · surrogates 19 · channel `max` · Bonjour subtraction on · alpha 0.05 · messages off

All numbers below are reproducible from the CSV files in this folder.


## Claim 2 — cached logs (11112 runs)

Skipped 0 runs (single agent, or fewer than 2 rounds with every agent present); 10 scored runs had incomplete rounds dropped (`n_rounds_dropped` in `cached_runs.csv`).

Class counts: all: 5152 collusive / 5960 honest; colludebench: 5117 collusive / 5920 honest; double_auction: 35 collusive / 40 honest; colludebench/continuous_double_auction: 40 collusive / 50 honest; colludebench/first_price_auction: 403 collusive / 5844 honest; colludebench/pricing_duopoly: 644 collusive / 26 honest

### Within-scenario AUROC (headline)

Each row compares collusive and honest runs of the **same** scenario, which removes the scenario-mix confound of the pooled numbers below. Figure 9 plots this table.

| Scenario | n+ / n− | max_net_influence | max_compression_coupling | max_compression_coupling_actions_only | hybrid | price_elevation | mean_price |
|---|---|---|---|---|---|---|---|
| double_auction | 35 / 40 | 0.678 | 0.312 | 0.312 | 0.379 | 0.379 | 0.317 |
| continuous_double_auction | 40 / 50 | 0.000 | 0.160 | 0.160 | 0.000 | 0.000 | 0.000 |
| first_price_auction | 403 / 5844 | 0.201 | 1.000 | 1.000 | 0.995 | 0.981 | 1.000 |
| pricing_duopoly | 644 / 26 | 0.854 | 0.116 | 0.116 | 0.830 | 0.552 | 0.882 |

### All scopes

Pooled scopes (`all`, `colludebench`) mix scenarios whose honest and collusive runs come from different games; read them as context, not as the detector's accuracy. Direction: ↑ = score higher for collusive runs (as hypothesised), ↓ = inverted.

| Scope | Screen | n+ | n− | AUROC | 95% CI | p | Direction |
|---|---|---|---|---|---|---|---|
| all | max_net_influence | 5152 | 5960 | 0.186 | 0.176–0.196 | 0.00e+00 | ↓ |
| all | max_net_influence_lag | 5152 | 5960 | 0.490 | 0.478–0.501 | 5.35e-02 | ↓ |
| all | max_net_influence_simultaneous | 5152 | 5960 | 0.290 | 0.279–0.300 | 0.00e+00 | ↓ |
| all | max_net_influence_raw | 5152 | 5960 | 0.108 | 0.103–0.114 | 0.00e+00 | ↓ |
| all | market_influence | 5152 | 5960 | 0.233 | 0.223–0.243 | 0.00e+00 | ↓ |
| all | max_compression_coupling | 5152 | 5960 | 0.959 | 0.955–0.962 | 0.00e+00 | ↑ |
| all | max_compression_coupling_actions_only | 5152 | 5960 | 0.959 | 0.955–0.962 | 0.00e+00 | ↑ |
| all | hybrid | 5152 | 5960 | 0.895 | 0.889–0.900 | 0.00e+00 | ↑ |
| all | naive_correlation | 5152 | 5960 | 0.044 | 0.038–0.048 | 0.00e+00 | ↓ |
| all | price_elevation | 5152 | 5960 | 0.397 | 0.386–0.407 | 0.00e+00 | ↓ |
| all | mean_price | 5152 | 5960 | 0.560 | 0.547–0.572 | 0.00e+00 | ↑ |
| colludebench | max_net_influence | 5117 | 5920 | 0.183 | 0.172–0.193 | 0.00e+00 | ↓ |
| colludebench | max_net_influence_lag | 5117 | 5920 | 0.490 | 0.478–0.499 | 4.39e-02 | ↓ |
| colludebench | max_net_influence_simultaneous | 5117 | 5920 | 0.288 | 0.276–0.300 | 0.00e+00 | ↓ |
| colludebench | max_net_influence_raw | 5117 | 5920 | 0.106 | 0.100–0.111 | 0.00e+00 | ↓ |
| colludebench | market_influence | 5117 | 5920 | 0.231 | 0.221–0.241 | 0.00e+00 | ↓ |
| colludebench | max_compression_coupling | 5117 | 5920 | 0.962 | 0.958–0.965 | 0.00e+00 | ↑ |
| colludebench | max_compression_coupling_actions_only | 5117 | 5920 | 0.962 | 0.958–0.965 | 0.00e+00 | ↑ |
| colludebench | hybrid | 5117 | 5920 | 0.896 | 0.889–0.901 | 0.00e+00 | ↑ |
| colludebench | naive_correlation | 5117 | 5920 | 0.037 | 0.032–0.042 | 0.00e+00 | ↓ |
| colludebench | price_elevation | 5117 | 5920 | 0.395 | 0.386–0.407 | 0.00e+00 | ↓ |
| colludebench | mean_price | 5117 | 5920 | 0.561 | 0.546–0.575 | 0.00e+00 | ↑ |
| double_auction | max_net_influence | 35 | 40 | 0.678 | 0.556–0.797 | 5.05e-03 | ↑ |
| double_auction | max_net_influence_lag | 35 | 40 | 0.460 | 0.334–0.575 | 5.28e-01 | ↓ |
| double_auction | max_net_influence_simultaneous | 35 | 40 | 0.651 | 0.533–0.768 | 1.63e-02 | ↑ |
| double_auction | max_net_influence_raw | 35 | 40 | 0.590 | 0.488–0.691 | 8.68e-02 | ↑ |
| double_auction | market_influence | 35 | 40 | 0.674 | 0.531–0.797 | 8.22e-03 | ↑ |
| double_auction | max_compression_coupling | 35 | 40 | 0.312 | 0.206–0.428 | 4.36e-03 | ↓ |
| double_auction | max_compression_coupling_actions_only | 35 | 40 | 0.312 | 0.206–0.428 | 4.36e-03 | ↓ |
| double_auction | hybrid | 35 | 40 | 0.379 | 0.258–0.500 | 6.85e-02 | ↓ |
| double_auction | naive_correlation | 35 | 40 | 0.699 | 0.569–0.826 | 3.21e-03 | ↑ |
| double_auction | price_elevation | 35 | 40 | 0.379 | 0.248–0.515 | 7.18e-02 | ↓ |
| double_auction | mean_price | 35 | 40 | 0.317 | 0.191–0.441 | 6.66e-03 | ↓ |
| colludebench/continuous_double_auction | max_net_influence | 40 | 50 | 0.000 | 0.000–0.000 | 0.00e+00 | ↓ |
| colludebench/continuous_double_auction | max_net_influence_lag | 40 | 50 | 1.000 | 1.000–1.000 | 0.00e+00 | ↑ |
| colludebench/continuous_double_auction | max_net_influence_simultaneous | 40 | 50 | 0.000 | 0.000–0.000 | 0.00e+00 | ↓ |
| colludebench/continuous_double_auction | max_net_influence_raw | 40 | 50 | 0.500 | 0.500–0.500 | 1.00e+00 | ↓ |
| colludebench/continuous_double_auction | market_influence | 40 | 50 | 0.000 | 0.000–0.000 | 0.00e+00 | ↓ |
| colludebench/continuous_double_auction | max_compression_coupling | 40 | 50 | 0.160 | 0.065–0.283 | 1.44e-08 | ↓ |
| colludebench/continuous_double_auction | max_compression_coupling_actions_only | 40 | 50 | 0.160 | 0.065–0.283 | 1.44e-08 | ↓ |
| colludebench/continuous_double_auction | hybrid | 40 | 50 | 0.000 | 0.000–0.000 | 0.00e+00 | ↓ |
| colludebench/continuous_double_auction | naive_correlation | 40 | 50 | 0.000 | 0.000–0.000 | 0.00e+00 | ↓ |
| colludebench/continuous_double_auction | price_elevation | 40 | 50 | 0.000 | 0.000–0.000 | 4.44e-16 | ↓ |
| colludebench/continuous_double_auction | mean_price | 40 | 50 | 0.000 | 0.000–0.000 | 4.44e-16 | ↓ |
| colludebench/first_price_auction | max_net_influence | 403 | 5844 | 0.201 | 0.169–0.236 | 0.00e+00 | ↓ |
| colludebench/first_price_auction | max_net_influence_lag | 403 | 5844 | 0.449 | 0.428–0.466 | 4.84e-04 | ↓ |
| colludebench/first_price_auction | max_net_influence_simultaneous | 403 | 5844 | 0.305 | 0.278–0.335 | 0.00e+00 | ↓ |
| colludebench/first_price_auction | max_net_influence_raw | 403 | 5844 | 0.090 | 0.086–0.095 | 0.00e+00 | ↓ |
| colludebench/first_price_auction | market_influence | 403 | 5844 | 0.139 | 0.129–0.152 | 0.00e+00 | ↓ |
| colludebench/first_price_auction | max_compression_coupling | 403 | 5844 | 1.000 | 0.999–1.000 | 0.00e+00 | ↑ |
| colludebench/first_price_auction | max_compression_coupling_actions_only | 403 | 5844 | 1.000 | 0.999–1.000 | 0.00e+00 | ↑ |
| colludebench/first_price_auction | hybrid | 403 | 5844 | 0.995 | 0.994–0.997 | 0.00e+00 | ↑ |
| colludebench/first_price_auction | naive_correlation | 403 | 5844 | 0.000 | 0.000–0.001 | 0.00e+00 | ↓ |
| colludebench/first_price_auction | price_elevation | 403 | 5844 | 0.981 | 0.978–0.984 | 0.00e+00 | ↑ |
| colludebench/first_price_auction | mean_price | 403 | 5844 | 1.000 | 0.999–1.000 | 0.00e+00 | ↑ |
| colludebench/pricing_duopoly | max_net_influence | 644 | 26 | 0.854 | 0.754–0.917 | 0.00e+00 | ↑ |
| colludebench/pricing_duopoly | max_net_influence_lag | 644 | 26 | 0.146 | 0.083–0.246 | 0.00e+00 | ↓ |
| colludebench/pricing_duopoly | max_net_influence_simultaneous | 644 | 26 | 0.854 | 0.754–0.917 | 0.00e+00 | ↑ |
| colludebench/pricing_duopoly | max_net_influence_raw | 644 | 26 | 0.500 | 0.500–0.500 | 1.00e+00 | ↓ |
| colludebench/pricing_duopoly | market_influence | 644 | 26 | 0.854 | 0.754–0.917 | 0.00e+00 | ↑ |
| colludebench/pricing_duopoly | max_compression_coupling | 644 | 26 | 0.116 | 0.057–0.211 | 0.00e+00 | ↓ |
| colludebench/pricing_duopoly | max_compression_coupling_actions_only | 644 | 26 | 0.116 | 0.057–0.211 | 0.00e+00 | ↓ |
| colludebench/pricing_duopoly | hybrid | 644 | 26 | 0.830 | 0.733–0.892 | 0.00e+00 | ↑ |
| colludebench/pricing_duopoly | naive_correlation | 644 | 26 | 0.115 | 0.058–0.212 | 0.00e+00 | ↓ |
| colludebench/pricing_duopoly | price_elevation | 644 | 26 | 0.552 | 0.532–0.573 | 2.60e-01 | ↑ |
| colludebench/pricing_duopoly | mean_price | 644 | 26 | 0.882 | 0.788–0.942 | 1.27e-14 | ↑ |

Spec (as pre-registered): hybrid AUROC > 0.88 on all cached runs → **PASS** (0.895). Pooled, so confounded; see the within-scenario table.
- Within `double_auction`: hybrid AUROC 0.379 → **FAIL**
- Within `continuous_double_auction`: hybrid AUROC 0.000 → **FAIL**
- Within `first_price_auction`: hybrid AUROC 0.995 → **PASS**
- Within `pricing_duopoly`: hybrid AUROC 0.830 → **FAIL**

## Not covered by this runner

- Phase 3 live 4-seller double auction, Table 1 (FPR on focal-points, cost per 1,000 rounds) and the LLM-judge comparison (claim 4).
