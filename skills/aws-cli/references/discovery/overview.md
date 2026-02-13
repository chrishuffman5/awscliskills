# AWS CLI v2 -- Application Discovery Service

## Overview

Complete reference for all `aws discovery` subcommands in AWS CLI v2. AWS Application Discovery Service helps you plan migration projects by identifying servers, virtual machines, software, and network dependencies in your on-premises data centers. Supports discovery via agents (installed on servers), agentless collectors (VMware vCenter), and manual import (CSV files).

## Quick Reference -- Common Workflows

### Get a discovery summary
```bash
aws discovery get-discovery-summary
```

### Start and stop agent data collection
```bash
aws discovery start-data-collection-by-agent-ids \
  --agent-ids "i-0123456789abcdef0" "i-abcdef0123456789a"

aws discovery stop-data-collection-by-agent-ids \
  --agent-ids "i-0123456789abcdef0" "i-abcdef0123456789a"
```

### List discovered servers with filters
```bash
aws discovery list-configurations \
  --configuration-type SERVER \
  --filters name="server.osName",values="Ubuntu",condition="CONTAINS"
```

### Create an application and associate servers
```bash
aws discovery create-application \
  --name "MyWebApp" \
  --description "Production web application"

aws discovery associate-configuration-items-to-application \
  --application-configuration-id "d-app-0123456789abcdef0" \
  --configuration-ids "d-server-0123456789abcdef0" "d-server-abcdef0123456789a"
```

### Export discovered data
```bash
aws discovery start-export-task

aws discovery describe-export-tasks \
  --export-ids "export-0123456789abcdef0"
```

### Import data from CSV
```bash
aws discovery start-import-task \
  --name "my-import" \
  --import-url "s3://my-bucket/import-data.csv"

aws discovery describe-import-tasks
```

### Start continuous export to S3/Athena
```bash
aws discovery start-continuous-export

aws discovery describe-continuous-exports
```

### List server network dependencies
```bash
aws discovery list-server-neighbors \
  --configuration-id "d-server-0123456789abcdef0" \
  --port-information-needed
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Agents | [`agents.md`](agents.md) | describe-agents, start-data-collection-by-agent-ids, stop-data-collection-by-agent-ids, batch-delete-agents |
| Configurations | [`configurations.md`](configurations.md) | describe-configurations, list-configurations, list-server-neighbors, get-discovery-summary, start-batch-delete-configuration-task, describe-batch-delete-configuration-task |
| Applications | [`applications.md`](applications.md) | create-application, update-application, delete-applications, associate-configuration-items-to-application, disassociate-configuration-items-from-application |
| Export & Import | [`export-import.md`](export-import.md) | start-export-task, describe-export-tasks, start-continuous-export, stop-continuous-export, describe-continuous-exports, start-import-task, describe-import-tasks, batch-delete-import-data |
| Tags | [`tags.md`](tags.md) | create-tags, delete-tags, describe-tags |
