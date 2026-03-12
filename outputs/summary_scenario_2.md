# Scenario results: scenario_2

## System metrics
|                                 |    value |
|:--------------------------------|---------:|
| solo_total_cost_eur             |  8.90328 |
| coalition_total_cost_eur        |  6.3041  |
| total_savings_vN_eur            |  2.59918 |
| peak_import_solo_kwh_per_h      | 10.3245  |
| peak_import_coal_kwh_per_h      |  9.317   |
| peak_import_reduction_kwh_per_h |  1.00755 |
| peak_import_reduction_pct       |  9.75881 |
| self_consumption_solo_pct       | 37.4818  |
| self_consumption_coal_pct       | 88.1361  |
| self_consumption_increase_pct   | 50.6543  |
| total_pv_kwh                    | 64.2069  |
| total_load_kwh                  | 98.9041  |

## Allocation table (EUR)
|    |   shapley |   equal_split |   pv_proportional |   contribution_proportional |   least_core |
|:---|----------:|--------------:|------------------:|----------------------------:|-------------:|
| H1 |  0.271872 |      0.324897 |          0.783353 |                    0.547014 |    0.0717488 |
| H2 |  0.298554 |      0.324897 |          0        |                    0.184178 |    0.418826  |
| H3 |  0.183551 |      0.324897 |          0.564311 |                    0.327765 |    0.0652905 |
| H4 |  0.545734 |      0.324897 |          0        |                    0.238676 |    0.783752  |
| H5 |  0.207463 |      0.324897 |          0.567221 |                    0.434508 |    0.0599653 |
| H6 |  0.598018 |      0.324897 |          0        |                    0.302804 |    0.843783  |
| H7 |  0.274869 |      0.324897 |          0.684293 |                    0.564234 |    0.0822056 |
| H8 |  0.219117 |      0.324897 |          0        |                    0        |    0.273607  |

## Stability summary
|                           |   blocking_coalitions_count |   worst_deficit |   in_core |
|:--------------------------|----------------------------:|----------------:|----------:|
| shapley                   |                          46 |        0.118261 |         0 |
| equal_split               |                          63 |        0.465807 |         0 |
| pv_proportional           |                         117 |        0.644998 |         0 |
| contribution_proportional |                          98 |        0.333634 |         0 |
| least_core                |                           0 |        0        |         1 |