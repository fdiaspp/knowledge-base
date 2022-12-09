# Vertex AI
It is the unified Machine Learning platform by Google Cloud
See more in https://cloud.google.com/vertex-ai

## Experimentation and Training



## Managed Datasets
First step of the process. It's a central place to make data available inside vertex[^6].

Tabular data can be used as dataset (as imagens, footages, sounds and text) and the sources could be:
- BigQuery
- Google Cloud Storage
- Pandas Dataframe

Terraform provides operator to create a dataset from code[^7].

## Logging and Security
Every action taken on Vertex AI[^5] are audited. The best practice here is to create the datasets that is needed to work as a [Vertex AI Managed Dataset](#managed-datasets) to have the logs on.

## MLOps

### Vertex Workbench
It's possible to control the access to a notebook with account granularity through Terraform[^2]. IT`ll, probabily, helps on audit of tasks executed on workbench.

### Vertex Pipelines: automation
Until this moment, it is known that Vertex do not provide an scheduling interface to orchestrate the execution of a pipeline. The solution for this remains on Cloud Scheduler[^1]. It will be used to schedule a HTTP request to Vertex Pipeline Run REST endpoint. Datomic already created a Terraform operator[^4] that encapsulate that. I, personally, dont like to depend on third party in simple cases like this one. It is possible to achieve the same results with one or two Terraform files.

> NOTICE: In Vertex Pipelines THERE IS NOT such concept of Pipeline. ONLY PipelineRun. 

Why this is an important piece of information? Because I DO NOT need to deploy my pipelines. Just send them, whenever I wanna it to run, through the rest api[^3]

#### What is the PipelineSpec[^3] mentioned on docs?

"The spec of the pipeline." says Google. 

Basically, it means, compile the Kubeflow pipeline and send it 
- or as string through HTTP request of a Cloud Schedule Task Creation 
- or to a Google Cloud Storage Bucket to be consumed everytime a Cloud Schedule trigger runs.

To compile a Kubeflow Pipeline, I need to 
```py
python my_pipeline.py
```
<!-- foot notes -->
[^1]: How to implement CI/CD for your Vertex AI Machine Learning Pipeline [link](https://medium.com/google-cloud/how-to-implement-ci-cd-for-your-vertex-ai-pipeline-27963bead8bd) \
[^2]: Set up Vertex AI Workbench with access to BigQuery and GCS using Terraform [link](https://nakamasato.medium.com/set-up-vertex-ai-workbench-with-access-to-bigquery-and-gcs-using-terraform-3844e7cb65bb) \
[^3]: Vertex API PipelineJobs REST endpoint overview [link](https://cloud.google.com/vertex-ai/docs/reference/rest/v1/projects.locations.pipelineJobs). \
[^4]: Terraform operator by Datomic [link](https://datatonic.com/insights/vertex-ai-pipelines-terraform-cloud-scheduler/) \
[^5]: Vertex AI Audit [link](https://cloud.google.com/vertex-ai/docs/general/audit-logging#audited_operations)
[^6]: Managed Datasets [link](https://cloud.google.com/vertex-ai/docs/training/using-managed-datasets)
[^7]: Terraform - Vertex ai Datasets [link](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/vertex_ai_dataset)