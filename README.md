# AWS CLI Skills for Claude Code

A unified AWS CLI v2 reference skill for [Claude Code](https://claude.ai/code). Provides comprehensive command references — flags, types, defaults, and JSON output schemas — for 121 AWS services, sourced from official AWS documentation.

## Covered Services

| Service | Reference | Scope |
|---------|-----------|-------|
| ECS | `references/ecs/` | Clusters, services, tasks, task definitions, container instances, capacity providers |
| EC2 | `references/ec2/` | Instances, VPCs, subnets, security groups, key pairs, AMIs, launch templates, auto scaling |
| ECR | `references/ecr/` | Repositories, images, lifecycle policies, scanning, authentication, registry |
| S3 | `references/s3/` | Buckets, objects, storage classes, lifecycle, versioning, website hosting, presigned URLs |
| RDS | `references/rds/` | DB instances, Aurora clusters, snapshots, parameter groups, subnet groups, replicas, proxies |
| Route 53 | `references/route53/` | Hosted zones, DNS records, health checks, routing policies, domain registration |
| IAM | `references/iam/` | Users, groups, roles, policies, instance profiles, access keys, MFA, identity providers |
| CloudWatch | `references/cloudwatch/` | Metrics, alarms, dashboards, log groups, log streams, metric filters, Insights queries |
| ELBv2 | `references/elbv2/` | ALBs, NLBs, target groups, listeners, rules, health checks, SSL certificates |
| Lambda | `references/lambda/` | Functions, layers, event source mappings, aliases, versions, concurrency, URLs |
| DynamoDB | `references/dynamodb/` | Tables, items, indexes, queries, scans, streams, backups, global tables, TTL |
| KMS | `references/kms/` | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| SNS | `references/sns/` | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | `references/sqs/` | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| CloudFront | `references/cloudfront/` | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| Secrets Manager | `references/secretsmanager/` | Secrets, versions, rotation, replication, resource policies, batch retrieval |
| API Gateway | `references/apigateway/` | REST APIs, HTTP APIs, resources, methods, stages, authorizers, API keys, usage plans |
| Step Functions | `references/stepfunctions/` | State machines, executions, activities, map runs, versions |
| Cognito | `references/cognito/` | User pools, user pool clients, users, groups, identity providers, identity pools, MFA |
| SES v2 | `references/sesv2/` | Email identities, configuration sets, contact lists, templates, sending, suppression |
| EventBridge | `references/eventbridge/` | Event buses, rules, targets, archives, replays, connections, API destinations, pipes |
| Systems Manager | `references/ssm/` | Parameter Store, documents, Run Command, Session Manager, patch baselines, state manager |
| ACM | `references/acm/` | Certificates, import/export, validation, tags, account configuration |
| STS | `references/sts/` | Assume role, session tokens, federation, caller identity |
| CloudTrail | `references/cloudtrail/` | Trails, event selectors, event data stores, queries, channels, imports |
| EFS | `references/efs/` | File systems, mount targets, access points, replication, lifecycle |
| ElastiCache | `references/elasticache/` | Clusters, replication groups, parameter groups, snapshots, users, serverless |
| WAF v2 | `references/wafv2/` | Web ACLs, rule groups, IP sets, regex pattern sets, logging |
| CodeBuild | `references/codebuild/` | Projects, builds, build batches, report groups, source credentials, webhooks, fleets |
| CodeDeploy | `references/codedeploy/` | Applications, deployment groups, deployments, deployment configs, revisions |
| CodePipeline | `references/codepipeline/` | Pipelines, stages, actions, action types, webhooks |
| CloudFormation | `references/cloudformation/` | Stacks, change sets, stack sets, drift detection, resource scanning, type registry |
| Auto Scaling | `references/autoscaling/` | Auto Scaling groups, launch configs, scaling policies, lifecycle hooks, instance refresh |
| EKS | `references/eks/` | Clusters, node groups, Fargate profiles, add-ons, access management, Pod Identity |
| Elastic Beanstalk | `references/elasticbeanstalk/` | Applications, environments, versions, configuration templates, platforms |
| Lightsail | `references/lightsail/` | Instances, disks, load balancers, databases, containers, distributions, domains |
| Batch | `references/batch/` | Jobs, job definitions, job queues, compute environments, scheduling policies |
| App Runner | `references/apprunner/` | Services, connections, auto scaling, observability, VPC connectors, custom domains |
| Proton | `references/proton/` | Environments, services, templates, components, repositories, sync configs |
| Outposts | `references/outposts/` | Outpost management, sites, orders, capacity tasks, assets, catalog items |
| EC2 Image Builder | `references/imagebuilder/` | Image pipelines, recipes, components, images, infrastructure configs, lifecycle |
| Service Quotas | `references/service-quotas/` | Quota lookups, increase requests, templates, auto-management, utilization |
| Resource Groups | `references/resource-groups/` | Resource groups, queries, configurations, tag-based grouping, tag sync |
| Resource Groups Tagging API | `references/resourcegroupstaggingapi/` | Cross-service tag management, resource discovery by tag, compliance reporting |
| Config | `references/configservice/` | Config rules, conformance packs, recorders, delivery channels, remediation, aggregators |
| Organizations | `references/organizations/` | Organization management, accounts, OUs, policies (SCPs, tag, backup, AI opt-out) |
| Compute Optimizer | `references/compute-optimizer/` | Resource optimization recommendations for EC2, EBS, Lambda, ASG, ECS, RDS |
| ELB Classic | `references/elb/` | Classic Load Balancers, listeners, health checks, stickiness policies, tags |
| Service Catalog | `references/servicecatalog/` | Portfolios, products, provisioned products, constraints, service actions |
| Elastic Disaster Recovery | `references/drs/` | Source servers, recovery instances, replication, launch config, failback |
| Systems Manager Incidents | `references/ssm-incidents/` | Response plans, incidents, timeline events, contacts, engagements, rotations |
| Cost Explorer | `references/ce/` | Cost and usage, forecasts, anomalies, savings plans, reservations, rightsizing |
| Budgets | `references/budgets/` | Budgets, budget actions, notifications, subscribers |
| Cost and Usage Report | `references/cur/` | Report definitions, S3 delivery |
| Pricing | `references/pricing/` | Services, products, attribute values, price lists |
| Savings Plans | `references/savingsplans/` | Savings plans, rates, offerings |
| Billing | `references/billing/` | Billing views, source views, resource policies |
| Marketplace Catalog | `references/marketplace-catalog/` | Entities, change sets, resource policies |
| License Manager | `references/license-manager/` | Licenses, grants, configurations, Linux subscriptions, user subscriptions |
| AWS Health | `references/health/` | Events, affected entities, organization events |
| Payment Cryptography | `references/payment-cryptography/` | Keys, encryption, PIN/MAC operations, card validation |
| Location Services | `references/location/` | Maps, places, routes, geofences, trackers, API keys |
| Resource Explorer | `references/resource-explorer-2/` | Indexes, views, search, supported resource types |
| GameLift | `references/gamelift/` | Fleets, builds, game sessions, matchmaking, server groups |
| Well-Architected | `references/wellarchitected/` | Workloads, lenses, reviews, milestones, profiles |
| Resilience Hub | `references/resiliencehub/` | Apps, resiliency policies, assessments, recommendations |
| WorkSpaces | `references/workspaces/` | Virtual desktops, bundles, images, directories, pools, web portals |
| AppStream 2.0 | `references/appstream/` | Fleets, stacks, images, image builders, app blocks, applications |
| CodeCommit | `references/codecommit/` | Repositories, branches, commits, files, pull requests, approval rules, merges |
| CodeArtifact | `references/codeartifact/` | Domains, repositories, packages, package versions, package groups |
| CodeStar Connections | `references/codestar/` | Source provider connections, hosts, repository links, sync configs |
| Cloud9 | `references/cloud9/` | Cloud IDE environments, memberships, environment status |
| X-Ray | `references/xray/` | Traces, service graphs, sampling rules, groups, insights, indexing |
| CodeGuru | `references/codeguru/` | Code reviews, repository associations, recommendations, security scans |
| FIS | `references/fis/` | Experiment templates, experiments, actions, target resources, safety levers |
| Amplify | `references/amplify/` | Apps, branches, domain associations, jobs, deployments, webhooks |
| Device Farm | `references/devicefarm/` | Projects, device pools, runs, uploads, remote access, test grid |
| CloudWatch Synthetics | `references/synthetics/` | Canaries, canary runs, groups, runtime versions |
| Application Insights | `references/application-insights/` | Applications, components, log patterns, problems, workloads |
| Managed Grafana | `references/grafana/` | Workspaces, authentication, permissions, service accounts, API keys |
| Managed Prometheus | `references/amp/` | Workspaces, alert manager, rule groups, scrapers, logging |
| Redshift | `references/redshift/` | Provisioned clusters, snapshots, parameter groups, data sharing, Data API, Serverless |
| EMR | `references/emr/` | Clusters, instance fleets/groups, steps, scaling, studios, EMR on EKS, Serverless |
| Athena | `references/athena/` | Query execution, workgroups, named queries, data catalogs, notebooks, sessions |
| Glue | `references/glue/` | ETL jobs, crawlers, databases, tables, connections, workflows, schema registry |
| Kinesis | `references/kinesis/` | Data streams, shards, records, consumers, Kinesis Data Analytics |
| Firehose | `references/firehose/` | Delivery streams, data ingestion, destination management, encryption |
| OpenSearch | `references/opensearch/` | Domains, packages, VPC endpoints, indexes, Serverless collections/security |
| Neptune | `references/neptune/` | DB clusters, instances, snapshots, global clusters, Analytics graphs, import/export |
| Timestream | `references/timestream/` | Databases, tables, write records, queries, scheduled queries |
| QuickSight | `references/quicksight/` | Dashboards, analyses, templates, data sets, data sources, users, topics, embedding |
| Lake Formation | `references/lakeformation/` | Permissions, LF-tags, data cell filters, resource registration, transactions |
| MWAA | `references/mwaa/` | Managed Apache Airflow environments, CLI tokens, web login, REST API |
| MSK | `references/msk/` | Kafka clusters, configurations, topics, brokers, replicators, MSK Connect |
| Data Exchange | `references/dataexchange/` | Data sets, revisions, assets, jobs, data grants, event actions |
| Clean Rooms | `references/cleanrooms/` | Collaborations, memberships, configured tables, protected queries, ML models |
| Keyspaces | `references/keyspaces/` | Keyspaces, tables, user-defined types, auto scaling, point-in-time recovery |
| QLDB | `references/qldb/` | Ledgers, journal exports, journal streams, blocks, revisions (end of support) |
| DocumentDB | `references/docdb/` | Clusters, instances, snapshots, parameter groups, global clusters, Elastic Clusters |
| Data Pipeline | `references/datapipeline/` | Pipelines, definitions, objects, task management (legacy service) |
| FinSpace | `references/finspace/` | Kdb environments, databases, clusters, dataviews, changesets, scaling groups |
| GuardDuty | `references/guardduty/` | Detectors, findings, filters, IP sets, threat intel sets, malware protection, members |
| Security Hub | `references/securityhub/` | Hub management, findings, insights, standards, security controls, automation rules |
| Detective | `references/detective/` | Behavior graphs, members, investigations, data sources, organization |
| Macie | `references/macie/` | Classification jobs, findings, filters, allow lists, data identifiers, buckets, automated discovery |
| Inspector | `references/inspector/` | Enablement, findings, filters, coverage, CIS scans, code security, SBOM export |
| Firewall Manager | `references/fms/` | Admin accounts, policies, apps/protocols lists, resource sets, third-party firewalls |
| Shield | `references/shield/` | Subscription, protections, attacks, DRT access, proactive engagement, automatic response |
| Audit Manager | `references/auditmanager/` | Assessments, frameworks, controls, reports, evidence, delegations, insights |
| Security Lake | `references/securitylake/` | Data lake configuration, log sources, subscribers, organization |
| RAM | `references/ram/` | Resource shares, invitations, permissions, organizations |
| IAM Identity Center | `references/identity-center/` | Instances, permission sets, account assignments, applications, identity store |
| Directory Service | `references/ds/` | Directories, hybrid AD, trusts, conditional forwarders, snapshots, certificates |
| Verified Permissions | `references/verifiedpermissions/` | Policy stores, policies, policy templates, identity sources, authorization |
| Private CA | `references/acm-pca/` | Certificate authorities, certificates, audit reports, permissions, policies |
| CloudHSM | `references/cloudhsmv2/` | Clusters, HSMs, backups, resource policies |
| Network Firewall | `references/network-firewall/` | Firewalls, firewall policies, rule groups, TLS inspection, logging |
| Trusted Advisor | `references/trustedadvisor/` | Recommendations, organization recommendations, support cases |
| IAM Access Analyzer | `references/accessanalyzer/` | Analyzers, findings, archive rules, access previews, policy tools |
| Control Tower | `references/controltower/` | Landing zones, controls, baselines |
| Artifact | `references/artifact/` | Reports, agreements, account settings |

## Adding the Skill to Your Project

Claude Code loads skills from a `skills/` directory in your project root. Copy the single `aws-cli` skill directory into your project:

```bash
# From your project root
cp -r /path/to/awscliskills/skills/aws-cli skills/
```

That's it — one directory gives you all 121 services.

### Alternative: Git subtree (stays synced with updates)

```bash
git subtree add --prefix=skills/aws-cli https://github.com/chrishuffman5/awscliskills.git main --squash
```

### What gets loaded

- Claude Code reads `SKILL.md` and uses the YAML frontmatter (`name`, `description`) to decide when the skill is relevant to your current task.
- `SKILL.md` contains general CLI conventions (output formats, `--query`, pagination, waiters) and a service index table pointing to per-service overview files.
- Each service has a `references/<service>/` directory with an `overview.md` (service overview + workflows + command reference table), `index.md` (quick reference), and per-command-group files (e.g., `clusters.md`, `services.md`).
- Progressive disclosure: `SKILL.md` → `overview.md` → group files. Claude only loads the specific command groups needed, reducing token cost by ~70-80%.

## Skill File Format

```
skills/aws-cli/
  SKILL.md                        # General CLI conventions + service index table
  references/
    ecs/                          # One directory per service
      overview.md                 # Service overview + common workflows + command ref table
      index.md                    # Quick reference table + global options
      clusters.md                 # Per-command-group reference files
      services.md
      tasks.md
      ...
    ec2/
    ecr/
    ... (121 service directories)
```

**SKILL.md** contains:
- YAML frontmatter with `name` and `description` (used by Claude Code for skill matching)
- General CLI conventions (output formats, `--query`, pagination, waiters)
- Service index table mapping each service to its `overview.md`

**references/\<service\>/overview.md** contains:
- Service overview
- Quick reference with common workflow examples
- Covered command groups table
- Command reference table mapping each group to its reference file

**references/\<service\>/index.md** contains:
- Quick reference table of all subcommands
- Global options reference

**references/\<service\>/\<group\>.md** files each contain:
- All commands in that group with:
  - Description
  - Required parameters table (parameter, type, description)
  - Optional parameters table (parameter, type, default, description)
  - JSON output schema

This split structure means Claude only loads the specific command groups needed for a task, reducing token cost by ~70-80% compared to loading a monolithic reference file.
