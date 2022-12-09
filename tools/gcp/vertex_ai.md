# Vertex AI



## MLOps

### Vertex Pipelines: automation
Until this moment, it is known that Vertex do not provide an scheduling interface to orchestrate the execution of a pipeline. The solution for this remains on Cloud Scheduler. It will be used to schedule a HTTP request to Vertex Pipeline Run REST endpoint. Datomic already created a [Terraform operator](https://datatonic.com/insights/vertex-ai-pipelines-terraform-cloud-scheduler/) that encapsulate that. I, personally, dont like to depend on third party in simple cases like this one. It is possible to achieve the same results with one or two Terraform files.

> NOTICE: In Vertex Pipelines THERE IS NOT such concept of Pipeline. ONLY PipelineRun. 

Why this is an important piece of information? Because I DO NOT need to deploy my pipelines. Just send them, whenever I wanna it to run, through the [Vertex API REST endpoint](https://cloud.google.com/vertex-ai/docs/reference/rest/v1/projects.locations.pipelineJobs). 

#### What is the [PipelineSpec](https://cloud.google.com/vertex-ai/docs/reference/rest/v1/projects.locations.pipelineJobs#PipelineJob.FIELDS.pipeline_spec) mentioned on docs?

"The spec of the pipeline." says Google. 

Basically, it means, compile the Kubeflow pipeline and send it 
- or as string through HTTP request of a Cloud Schedule Task Creation 
- or to a Google Cloud Storage Bucket to be consumed everytime a Cloud Schedule trigger runs.

To compile a Kubeflow Pipeline, I need to 
```py
python my_pipeline.py
```

## Resources
- How to implement CI/CD for your Vertex AI Machine Learning Pipeline [link](https://medium.com/google-cloud/how-to-implement-ci-cd-for-your-vertex-ai-pipeline-27963bead8bd)
- Set up Vertex AI Workbench with access to BigQuery and GCS using Terraform [link](https://nakamasato.medium.com/set-up-vertex-ai-workbench-with-access-to-bigquery-and-gcs-using-terraform-3844e7cb65bb)