# BigQuery Jobs[^1]


### Checking the query 
To check a query used in a specific job via cli (`bq` utility which come along with `gcloud` instalation), use:

```bash
bq --location=southamerica-east1 --format=prettyjson show -j <job_id> | grep '"query":'
```


### Distribution of Bytes Billed
```sql
-- Bytes billed distribution hourly from last week
--
--
select 
  LEFT(STRING(DATETIME(end_time, "America/Sao_Paulo")), 13) end_time_h,
  SUM(total_bytes_billed) total_bytes_billed

from `region-southamerica-east1`.INFORMATION_SCHEMA.JOBS
where creation_time BETWEEN TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 8 DAY) AND CURRENT_TIMESTAMP()
 and end_time BETWEEN TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 7 DAY) AND CURRENT_TIMESTAMP()
group by end_time_h
```


### Learning granular execution
```sql
-- learning who did something, based on query end_time
--
--
select 
  DATETIME(end_time, "America/Sao_Paulo") end_time,
  user_email,
  query, 
  total_bytes_billed
from `region-southamerica-east1`.INFORMATION_SCHEMA.JOBS
where creation_time BETWEEN TIMESTAMP_SUB(CURRENT_TIMESTAMP(), INTERVAL 8 DAY) AND CURRENT_TIMESTAMP()
 and end_time BETWEEN '2023-07-06 00:00:00' and '2023-07-07 00:00:00'
 ```


[^1]: Jobs view: https://cloud.google.com/bigquery/docs/information-schema-jobs