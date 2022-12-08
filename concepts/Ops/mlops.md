# MLOps

The term descends from [DevOps](./devops.md).
It's DevOps applied to Machine-Learning projects.

## Lifecycle of a Machine Learning Project

![](https://i0.wp.com/neptune.ai/wp-content/uploads/2022/10/MLOps-life-cycle.png)
[neptune.ai about the process](https://neptune.ai/blog/life-cycle-of-a-machine-learning-project)


About the steps presented before, we have:
- happening in a sandbox environment, where developer -- or scientist -- are strugling to understand the data and to build a dataset that could help him to answer the main goal question:
  - Problem understading
  - Data Collection
  - Data Annotation
  - Data Wrangling
- yet happening in a sandbox environment, but a stage that could leverage some kind of automation:
  - Model Development
  - Training
  - Evaluation
- and, then, the final step of the process, where MLOps should be all over it:
  - Model Deployment
  - Maintenance

## Principles
and the relation with the one metioned at [DevOps](devops.md):

| MLOps Princple | DevOps Principle |
| --- | --- |
| Iterative-Incremental Development | Customer-Centric Action | 
| Automation | Automate everything you can |
| Continuos Testing, Integration, Delivery, Monitoring, Training... | End-to-end Resposibility, Automate everything you can and Continuos improvement |
| Versioning | End-to-end responsibility | 
| Reproducibility | Automate everything you can and Continuos improvement |

## Tools
Everyone metioned at [DevOps](devops.md) and 

- Pipeline automation 
  - Kubeflow
  - Tensorflow Extended

## Resources
1. [ml-ops.org](https://ml-ops.org/content/mlops-principles)
