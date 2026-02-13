# AWS CLI v2 — EMR (Elastic MapReduce + EMR Containers + EMR Serverless)

## Overview

Complete reference for `aws emr`, `aws emr-containers`, and `aws emr-serverless` subcommands in AWS CLI v2. Covers EMR cluster lifecycle management, instance groups and fleets, step submission, auto scaling, security configuration, EMR Studio and notebooks, EMR on EKS virtual clusters and managed endpoints, and EMR Serverless applications and job runs.

## Quick Reference — Common Workflows

### Create an EMR cluster
```bash
aws emr create-cluster \
  --name "My Spark Cluster" \
  --release-label emr-7.0.0 \
  --applications Name=Spark Name=Hive \
  --instance-type m5.xlarge --instance-count 3 \
  --use-default-roles
```

### Add a Spark step to a running cluster
```bash
aws emr add-steps --cluster-id j-XXXXXXXXXXXXX \
  --steps Type=Spark,Name="Spark Job",ActionOnFailure=CONTINUE,\
Args=[--class,com.example.Main,s3://bucket/app.jar,arg1]
```

### List cluster status
```bash
aws emr describe-cluster --cluster-id j-XXXXXXXXXXXXX \
  --query 'Cluster.{Name:Name,Status:Status.State}'
```

### SSH into the master node
```bash
aws emr ssh --cluster-id j-XXXXXXXXXXXXX --key-pair-file ~/.ssh/mykey.pem
```

### Terminate a cluster
```bash
aws emr terminate-clusters --cluster-ids j-XXXXXXXXXXXXX
```

### Create an EMR on EKS virtual cluster
```bash
aws emr-containers create-virtual-cluster \
  --name my-virtual-cluster \
  --container-provider type=EKS,id=my-eks-cluster,\
info={eksInfo={namespace=emr}}
```

### Submit a job to EMR on EKS
```bash
aws emr-containers start-job-run \
  --virtual-cluster-id vc-XXXXXXXXXXXXX \
  --name "My Spark Job" \
  --execution-role-arn arn:aws:iam::123456789012:role/emr-on-eks-role \
  --release-label emr-7.0.0-latest \
  --job-driver sparkSubmitJobDriver='{entryPoint: "s3://bucket/script.py"}'
```

### Create an EMR Serverless application
```bash
aws emr-serverless create-application \
  --name my-spark-app \
  --release-label emr-7.0.0 \
  --type SPARK
```

### Run a job on EMR Serverless
```bash
aws emr-serverless start-job-run \
  --application-id app-XXXXXXXXXXXXX \
  --execution-role-arn arn:aws:iam::123456789012:role/emr-serverless-role \
  --job-driver sparkSubmit='{entryPoint: "s3://bucket/script.py"}' \
  --name "My Serverless Spark Job"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cluster, describe-cluster, list-clusters, terminate-clusters, modify-cluster, put-auto-termination-policy, get-auto-termination-policy, remove-auto-termination-policy |
| Instance Management | [`instance-management.md`](instance-management.md) | add-instance-groups, modify-instance-groups, list-instance-groups, add-instance-fleet, modify-instance-fleet, list-instance-fleets, list-instances, modify-cluster |
| Steps | [`steps.md`](steps.md) | add-steps, cancel-steps, list-steps, describe-step |
| Scaling | [`scaling.md`](scaling.md) | put-auto-scaling-policy, remove-auto-scaling-policy, put-managed-scaling-policy, get-managed-scaling-policy, remove-managed-scaling-policy |
| Security | [`security.md`](security.md) | create-security-configuration, delete-security-configuration, describe-security-configuration, list-security-configurations, put-block-public-access-configuration, get-block-public-access-configuration, delete-block-public-access-configuration |
| Studios | [`studios.md`](studios.md) | create-studio, delete-studio, describe-studio, list-studios, update-studio, create-studio-session-mapping, delete-studio-session-mapping, get-studio-session-mapping, list-studio-session-mappings, update-studio-session-mapping |
| Notebooks | [`notebooks.md`](notebooks.md) | create-notebook-execution, describe-notebook-execution, list-notebook-executions, start-notebook-execution, stop-notebook-execution |
| HBase | [`hbase.md`](hbase.md) | create-cluster (HBase), schedule-hbase-backup, restore-hbase-backup |
| App UI | [`app-ui.md`](app-ui.md) | get-cluster-session-credentials |
| Utility | [`utility.md`](utility.md) | ssh, socks, get, put, wait |
| EMR Containers — Clusters | [`emr-containers-clusters.md`](emr-containers-clusters.md) | create-virtual-cluster, delete-virtual-cluster, describe-virtual-cluster, list-virtual-clusters |
| EMR Containers — Jobs | [`emr-containers-jobs.md`](emr-containers-jobs.md) | start-job-run, cancel-job-run, describe-job-run, list-job-runs, get-managed-endpoint-session-credentials |
| EMR Containers — Security | [`emr-containers-security.md`](emr-containers-security.md) | create-managed-endpoint, delete-managed-endpoint, describe-managed-endpoint, list-managed-endpoints, create-security-configuration, delete-security-configuration, describe-security-configuration, list-security-configurations, tag-resource, untag-resource, list-tags-for-resource |
| Serverless — Applications | [`serverless-applications.md`](serverless-applications.md) | create-application, delete-application, get-application, list-applications, update-application, start-application, stop-application |
| Serverless — Jobs | [`serverless-jobs.md`](serverless-jobs.md) | start-job-run, cancel-job-run, get-job-run, list-job-runs, get-dashboard-for-job-run, tag-resource, untag-resource, list-tags-for-resource |
| Wait Commands | [`wait.md`](wait.md) | wait cluster-running, wait cluster-terminated, wait step-complete |
