# Scenario results: scenario_1

## System metrics
|                                 |    value |
|:--------------------------------|---------:|
| solo_total_cost_eur             |  7.50984 |
| coalition_total_cost_eur        |  6.20958 |
| total_savings_vN_eur            |  1.30027 |
| peak_import_solo_kwh_per_h      |  5.92254 |
| peak_import_coal_kwh_per_h      |  5.13393 |
| peak_import_reduction_kwh_per_h |  0.78861 |
| peak_import_reduction_pct       | 13.3154  |
| self_consumption_solo_pct       | 37.2846  |
| self_consumption_coal_pct       | 88.7951  |
| self_consumption_increase_pct   | 51.5105  |
| total_pv_kwh                    | 37.6658  |
| total_load_kwh                  | 77.5165  |

## Allocation table (EUR)
|    |   shapley |   equal_split |   pv_proportional |   contribution_proportional |   least_core |
|:---|----------:|--------------:|------------------:|----------------------------:|-------------:|
| H1 |  0.334549 |      0.260053 |          0.694671 |                    0.575194 |    0.234808  |
| H2 |  0.469433 |      0.260053 |          0        |                    0.261604 |    0.617944  |
| H3 |  0.250576 |      0.260053 |          0.605594 |                    0.463468 |    0.188467  |
| H4 |  0.101155 |      0.260053 |          0        |                    0        |    0.0651065 |
| H5 |  0.144551 |      0.260053 |          0        |                    0        |    0.19394   |

## Stability summary
|                           |   blocking_coalitions_count |   worst_deficit |   in_core |
|:--------------------------|----------------------------:|----------------:|----------:|
| shapley                   |                           1 |     0.000131109 |         0 |
| equal_split               |                           7 |     0.284007    |         0 |
| pv_proportional           |                          11 |     0.219393    |         0 |
| contribution_proportional |                           5 |     0.0772659   |         0 |
| least_core                |                           0 |     0           |         1 |