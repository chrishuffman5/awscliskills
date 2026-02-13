# AWS CLI v2 — Amazon SageMaker

## Overview

Complete reference for `aws sagemaker` and `aws sagemaker-runtime` subcommands in AWS CLI v2. Covers training jobs, model creation, endpoint deployment, processing jobs, hyperparameter tuning, AutoML, pipelines, experiments, Feature Store, model registry, model cards, monitoring, inference experiments, notebook instances, HyperPod clusters, Studio domains, MLflow integration, optimization jobs, labeling, workforce management, custom images, SageMaker Hubs, lineage tracking, edge deployment, partner apps, studio lifecycle configs, batch transform, algorithms, projects, code repositories, search, and real-time/async inference.

## Quick Reference — Common Workflows

### Create a training job
```bash
aws sagemaker create-training-job \
  --training-job-name my-training \
  --role-arn arn:aws:iam::123456789012:role/SageMakerRole \
  --algorithm-specification TrainingImage=382416733822.dkr.ecr.us-east-1.amazonaws.com/xgboost:latest,TrainingInputMode=File \
  --input-data-config '[{"ChannelName":"train","DataSource":{"S3DataSource":{"S3Uri":"s3://bucket/train","S3DataType":"S3Prefix"}}}]' \
  --output-data-config S3OutputPath=s3://bucket/output \
  --resource-config InstanceType=ml.m5.xlarge,InstanceCount=1,VolumeSizeInGB=30 \
  --stopping-condition MaxRuntimeInSeconds=86400
```

### Create a model and deploy to an endpoint
```bash
aws sagemaker create-model \
  --model-name my-model \
  --primary-container Image=382416733822.dkr.ecr.us-east-1.amazonaws.com/xgboost:latest,ModelDataUrl=s3://bucket/output/model.tar.gz \
  --execution-role-arn arn:aws:iam::123456789012:role/SageMakerRole

aws sagemaker create-endpoint-config \
  --endpoint-config-name my-config \
  --production-variants '[{"VariantName":"primary","ModelName":"my-model","InstanceType":"ml.m5.xlarge","InitialInstanceCount":1}]'

aws sagemaker create-endpoint \
  --endpoint-name my-endpoint \
  --endpoint-config-name my-config

aws sagemaker wait endpoint-in-service --endpoint-name my-endpoint
```

### Invoke an endpoint
```bash
aws sagemaker-runtime invoke-endpoint \
  --endpoint-name my-endpoint \
  --content-type text/csv \
  --body '1.0,2.0,3.0' \
  output.json
```

### Create and run a pipeline
```bash
aws sagemaker create-pipeline \
  --pipeline-name my-pipeline \
  --pipeline-definition file://pipeline.json \
  --role-arn arn:aws:iam::123456789012:role/SageMakerRole

aws sagemaker start-pipeline-execution \
  --pipeline-name my-pipeline
```

### Run a processing job
```bash
aws sagemaker create-processing-job \
  --processing-job-name my-processing \
  --role-arn arn:aws:iam::123456789012:role/SageMakerRole \
  --processing-resources '{"ClusterConfig":{"InstanceCount":1,"InstanceType":"ml.m5.xlarge","VolumeSizeInGB":30}}' \
  --app-specification ImageUri=382416733822.dkr.ecr.us-east-1.amazonaws.com/sagemaker-scikit-learn:latest
```

### Create a hyperparameter tuning job
```bash
aws sagemaker create-hyper-parameter-tuning-job \
  --hyper-parameter-tuning-job-name my-tuning \
  --hyper-parameter-tuning-job-config '{"Strategy":"Bayesian","HyperParameterTuningJobObjective":{"Type":"Maximize","MetricName":"validation:auc"},"ResourceLimits":{"MaxNumberOfTrainingJobs":20,"MaxParallelTrainingJobs":3}}' \
  --training-job-definition file://training-def.json
```

### Create a Feature Store feature group
```bash
aws sagemaker create-feature-group \
  --feature-group-name my-features \
  --record-identifier-feature-name customer_id \
  --event-time-feature-name event_time \
  --feature-definitions '[{"FeatureName":"customer_id","FeatureType":"String"},{"FeatureName":"event_time","FeatureType":"String"},{"FeatureName":"age","FeatureType":"Integral"}]' \
  --online-store-config '{"EnableOnlineStore":true}' \
  --role-arn arn:aws:iam::123456789012:role/SageMakerRole
```

### Register a model in Model Registry
```bash
aws sagemaker create-model-package \
  --model-package-group-name my-model-group \
  --inference-specification '{"Containers":[{"Image":"382416733822.dkr.ecr.us-east-1.amazonaws.com/xgboost:latest","ModelDataUrl":"s3://bucket/model.tar.gz"}],"SupportedTransformInstanceTypes":["ml.m5.xlarge"],"SupportedRealtimeInferenceInstanceTypes":["ml.m5.xlarge"],"SupportedContentTypes":["text/csv"],"SupportedResponseMIMETypes":["text/csv"]}' \
  --model-approval-status Approved
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Training | [`training.md`](training.md) | create-training-job, describe-training-job, list-training-jobs, stop-training-job, update-training-job, delete-training-job, create-training-plan, describe-training-plan, list-training-plans, search-training-plan-offerings |
| Models | [`models.md`](models.md) | create-model, describe-model, list-models, delete-model, create-compilation-job, describe-compilation-job, list-compilation-jobs, stop-compilation-job, delete-compilation-job |
| Endpoints | [`endpoints.md`](endpoints.md) | create-endpoint-config, describe-endpoint-config, list-endpoint-configs, delete-endpoint-config, create-endpoint, describe-endpoint, list-endpoints, update-endpoint, update-endpoint-weights-and-capacities, delete-endpoint, create-inference-component, describe-inference-component, list-inference-components, update-inference-component, update-inference-component-runtime-config, delete-inference-component |
| Processing | [`processing.md`](processing.md) | create-processing-job, describe-processing-job, list-processing-jobs, stop-processing-job, delete-processing-job |
| Hyperparameter Tuning | [`hyperparameter-tuning.md`](hyperparameter-tuning.md) | create-hyper-parameter-tuning-job, describe-hyper-parameter-tuning-job, list-hyper-parameter-tuning-jobs, stop-hyper-parameter-tuning-job, delete-hyper-parameter-tuning-job, list-training-jobs-for-hyper-parameter-tuning-job |
| AutoML | [`automl.md`](automl.md) | create-auto-ml-job, describe-auto-ml-job, list-auto-ml-jobs, stop-auto-ml-job, create-auto-ml-job-v2, describe-auto-ml-job-v2, list-candidates-for-auto-ml-job |
| Pipelines | [`pipelines.md`](pipelines.md) | create-pipeline, describe-pipeline, list-pipelines, update-pipeline, delete-pipeline, start-pipeline-execution, describe-pipeline-execution, list-pipeline-executions, stop-pipeline-execution, retry-pipeline-execution, update-pipeline-execution, list-pipeline-execution-steps, list-pipeline-parameters-for-execution, describe-pipeline-definition-for-execution, send-pipeline-execution-step-success, send-pipeline-execution-step-failure, list-pipeline-versions, update-pipeline-version |
| Experiments | [`experiments.md`](experiments.md) | create-experiment, describe-experiment, list-experiments, update-experiment, delete-experiment, create-trial, describe-trial, list-trials, update-trial, delete-trial, create-trial-component, describe-trial-component, list-trial-components, update-trial-component, delete-trial-component, associate-trial-component, disassociate-trial-component |
| Feature Store | [`feature-store.md`](feature-store.md) | create-feature-group, describe-feature-group, list-feature-groups, update-feature-group, delete-feature-group, describe-feature-metadata, update-feature-metadata |
| Model Registry | [`model-registry.md`](model-registry.md) | create-model-package-group, describe-model-package-group, list-model-package-groups, delete-model-package-group, get-model-package-group-policy, put-model-package-group-policy, delete-model-package-group-policy, create-model-package, describe-model-package, list-model-packages, update-model-package, delete-model-package, batch-describe-model-package, list-model-metadata |
| Model Cards | [`model-cards.md`](model-cards.md) | create-model-card, describe-model-card, list-model-cards, update-model-card, delete-model-card, list-model-card-versions, create-model-card-export-job, describe-model-card-export-job, list-model-card-export-jobs |
| Monitoring | [`monitoring.md`](monitoring.md) | create-monitoring-schedule, describe-monitoring-schedule, list-monitoring-schedules, update-monitoring-schedule, delete-monitoring-schedule, start-monitoring-schedule, stop-monitoring-schedule, list-monitoring-executions, list-monitoring-alerts, list-monitoring-alert-history, update-monitoring-alert, create-data-quality-job-definition, describe-data-quality-job-definition, list-data-quality-job-definitions, delete-data-quality-job-definition, create-model-quality-job-definition, describe-model-quality-job-definition, list-model-quality-job-definitions, delete-model-quality-job-definition, create-model-bias-job-definition, describe-model-bias-job-definition, list-model-bias-job-definitions, delete-model-bias-job-definition, create-model-explainability-job-definition, describe-model-explainability-job-definition, list-model-explainability-job-definitions, delete-model-explainability-job-definition |
| Inference Experiments | [`inference-experiments.md`](inference-experiments.md) | create-inference-experiment, describe-inference-experiment, list-inference-experiments, update-inference-experiment, start-inference-experiment, stop-inference-experiment, delete-inference-experiment, create-inference-recommendations-job, describe-inference-recommendations-job, list-inference-recommendations-jobs, stop-inference-recommendations-job, list-inference-recommendations-job-steps, get-scaling-configuration-recommendation |
| Notebooks | [`notebooks.md`](notebooks.md) | create-notebook-instance, describe-notebook-instance, list-notebook-instances, update-notebook-instance, start-notebook-instance, stop-notebook-instance, delete-notebook-instance, create-notebook-instance-lifecycle-config, describe-notebook-instance-lifecycle-config, list-notebook-instance-lifecycle-configs, update-notebook-instance-lifecycle-config, delete-notebook-instance-lifecycle-config, create-presigned-notebook-instance-url |
| Clusters | [`clusters.md`](clusters.md) | create-cluster, describe-cluster, list-clusters, update-cluster, delete-cluster, update-cluster-software, describe-cluster-node, list-cluster-nodes, batch-add-cluster-nodes, batch-delete-cluster-nodes, batch-reboot-cluster-nodes, batch-replace-cluster-nodes, attach-cluster-node-volume, detach-cluster-node-volume, describe-cluster-event, list-cluster-events, create-cluster-scheduler-config, describe-cluster-scheduler-config, list-cluster-scheduler-configs, update-cluster-scheduler-config, delete-cluster-scheduler-config, create-compute-quota, describe-compute-quota, list-compute-quotas, update-compute-quota, delete-compute-quota, describe-reserved-capacity, list-ultra-servers-by-reserved-capacity |
| Domains | [`domains.md`](domains.md) | create-domain, describe-domain, list-domains, update-domain, delete-domain, create-user-profile, describe-user-profile, list-user-profiles, update-user-profile, delete-user-profile, create-space, describe-space, list-spaces, update-space, delete-space, create-app, describe-app, list-apps, delete-app, create-presigned-domain-url |
| MLflow | [`mlflow.md`](mlflow.md) | create-mlflow-tracking-server, describe-mlflow-tracking-server, list-mlflow-tracking-servers, update-mlflow-tracking-server, start-mlflow-tracking-server, stop-mlflow-tracking-server, delete-mlflow-tracking-server, create-presigned-mlflow-tracking-server-url, create-mlflow-app, describe-mlflow-app, list-mlflow-apps, update-mlflow-app, delete-mlflow-app, create-presigned-mlflow-app-url |
| Optimization | [`optimization.md`](optimization.md) | create-optimization-job, describe-optimization-job, list-optimization-jobs, stop-optimization-job, delete-optimization-job |
| Labeling | [`labeling.md`](labeling.md) | create-labeling-job, describe-labeling-job, list-labeling-jobs, stop-labeling-job, list-labeling-jobs-for-workteam, create-flow-definition, describe-flow-definition, list-flow-definitions, delete-flow-definition, create-human-task-ui, describe-human-task-ui, list-human-task-uis, delete-human-task-ui, render-ui-template |
| Workforce | [`workforce.md`](workforce.md) | create-workforce, describe-workforce, list-workforces, update-workforce, delete-workforce, create-workteam, describe-workteam, list-workteams, update-workteam, delete-workteam, describe-subscribed-workteam, list-subscribed-workteams |
| Images | [`images.md`](images.md) | create-image, describe-image, list-images, update-image, delete-image, create-image-version, describe-image-version, list-image-versions, update-image-version, delete-image-version, create-app-image-config, describe-app-image-config, list-app-image-configs, update-app-image-config, delete-app-image-config |
| Hubs | [`hubs.md`](hubs.md) | create-hub, describe-hub, list-hubs, update-hub, delete-hub, describe-hub-content, list-hub-contents, list-hub-content-versions, update-hub-content, delete-hub-content, create-hub-content-reference, update-hub-content-reference, delete-hub-content-reference, create-hub-content-presigned-urls, import-hub-content |
| Lineage | [`lineage.md`](lineage.md) | create-action, describe-action, list-actions, update-action, delete-action, create-artifact, describe-artifact, list-artifacts, update-artifact, delete-artifact, create-context, describe-context, list-contexts, update-context, delete-context, add-association, list-associations, delete-association, describe-lineage-group, list-lineage-groups, get-lineage-group-policy, query-lineage |
| Edge | [`edge.md`](edge.md) | create-device-fleet, describe-device-fleet, list-device-fleets, update-device-fleet, delete-device-fleet, get-device-fleet-report, register-devices, describe-device, list-devices, update-devices, deregister-devices, create-edge-deployment-plan, describe-edge-deployment-plan, list-edge-deployment-plans, delete-edge-deployment-plan, create-edge-deployment-stage, start-edge-deployment-stage, stop-edge-deployment-stage, delete-edge-deployment-stage, create-edge-packaging-job, describe-edge-packaging-job, list-edge-packaging-jobs, stop-edge-packaging-job |
| Partner Apps | [`partner-apps.md`](partner-apps.md) | create-partner-app, describe-partner-app, list-partner-apps, update-partner-app, delete-partner-app, create-partner-app-presigned-url |
| Studio Lifecycle | [`studio-lifecycle.md`](studio-lifecycle.md) | create-studio-lifecycle-config, describe-studio-lifecycle-config, list-studio-lifecycle-configs, delete-studio-lifecycle-config |
| Transform | [`transform.md`](transform.md) | create-transform-job, describe-transform-job, list-transform-jobs, stop-transform-job |
| Algorithms | [`algorithms.md`](algorithms.md) | create-algorithm, describe-algorithm, list-algorithms, delete-algorithm |
| Projects | [`projects.md`](projects.md) | create-project, describe-project, list-projects, update-project, delete-project, enable-sagemaker-servicecatalog-portfolio, disable-sagemaker-servicecatalog-portfolio, get-sagemaker-servicecatalog-portfolio-status, list-resource-catalogs |
| Code Repositories | [`code-repositories.md`](code-repositories.md) | create-code-repository, describe-code-repository, list-code-repositories, update-code-repository, delete-code-repository |
| Search & Tags | [`search-tags.md`](search-tags.md) | search, get-search-suggestions, add-tags, delete-tags, list-tags, list-aliases |
| Runtime | [`runtime.md`](runtime.md) | invoke-endpoint, invoke-endpoint-async |
| Wait | [`wait.md`](wait.md) | wait endpoint-in-service, wait endpoint-deleted, wait notebook-instance-in-service, wait notebook-instance-stopped, wait notebook-instance-deleted, wait training-job-completed-or-stopped, wait processing-job-completed-or-stopped, wait transform-job-completed-or-stopped, wait image-created, wait image-updated, wait image-deleted, wait image-version-created, wait image-version-deleted |
