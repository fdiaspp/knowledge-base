# BigQuery Slots
Resources and thoughts on estimating and determining best amount of slots needed for a certain Reservation.

### What is Reservation

### What is Commitment

### How to estimate Slots
It's possible to estimate[^1][^2] slot utilization metric using:
```math
us = \frac{ts}{e}
```
where:
- us: used slots
- ts: totalSlotsMs BigQuery metric
- e: elapsedMs Bigquery Metric


# References
[^1]: https://cloud.google.com/bigquery/docs/information-schema-jobs?hl=pt-br#calculate_average_slot_utilization
[^2]: https://medium.com/google-cloud/bigquery-slot-squeezes-896d9e0f2fc
