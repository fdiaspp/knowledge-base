# BigQuery Jobs


### Checking the query 
To check a query used in a specific job via cli (`bq` utility which come along with `gcloud` instalation), use:

```bash
bq --location=southamerica-east1 --format=prettyjson show -j <job_id> | grep '"query":'
```