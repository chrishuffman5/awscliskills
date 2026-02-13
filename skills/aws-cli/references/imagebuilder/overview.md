# AWS CLI v2 — EC2 Image Builder

## Overview

Complete reference for all `aws imagebuilder` subcommands in AWS CLI v2. Covers image pipeline management, image recipes, container recipes, component creation, image building and testing, infrastructure configurations, distribution configurations, lifecycle policies, and workflow orchestration. EC2 Image Builder automates the creation, management, and deployment of customized, secure, and up-to-date server images.

## Quick Reference — Common Workflows

### Create a component
```bash
aws imagebuilder create-component \
  --name my-component \
  --semantic-version 1.0.0 \
  --platform Linux \
  --uri s3://my-bucket/component.yaml
```

### Create an image recipe
```bash
aws imagebuilder create-image-recipe \
  --name my-recipe \
  --semantic-version 1.0.0 \
  --parent-image arn:aws:imagebuilder:us-east-1:aws:image/amazon-linux-2-x86/x.x.x \
  --components componentArn=arn:aws:imagebuilder:us-east-1:123456789012:component/my-component/1.0.0
```

### Create infrastructure configuration
```bash
aws imagebuilder create-infrastructure-configuration \
  --name my-infra-config \
  --instance-profile-name EC2InstanceProfileForImageBuilder \
  --instance-types m5.large \
  --subnet-id subnet-12345 \
  --security-group-ids sg-12345
```

### Create distribution configuration
```bash
aws imagebuilder create-distribution-configuration \
  --name my-dist-config \
  --distributions '[{"region":"us-east-1","amiDistributionConfiguration":{"name":"my-ami-{{imagebuilder:buildDate}}","amiTags":{"Name":"my-image"}}}]'
```

### Create an image pipeline
```bash
aws imagebuilder create-image-pipeline \
  --name my-pipeline \
  --image-recipe-arn arn:aws:imagebuilder:us-east-1:123456789012:image-recipe/my-recipe/1.0.0 \
  --infrastructure-configuration-arn arn:aws:imagebuilder:us-east-1:123456789012:infrastructure-configuration/my-infra-config \
  --distribution-configuration-arn arn:aws:imagebuilder:us-east-1:123456789012:distribution-configuration/my-dist-config \
  --schedule scheduleExpression="cron(0 10 * * ? *)",pipelineExecutionStartCondition=EXPRESSION_MATCH_ONLY
```

### Start a pipeline execution
```bash
aws imagebuilder start-image-pipeline-execution \
  --image-pipeline-arn arn:aws:imagebuilder:us-east-1:123456789012:image-pipeline/my-pipeline
```

### List images built by a pipeline
```bash
aws imagebuilder list-image-pipeline-images \
  --image-pipeline-arn arn:aws:imagebuilder:us-east-1:123456789012:image-pipeline/my-pipeline \
  --query 'imageSummaryList[].{Name:name,Version:version,Status:state.status}'
```

### Create a lifecycle policy
```bash
aws imagebuilder create-lifecycle-policy \
  --name my-lifecycle-policy \
  --execution-role arn:aws:iam::123456789012:role/ImageBuilderLifecycleRole \
  --resource-type AMI_IMAGE \
  --policy-details '[{"action":{"type":"DELETE"},"filter":{"type":"AGE","value":90,"unit":"DAYS"}}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Pipelines | [`pipelines.md`](pipelines.md) | create-image-pipeline, get-image-pipeline, list-image-pipelines, update-image-pipeline, delete-image-pipeline, start-image-pipeline-execution, list-image-pipeline-images |
| Image Recipes | [`image-recipes.md`](image-recipes.md) | create-image-recipe, get-image-recipe, list-image-recipes, get-image-recipe-policy, put-image-recipe-policy, delete-image-recipe |
| Container Recipes | [`container-recipes.md`](container-recipes.md) | create-container-recipe, get-container-recipe, list-container-recipes, get-container-recipe-policy, put-container-recipe-policy, delete-container-recipe |
| Components | [`components.md`](components.md) | create-component, get-component, list-components, import-component, get-component-policy, put-component-policy, delete-component, list-component-build-versions |
| Images | [`images.md`](images.md) | create-image, get-image, list-images, list-image-build-versions, get-image-policy, put-image-policy, delete-image, cancel-image-creation, import-vm-image |
| Image Scanning | [`image-scanning.md`](image-scanning.md) | get-image-recipe, list-image-scan-findings, list-image-scan-finding-aggregations, get-workflow-step-execution |
| Infrastructure | [`infrastructure.md`](infrastructure.md) | create-infrastructure-configuration, get-infrastructure-configuration, list-infrastructure-configurations, update-infrastructure-configuration, delete-infrastructure-configuration |
| Distribution | [`distribution.md`](distribution.md) | create-distribution-configuration, get-distribution-configuration, list-distribution-configurations, update-distribution-configuration, delete-distribution-configuration |
| Lifecycle | [`lifecycle.md`](lifecycle.md) | create-lifecycle-policy, get-lifecycle-policy, list-lifecycle-policies, update-lifecycle-policy, delete-lifecycle-policy, list-lifecycle-executions, list-lifecycle-execution-resources |
| Workflows | [`workflows.md`](workflows.md) | create-workflow, get-workflow, list-workflows, get-workflow-execution, list-workflow-executions, get-workflow-step-execution, list-workflow-step-executions, list-workflow-build-versions, delete-workflow |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
