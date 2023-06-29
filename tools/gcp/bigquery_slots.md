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

To know the average utilization over a period, use the base period in miliseconds[^3].

#### Example:
<img src="../../resources/imgs/bigquery_job_statistics.png" width=500 />

Image extracted from BigQuery from [^2].

The average over 1 hour where there will be only the execution of the images job, we will have the following:
```math
us = \frac{272086967}{60 * 60 * 1000} = 75.57
```
So, in average, we'll have 75 slots used on that hour. 
But this couldnt be any that efficient to determine how many slots we wanna have available on our org. 
I mean, we can see that there is a peak and that this job will, at least, be delayed.
We are using 75 slots in average per hour, and 4.534 per second untill this execution hit its end.



# References
[^1]: https://cloud.google.com/bigquery/docs/information-schema-jobs?hl=pt-br#calculate_average_slot_utilization
[^2]: https://medium.com/google-cloud/bigquery-slot-squeezes-896d9e0f2fc
[^3]: https://stackoverflow.com/questions/72187568/big-query-slot-estimator
