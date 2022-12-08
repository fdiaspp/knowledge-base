
# [Kubeflow](https://www.kubeflow.org/)

This tool is related to [MLOps](../concepts/Ops/mlops.md) concept.

## Architecture
It's a big platform that provides great tools to automate the pipeline and lifecycle of a machine learning model. Until now, it encopasses such components like:

- Central Dashboard
- [Kubeflow Pipelines](#kubeflow-pipelines)
- Kubeflow Notebooks
- Katib [beta in december '22] - Kubernetes native solution for AutoML. 

and others cool stuff like Training Operators and Multi-Tenancy. More [here](https://www.kubeflow.org/docs/components/multi-tenancy/overview/).


## Kubeflow Pipelines

V2 is out there already, but, at this moment, it's not in a stable form yet. So, let's continue with the stable one. I mean, V1.

### Key Concepts

#### Pipeline
Conceptual description of a ML Workflow. 

Important to note that there is a separation between what is abstract and what is the actual execution of a Pipeline. This term, Pipeline, is the concept of the workflow. The actual execution of a Pipeline is a [run](#run-and-recurring-run).

#### Pipeline Components [most important]
Conceptual definition of a ML task. 

Important to note, as Pipelines, this is a conceptual model. The actual execution of a Component is a [step](#step).

A Component is: 
- It's self-contained task.
- Like a Function, it has its own name, parameters, body and returns a values. 
  - A function that works on a K8s POD 
  - It must be enveloped as a [Docker Image](https://docs.docker.com/get-started/02_our_app/)
- For each component, one Kubernetes POD will be launch.

The component should implement two levels of code. 
- Runtime code - the one that actually DO the job
- Client code - the one that communicate with the engine that will RUN the job (like a GCP DATAPROC or AWS EMR spark cluster) **Not sure about this yet**

> Although the entire Kubeflow runs in a Kubernetes environment, for big data, maybe, process the job in a K8s POD is not the best practice. For those cases, Kubeflow/K8s acts like an orquestrator, which will be responsible to comunicate with the actual executor of your job.

**To specify** a compoment you must:
- Metadata [optional]
- Interface [optional]
- Implementation 

[Example of a component specification](https://www.kubeflow.org/docs/components/pipelines/v1/reference/component-spec/)

#### Graph
Pictorial representation in the Kubeflow Pipelines UI
![](https://www.kubeflow.org/docs/images/pipelines-xgboost-graph.png)

#### Experiment
- A workspace where you can specify different configuration setting for your pipelines
- You can separate each on in different logical namespaces
- You can use runs and recurring runs

#### Run and Recurring Run

Run:
- It is a single execution of a pipeline
- It has immutable logs of all experiments attempted
- It's self-contained to allow reproducibility

Recurring Run:
- It is a scheduled run


#### Run Trigger
Can be set with:
- Periodic
- Cron

#### Step
It's the instantiation of a [Component](#pipeline-components-most-important).

Like the relationship Pipeline -> Run. 
In complex pipelines, it could happen execute one Component more than once or even not execute at all, based on a if clause.

#### Output Artifact
Stuff emitted by the execution of a [Component](#pipeline-components-most-important) (or, a [Step](#step)).


#### ML Metadata
It uses [google/ml-metadata](https://github.com/google/ml-metadata) project to generate metadata infos and registering in Metadata Store.