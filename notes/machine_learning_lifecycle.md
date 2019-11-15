# Azure Machine Learning Lifecycle

- Data acquisition

  - Ingest data from sources
    - RDBMS, NoSQL, unstructured, and/or data lake datasoruces
  - [AzureML open datasets](https://docs.microsoft.com/en-us/python/api/azureml-opendatasets/azureml.opendatasets?view=azure-ml-py)
    - Includes popular open datasets like New York City Taxi and Limousine Commission

- Data preparation

  - Create [datastore](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.datastore?view=azure-ml-py)
    - Supports Azure Blob Container, Azure File Share, Azure Data Lake, Azure Data Lake Gen2, Azure SQL Database, Azure PostgreSQL, and Databricks File System (as of 10/10/2019)
  - Create [datasets](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.dataset.dataset?view=azure-ml-py)
    - Supports TabularDatasets (csv, tsv, parquet, SQL query results, public web url) and FileDatasets (unstructured data like images)
  - Register datasets for reuse across experiments
  - Split data into training and testing sets

- Modelling

  - Create [workspace](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.workspace.workspace?view=azure-ml-py)
    - A workspace is the top-level resource for Azure Machine Learning service

  - Create [experiment](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.experiment.experiment?view=azure-ml-py)
    - An experiment is a grouping of many runs from a specified script

  - Create [ComputeTarget](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.computetarget?view=azure-ml-py)
    - [Full list of supported ComputeTarget](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-compute-target))
    - Training compute targets: local computer, AML Compute, Remote VM, Azure Databricks, HDInsight, etc

  - Create [environment](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.environment.environment?view=azure-ml-py)(Docker / Python / Spark / etc.)
    - An environment specifies the Python packages, environment variables, and software settings around your training and scoring scripts, and run times (Python, Spark, or Docker)
    - [How to use environments](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-use-environments)

  - Create training script
    - Supports all open source machine learning framework like Tensorflow, Keras, PyTorch, etc.

  - Create [run configuration](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.runconfiguration?view=azure-ml-py)
    - A run configuration is a set of instructions that defines how a script should be run in a specified compute target

  - Create [run](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.run%28class%29?view=azure-ml-py)
    - A run is a single execution of a training script

  - Alternative: [Estimators](https://docs.microsoft.com/en-us/python/api/azureml-train-core/azureml.train.estimator.estimator?view=azure-ml-py)
    - Wraps run configuration information to help simplify the tasks of specifying how a script is executed
    - Pre-configured estimators exist for Chainer, PyTorch, TensorFlow, and SKLearn

  - Register model to model registry
    - [Reference](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.run(class)?view=azure-ml-py#register-model-model-name--model-path-none--tags-none--properties-none--model-framework-none--model-framework-version-none--description-none--datasets-none----kwargs-)

- Deployment

  - Create [ComputeTarget](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.computetarget?view=azure-ml-py)
    - [Full list of supported ComputeTarget](https://docs.microsoft.com/en-us/azure/machine-learning/service/concept-compute-target))
    - Deployment targets: local computer, ACI, AKS, AML Compute, Azure IoT Edge  - Create scoring script

  - Create [inferencing configuration](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.model.inferenceconfig?view=azure-ml-py)
    - Model deployment config specific to model deployments - requires entry_script and runtime.

  - Create [deployment configuration](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.webservice.akswebservice?view=azure-ml-py#deploy-configuration-autoscale-enabled-none--autoscale-min-replicas-none--autoscale-max-replicas-none--autoscale-refresh-seconds-none--autoscale-target-utilization-none--collect-model-data-none--auth-enabled-none--cpu-cores-none--memory-gb-none--enable-app-insights-none--scoring-timeout-ms-none--replica-max-concurrent-requests-none--max-request-wait-time-none--num-replicas-none--primary-key-none--secondary-key-none--tags-none--properties-none--description-none--gpu-cores-none--period-seconds-none--initial-delay-seconds-none--timeout-seconds-none--success-threshold-none--failure-threshold-none--namespace-none--token-auth-enabled-none-)
    - `deploy_configuration` is different per deployment target (e.g. ACI, AKS, etc.)

  - Create web service deployment
    - There are 2 mechanisms for deploying ML models: [deploy from model](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.model.model?view=azure-ml-py#deploy-workspace--name--models--inference-config--deployment-config-none--deployment-target-none-) and [deploy from image](https://docs.microsoft.com/en-us/python/api/azureml-core/azureml.core.webservice%28class%29?view=azure-ml-py#deploy-from-image-workspace--name--image--deployment-config-none--deployment-target-none-)

- Monitoring
  - Application Insight

- Tracking
  - Metadata about the run (timestamp, duration, and so on)
  - [Logging and Metrics](https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-track-experiments)
  - Output files that are autocollected by the experiment or explicitly uploaded by you
  - Snapshot of the directory that contains your scripts, prior to the run
  - GitHub tracking and integration
    - When you start a training run where the source directory is a local Git repository, information about the repository is stored in the run history. For example, the current commit ID for the repository is logged as part of the history.

## Extras

- [Pipeline](https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/azureml.pipeline.core.pipeline%28class%29?view=azure-ml-py)
  - A pipeline create and manage workflows that stitch together machine learning phases
  - [Pre-built steps](https://docs.microsoft.com/en-us/python/api/azureml-pipeline-steps/azureml.pipeline.steps?view=azure-ml-py) that can be executed in an AML Pipeline

- [AutoML](https://docs.microsoft.com/en-us/python/api/azureml-train-automl/azureml.train.automl?view=azure-ml-py)

- [Azure ML Hardware Accelerated Models](https://docs.microsoft.com/en-us/python/api/azureml-accel-models/azureml.accel?view=azure-ml-py)

- [Explain Model](https://docs.microsoft.com/en-us/python/api/azureml-explain-model/azureml.explain.model?view=azure-ml-py)
  - Explain why a model model makes the predictions it does and help build confidence in the model
  - Understand the model’s global behavior or specific predictions