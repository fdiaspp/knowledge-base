# Vertex AI

## MLOps

### Pipeline execution automation
Until this moment, it is known that Vertex do not provide an scheduling interface to orchestrate the execution of a pipeline. The solution for this remains on Cloud Scheduler. It will be used to schedule a HTTP request to Vertex Pipeline Run REST endpoint. Datomic already created resouce an a Terraform operator that aims to do that. [link](https://datatonic.com/insights/vertex-ai-pipelines-terraform-cloud-scheduler/) 


## Other Cool Resources
- Set up Vertex AI Workbench with access to BigQuery and GCS using Terraform [link](https://nakamasato.medium.com/set-up-vertex-ai-workbench-with-access-to-bigquery-and-gcs-using-terraform-3844e7cb65bb)