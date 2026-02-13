# AWS CLI v2 — MWAA (Managed Workflows for Apache Airflow)

## Overview

Complete reference for all `aws mwaa` subcommands in AWS CLI v2. Covers environment creation and management, Airflow CLI and web login token generation, REST API invocation, and resource tagging. MWAA provides a fully managed Apache Airflow service that runs in your VPC with automatic scaling, patching, and monitoring.

## Quick Reference — Common Workflows

### Create an environment
```bash
aws mwaa create-environment --name my-airflow-env \
  --execution-role-arn arn:aws:iam::123456789012:role/MwaaExecutionRole \
  --source-bucket-arn arn:aws:s3:::my-airflow-bucket \
  --dag-s3-path dags \
  --network-configuration "SubnetIds=subnet-aaa,subnet-bbb,SecurityGroupIds=sg-ccc" \
  --environment-class mw1.small \
  --max-workers 10 --min-workers 1 \
  --webserver-access-mode PUBLIC_ONLY
```

### Get environment details
```bash
aws mwaa get-environment --name my-airflow-env \
  --query 'Environment.{Status:Status,Url:WebserverUrl,Version:AirflowVersion}'
```

### Update environment (deploy new DAGs / change config)
```bash
aws mwaa update-environment --name my-airflow-env \
  --airflow-version 2.10.3 \
  --environment-class mw1.medium \
  --max-workers 20
```

### Create a CLI token and run an Airflow command
```bash
CLI_TOKEN=$(aws mwaa create-cli-token --name my-airflow-env --query CliToken --output text)
HOSTNAME=$(aws mwaa create-cli-token --name my-airflow-env --query WebServerHostname --output text)
curl -s "https://$HOSTNAME/aws_mwaa/cli" \
  -H "Authorization: Bearer $CLI_TOKEN" \
  -H "Content-Type: text/plain" \
  -d "dags list"
```

### Create a web login token
```bash
aws mwaa create-web-login-token --name my-airflow-env
```

### Invoke the Airflow REST API
```bash
aws mwaa invoke-rest-api --name my-airflow-env \
  --path "/dags" --method GET
```

### List all environments
```bash
aws mwaa list-environments --query 'Environments'
```

### Delete an environment
```bash
aws mwaa delete-environment --name my-airflow-env
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Environments | [`environments.md`](environments.md) | create-environment, get-environment, update-environment, delete-environment, list-environments |
| Access & API | [`access-api.md`](access-api.md) | create-cli-token, create-web-login-token, invoke-rest-api, tag-resource, untag-resource, list-tags-for-resource |
