# AWS CLI Skills for Claude Code

An installable [Claude Code](https://claude.ai/code) plugin providing comprehensive AWS CLI v2 command references — flags, types, defaults, and JSON output schemas — for 190 AWS services, sourced from official AWS documentation.

A lean **router skill** carries the CLI conventions and routes to one **sub-skill per service**, so Claude loads only the service you ask about instead of a 190-service catalog.

## Installation

### Claude Code (via plugin marketplace)

Register the marketplace, then install the plugin:

```
/plugin marketplace add chrishuffman5/awscliskills
/plugin install aws-cli@chrishuffman5
```

### Claude Code (manual)

```bash
git clone https://github.com/chrishuffman5/awscliskills.git .claude/plugins/aws-cli/
```

Auto-discovers the skill via `.claude-plugin/plugin.json`. Just describe what you need — no configuration required.

### Use the skill without installing the plugin

Claude Code also loads skills from a `skills/` directory in your project root. Copy the single `aws-cli` skill directory in:

```bash
# From your project root
cp -r /path/to/awscliskills/skills/aws-cli skills/
```

That's it — one directory gives you all 190 services. Or track it with git subtree so it stays synced with updates:

```bash
git subtree add --prefix=skills/aws-cli https://github.com/chrishuffman5/awscliskills.git main --squash
```

### Other platforms

```bash
# GitHub Copilot CLI
copilot plugin install chrishuffman5/awscliskills

# OpenAI Codex CLI
git clone https://github.com/chrishuffman5/awscliskills.git ~/.codex/skills/aws-cli/

# Gemini CLI (extension support still maturing)
gemini extensions install https://github.com/chrishuffman5/awscliskills
```

### Verify

Start a new session and ask something AWS-specific:

```
> How do I create an S3 bucket with a lifecycle policy via the CLI?
> List my ECS services and their running task counts.
> Which AWS service should I use for a CDN?
```

## How it works

- **Router** — `skills/aws-cli/SKILL.md` is the only skill registered with Claude. It holds the CLI conventions (output formats, `--query`, pagination, waiters, ARNs, env vars) plus a routing protocol, and is the only thing loaded into context at session start.
- **Per-service sub-skills** — each service is a bundled sub-skill at `skills/aws-cli/<aws-command>/SKILL.md` (e.g. `s3/`, `ec2/`, `dynamodb/`). The router reads only the one you need; the full catalog never loads up front.
- **Command groups** — within a service, files alongside `SKILL.md` (e.g. `instances.md`, `vpc.md`) hold the full per-command flags, types, defaults, and JSON output schemas.
- **Full lookup** — `skills/aws-cli/service-index.md` maps every friendly name to its sub-skill path, read only when the CLI service name isn't already known.

## Covered Services

| Service | Sub-skill | Scope |
|---------|-----------|-------|
| ACM | `skills/aws-cli/acm/` | Certificates, import/export, validation, tags, account configuration |
| Amazon MQ | `skills/aws-cli/mq/` | ActiveMQ and RabbitMQ brokers, configurations, users, engine types |
| Amplify | `skills/aws-cli/amplify/` | Apps, branches, domain associations, jobs, deployments, webhooks |
| API Gateway | `skills/aws-cli/apigateway/` | REST APIs, HTTP APIs, resources, methods, stages, authorizers, API keys, usage plans |
| App Mesh | `skills/aws-cli/appmesh/` | Meshes, virtual nodes, virtual services, virtual routers, routes, virtual gateways |
| App Runner | `skills/aws-cli/apprunner/` | Services, connections, auto scaling, observability, VPC connectors, custom domains |
| AppConfig | `skills/aws-cli/appconfig/` | Feature flags, configuration profiles, deployment strategies, environments, extensions, runtime data |
| AppStream 2.0 | `skills/aws-cli/appstream/` | Fleets, stacks, images, image builders, app blocks, applications |
| AppSync | `skills/aws-cli/appsync/` | GraphQL and Events APIs, data sources, resolvers, functions, types, API keys, caching, domain names, merged APIs |
| Application Auto Scaling | `skills/aws-cli/application-autoscaling/` | Scalable targets, scaling policies, scheduled actions, predictive scaling |
| Application Discovery | `skills/aws-cli/discovery/` | Agents, configurations, applications, export/import tasks |
| Application Insights | `skills/aws-cli/application-insights/` | Applications, components, log patterns, problems, workloads |
| Artifact | `skills/aws-cli/artifact/` | Reports, agreements, account settings |
| Athena | `skills/aws-cli/athena/` | Query execution, workgroups, named queries, data catalogs, notebooks, sessions |
| Audit Manager | `skills/aws-cli/auditmanager/` | Assessments, frameworks, controls, reports, evidence, delegations, insights |
| Auto Scaling | `skills/aws-cli/autoscaling/` | Auto Scaling groups, launch configs, scaling policies, lifecycle hooks, instance refresh |
| AWS Health | `skills/aws-cli/health/` | Events, affected entities, organization events |
| Backup | `skills/aws-cli/backup/` | Backup plans, vaults, jobs, recovery points, frameworks, reports, Backup Gateway |
| Batch | `skills/aws-cli/batch/` | Jobs, job definitions, job queues, compute environments, scheduling policies |
| Bedrock | `skills/aws-cli/bedrock/` | Foundation models, custom models, guardrails, inference profiles, agents, knowledge bases, prompts, flows, RAG, runtime inference |
| Billing | `skills/aws-cli/billing/` | Billing views, source views, resource policies |
| Budgets | `skills/aws-cli/budgets/` | Budgets, budget actions, notifications, subscribers |
| Chime SDK | `skills/aws-cli/chime/` | App instances, meetings, attendees, messaging channels, voice connectors, phone numbers, SIP, voice profiles |
| Clean Rooms | `skills/aws-cli/cleanrooms/` | Collaborations, memberships, configured tables, protected queries, ML models |
| Cloud9 | `skills/aws-cli/cloud9/` | Cloud IDE environments, memberships, environment status |
| Cloud Map | `skills/aws-cli/servicediscovery/` | Namespaces, services, instances, service discovery, health status |
| CloudFormation | `skills/aws-cli/cloudformation/` | Stacks, change sets, stack sets, drift detection, resource scanning, type registry |
| CloudFront | `skills/aws-cli/cloudfront/` | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| CloudHSM | `skills/aws-cli/cloudhsmv2/` | Clusters, HSMs, backups, resource policies |
| CloudTrail | `skills/aws-cli/cloudtrail/` | Trails, event selectors, event data stores, queries, channels, imports |
| CloudWatch | `skills/aws-cli/cloudwatch/` | Metrics, alarms, dashboards, log groups, log streams, metric filters, Insights queries |
| CloudWatch Evidently | `skills/aws-cli/evidently/` | Feature flags, A/B testing, projects, features, experiments, launches, segments |
| CloudWatch Network Monitor | `skills/aws-cli/networkmonitor/` | Network monitors, probes, performance monitoring |
| CloudWatch RUM | `skills/aws-cli/rum/` | Real user monitoring, app monitors, custom metrics, resource policies |
| CloudWatch Synthetics | `skills/aws-cli/synthetics/` | Canaries, canary runs, groups, runtime versions |
| CodeArtifact | `skills/aws-cli/codeartifact/` | Domains, repositories, packages, package versions, package groups |
| CodeBuild | `skills/aws-cli/codebuild/` | Projects, builds, build batches, report groups, source credentials, webhooks, fleets |
| CodeCommit | `skills/aws-cli/codecommit/` | Repositories, branches, commits, files, pull requests, approval rules, merges |
| CodeDeploy | `skills/aws-cli/codedeploy/` | Applications, deployment groups, deployments, deployment configs, revisions |
| CodeGuru | `skills/aws-cli/codeguru/` | Code reviews, repository associations, recommendations, security scans |
| CodePipeline | `skills/aws-cli/codepipeline/` | Pipelines, stages, actions, action types, webhooks |
| CodeStar Connections | `skills/aws-cli/codestar/` | Source provider connections, hosts, repository links, sync configs |
| Cognito | `skills/aws-cli/cognito/` | User pools, user pool clients, users, groups, identity providers, identity pools, MFA |
| Comprehend | `skills/aws-cli/comprehend/` | NLP text analysis, entity detection, sentiment, key phrases, language detection, document classification, entity recognizers, flywheels |
| Comprehend Medical | `skills/aws-cli/comprehendmedical/` | Medical entity detection, PHI detection, ICD-10-CM/RxNorm/SNOMED CT code inference, batch processing |
| Compute Optimizer | `skills/aws-cli/compute-optimizer/` | Resource optimization recommendations for EC2, EBS, Lambda, ASG, ECS, RDS |
| Config | `skills/aws-cli/configservice/` | Config rules, conformance packs, recorders, delivery channels, remediation, aggregators |
| Connect | `skills/aws-cli/connect/` | Contact center instances, contact flows, contacts, users, queues, routing profiles, evaluation forms, metrics, cases |
| Control Tower | `skills/aws-cli/controltower/` | Landing zones, controls, baselines |
| Cost and Usage Report | `skills/aws-cli/cur/` | Report definitions, S3 delivery |
| Cost Explorer | `skills/aws-cli/ce/` | Cost and usage, forecasts, anomalies, savings plans, reservations, rightsizing |
| Data Exchange | `skills/aws-cli/dataexchange/` | Data sets, revisions, assets, jobs, data grants, event actions |
| Data Pipeline | `skills/aws-cli/datapipeline/` | Pipelines, definitions, objects, task management (legacy service) |
| DataSync | `skills/aws-cli/datasync/` | Agents, tasks, locations (S3, EFS, FSx, NFS, SMB, HDFS, Azure Blob) |
| Detective | `skills/aws-cli/detective/` | Behavior graphs, members, investigations, data sources, organization |
| Device Farm | `skills/aws-cli/devicefarm/` | Projects, device pools, runs, uploads, remote access, test grid |
| Direct Connect | `skills/aws-cli/directconnect/` | Connections, gateways, virtual interfaces, LAGs, BGP peering, MACsec |
| Directory Service | `skills/aws-cli/ds/` | Directories, hybrid AD, trusts, conditional forwarders, snapshots, certificates |
| DMS | `skills/aws-cli/dms/` | Replication instances, endpoints, tasks, serverless replication, data migrations |
| DocumentDB | `skills/aws-cli/docdb/` | Clusters, instances, snapshots, parameter groups, global clusters, Elastic Clusters |
| DynamoDB | `skills/aws-cli/dynamodb/` | Tables, items, indexes, queries, scans, streams, backups, global tables, TTL |
| EC2 | `skills/aws-cli/ec2/` | Instances, VPCs, subnets, security groups, key pairs, AMIs, launch templates, auto scaling |
| EC2 Image Builder | `skills/aws-cli/imagebuilder/` | Image pipelines, recipes, components, images, infrastructure configs, lifecycle |
| ECR | `skills/aws-cli/ecr/` | Repositories, images, lifecycle policies, scanning, authentication, registry |
| ECS | `skills/aws-cli/ecs/` | Clusters, services, tasks, task definitions, container instances, capacity providers |
| EFS | `skills/aws-cli/efs/` | File systems, mount targets, access points, replication, lifecycle |
| EKS | `skills/aws-cli/eks/` | Clusters, node groups, Fargate profiles, add-ons, access management, Pod Identity |
| ELB Classic | `skills/aws-cli/elb/` | Classic Load Balancers, listeners, health checks, stickiness policies, tags |
| ELBv2 | `skills/aws-cli/elbv2/` | ALBs, NLBs, target groups, listeners, rules, health checks, SSL certificates |
| ElastiCache | `skills/aws-cli/elasticache/` | Clusters, replication groups, parameter groups, snapshots, users, serverless |
| Elastic Beanstalk | `skills/aws-cli/elasticbeanstalk/` | Applications, environments, versions, configuration templates, platforms |
| Elastic Disaster Recovery | `skills/aws-cli/drs/` | Source servers, recovery instances, replication, launch config, failback |
| Elastic Transcoder | `skills/aws-cli/elastictranscoder/` | Pipelines, presets, transcoding jobs (legacy service) |
| EMR | `skills/aws-cli/emr/` | Clusters, instance fleets/groups, steps, scaling, studios, EMR on EKS, Serverless |
| Entity Resolution | `skills/aws-cli/entityresolution/` | Entity matching workflows, ID mapping, ID namespaces, schema mappings, provider services |
| EventBridge | `skills/aws-cli/eventbridge/` | Event buses, rules, targets, archives, replays, connections, API destinations, pipes |
| EventBridge Pipes | `skills/aws-cli/pipes/` | Point-to-point event pipes, source-target connections, filtering, enrichment |
| EventBridge Scheduler | `skills/aws-cli/scheduler/` | One-time and recurring schedules, schedule groups, universal target invocation |
| Firehose | `skills/aws-cli/firehose/` | Delivery streams, data ingestion, destination management, encryption |
| FinSpace | `skills/aws-cli/finspace/` | Kdb environments, databases, clusters, dataviews, changesets, scaling groups |
| Firewall Manager | `skills/aws-cli/fms/` | Admin accounts, policies, apps/protocols lists, resource sets, third-party firewalls |
| FIS | `skills/aws-cli/fis/` | Experiment templates, experiments, actions, target resources, safety levers |
| Forecast | `skills/aws-cli/forecast/` | Time-series forecasting, datasets, AutoPredictors, forecasts, what-if analysis, explainability, monitors, queries |
| FSx | `skills/aws-cli/fsx/` | File systems (Windows/Lustre/ONTAP/OpenZFS), volumes, snapshots, data repository |
| GameLift | `skills/aws-cli/gamelift/` | Fleets, builds, game sessions, matchmaking, server groups |
| Glue | `skills/aws-cli/glue/` | ETL jobs, crawlers, databases, tables, connections, workflows, schema registry |
| Global Accelerator | `skills/aws-cli/globalaccelerator/` | Accelerators, listeners, endpoint groups, custom routing, BYOIP |
| Greengrass v2 | `skills/aws-cli/greengrassv2/` | Core devices, components, deployments, client device associations |
| GuardDuty | `skills/aws-cli/guardduty/` | Detectors, findings, filters, IP sets, threat intel sets, malware protection, members |
| HealthLake | `skills/aws-cli/healthlake/` | FHIR R4 data stores, import/export jobs, SSE encryption, SMART on FHIR authorization |
| IAM | `skills/aws-cli/iam/` | Users, groups, roles, policies, instance profiles, access keys, MFA, identity providers |
| IAM Access Analyzer | `skills/aws-cli/accessanalyzer/` | Analyzers, findings, archive rules, access previews, policy tools |
| IAM Identity Center | `skills/aws-cli/identity-center/` | Instances, permission sets, account assignments, applications, identity store |
| Inspector | `skills/aws-cli/inspector/` | Enablement, findings, filters, coverage, CIS scans, code security, SBOM export |
| Internet Monitor | `skills/aws-cli/internetmonitor/` | Monitors, health events, internet events, queries |
| IoT Core | `skills/aws-cli/iot/` | Things, certificates, policies, rules, shadows, jobs, fleet indexing, security auditing, OTA updates |
| IoT Device Advisor | `skills/aws-cli/iotdeviceadvisor/` | Suite definitions, suite runs, test reports, endpoint management |
| IoT Events | `skills/aws-cli/iotevents/` | Detector models, inputs, alarm models, runtime detector and alarm operations |
| IoT FleetWise | `skills/aws-cli/iotfleetwise/` | Signal catalogs, model manifests, vehicles, campaigns, decoder manifests, fleets |
| IoT SiteWise | `skills/aws-cli/iotsitewise/` | Asset models, assets, portals, dashboards, gateways, projects, time series data |
| IoT TwinMaker | `skills/aws-cli/iottwinmaker/` | Workspaces, entities, component types, scenes, sync jobs, metadata transfer |
| IoT Wireless | `skills/aws-cli/iotwireless/` | LoRaWAN/Sidewalk devices, wireless gateways, destinations, multicast, FUOTA tasks |
| IVS | `skills/aws-cli/ivs/` | Channels, streams, stages, compositions, participants, chat rooms, recording |
| Kendra | `skills/aws-cli/kendra/` | Intelligent search indexes, data sources, FAQs, thesauri, query suggestions, featured results, experiences, ranking |
| Keyspaces | `skills/aws-cli/keyspaces/` | Keyspaces, tables, user-defined types, auto scaling, point-in-time recovery |
| Kinesis | `skills/aws-cli/kinesis/` | Data streams, shards, records, consumers, Kinesis Data Analytics |
| KMS | `skills/aws-cli/kms/` | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| Lake Formation | `skills/aws-cli/lakeformation/` | Permissions, LF-tags, data cell filters, resource registration, transactions |
| Lambda | `skills/aws-cli/lambda/` | Functions, layers, event source mappings, aliases, versions, concurrency, URLs |
| Lex v2 | `skills/aws-cli/lex/` | Conversational AI bots, intents, slots, locales, custom vocabulary, analytics |
| License Manager | `skills/aws-cli/license-manager/` | Licenses, grants, configurations, Linux subscriptions, user subscriptions |
| Lightsail | `skills/aws-cli/lightsail/` | Instances, disks, load balancers, databases, containers, distributions, domains |
| Lookout for Equipment | `skills/aws-cli/lookoutequipment/` | Industrial equipment anomaly detection, datasets, models, inference schedulers, labels, retraining |
| Lookout for Metrics | `skills/aws-cli/lookoutmetrics/` | Metric anomaly detection, detectors, metric sets, alerts, anomaly groups |
| Lookout for Vision | `skills/aws-cli/lookoutvision/` | Visual anomaly detection, projects, models, datasets, model packaging |
| Location Services | `skills/aws-cli/location/` | Maps, places, routes, geofences, trackers, API keys |
| Macie | `skills/aws-cli/macie/` | Classification jobs, findings, filters, allow lists, data identifiers, buckets, automated discovery |
| Managed Grafana | `skills/aws-cli/grafana/` | Workspaces, authentication, permissions, service accounts, API keys |
| Managed Prometheus | `skills/aws-cli/amp/` | Workspaces, alert manager, rule groups, scrapers, logging |
| Marketplace Catalog | `skills/aws-cli/marketplace-catalog/` | Entities, change sets, resource policies |
| MediaConnect | `skills/aws-cli/mediaconnect/` | Flows, sources, outputs, entitlements, media streams, bridges, gateways |
| MediaConvert | `skills/aws-cli/mediaconvert/` | Transcoding jobs, job templates, output presets, queues, policies |
| MediaLive | `skills/aws-cli/medialive/` | Channels, inputs, multiplexes, clusters, networks, schedules, reservations, signal maps |
| MediaPackage | `skills/aws-cli/mediapackage/` | Channel groups, channels, origin endpoints, harvest jobs, VOD packaging |
| MediaStore | `skills/aws-cli/mediastore/` | Containers, policies, CORS, lifecycle, object operations |
| Migration | `skills/aws-cli/migration/` | MGN source servers, replication, cutover, Migration Hub Config, Orchestrator |
| MSK | `skills/aws-cli/msk/` | Kafka clusters, configurations, topics, brokers, replicators, MSK Connect |
| MWAA | `skills/aws-cli/mwaa/` | Managed Apache Airflow environments, CLI tokens, web login, REST API |
| Neptune | `skills/aws-cli/neptune/` | DB clusters, instances, snapshots, global clusters, Analytics graphs, import/export |
| Network Firewall | `skills/aws-cli/network-firewall/` | Firewalls, firewall policies, rule groups, TLS inspection, logging |
| Network Manager | `skills/aws-cli/networkmanager/` | Global networks, core networks, sites, devices, attachments, route analysis |
| OpenSearch | `skills/aws-cli/opensearch/` | Domains, packages, VPC endpoints, indexes, Serverless collections/security |
| Organizations | `skills/aws-cli/organizations/` | Organization management, accounts, OUs, policies (SCPs, tag, backup, AI opt-out) |
| Outposts | `skills/aws-cli/outposts/` | Outpost management, sites, orders, capacity tasks, assets, catalog items |
| Payment Cryptography | `skills/aws-cli/payment-cryptography/` | Keys, encryption, PIN/MAC operations, card validation |
| Personalize | `skills/aws-cli/personalize/` | ML recommendations, dataset groups, schemas, solutions, campaigns, recommenders, batch jobs, event trackers |
| Pinpoint | `skills/aws-cli/pinpoint/` | Customer engagement campaigns, journeys, segments, messaging channels, templates, endpoints, SMS/voice v2 |
| Polly | `skills/aws-cli/polly/` | Text-to-speech synthesis, speech marks, lexicons, voice descriptions |
| Pricing | `skills/aws-cli/pricing/` | Services, products, attribute values, price lists |
| Private CA | `skills/aws-cli/acm-pca/` | Certificate authorities, certificates, audit reports, permissions, policies |
| Proton | `skills/aws-cli/proton/` | Environments, services, templates, components, repositories, sync configs |
| Q Connect | `skills/aws-cli/qconnect/` | AI-powered contact center assistant, knowledge bases, AI agents, guardrails, prompts, sessions |
| QLDB | `skills/aws-cli/qldb/` | Ledgers, journal exports, journal streams, blocks, revisions (end of support) |
| QuickSight | `skills/aws-cli/quicksight/` | Dashboards, analyses, templates, data sets, data sources, users, topics, embedding |
| RAM | `skills/aws-cli/ram/` | Resource shares, invitations, permissions, organizations |
| RDS | `skills/aws-cli/rds/` | DB instances, Aurora clusters, snapshots, parameter groups, subnet groups, replicas, proxies |
| Redshift | `skills/aws-cli/redshift/` | Provisioned clusters, snapshots, parameter groups, data sharing, Data API, Serverless |
| Rekognition | `skills/aws-cli/rekognition/` | Image/video analysis, face detection, collections, users, liveness, stream processors, media analysis, custom labels projects |
| Resilience Hub | `skills/aws-cli/resiliencehub/` | Apps, resiliency policies, assessments, recommendations |
| Resource Explorer | `skills/aws-cli/resource-explorer-2/` | Indexes, views, search, supported resource types |
| Resource Groups | `skills/aws-cli/resource-groups/` | Resource groups, queries, configurations, tag-based grouping, tag sync |
| Resource Groups Tagging API | `skills/aws-cli/resourcegroupstaggingapi/` | Cross-service tag management, resource discovery by tag, compliance reporting |
| Route 53 | `skills/aws-cli/route53/` | Hosted zones, DNS records, health checks, routing policies, domain registration |
| Route 53 Recovery | `skills/aws-cli/route53-recovery/` | Recovery clusters, control panels, routing controls, safety rules, readiness checks |
| Route 53 Resolver | `skills/aws-cli/route53resolver/` | Resolver endpoints, rules, DNS Firewall, query logging, DNSSEC, Profiles |
| S3 | `skills/aws-cli/s3/` | Buckets, objects, storage classes, lifecycle, versioning, website hosting, presigned URLs |
| S3 Control | `skills/aws-cli/s3control/` | Access points, Object Lambda, Access Grants, Batch Operations, Storage Lens |
| S3 Outposts | `skills/aws-cli/s3outposts/` | Endpoints, shared endpoints, Outposts with S3 capability |
| SageMaker | `skills/aws-cli/sagemaker/` | Training jobs, models, endpoints, processing, hyperparameter tuning, AutoML, pipelines, experiments, Feature Store, model registry, monitoring, notebooks, HyperPod clusters |
| SageMaker A2I | `skills/aws-cli/sagemaker-a2i-runtime/` | Human-in-the-loop review, human loops, flow definitions |
| Savings Plans | `skills/aws-cli/savingsplans/` | Savings plans, rates, offerings |
| Security Hub | `skills/aws-cli/securityhub/` | Hub management, findings, insights, standards, security controls, automation rules |
| Security Lake | `skills/aws-cli/securitylake/` | Data lake configuration, log sources, subscribers, organization |
| Secrets Manager | `skills/aws-cli/secretsmanager/` | Secrets, versions, rotation, replication, resource policies, batch retrieval |
| Service Catalog | `skills/aws-cli/servicecatalog/` | Portfolios, products, provisioned products, constraints, service actions |
| Service Catalog AppRegistry | `skills/aws-cli/servicecatalog-appregistry/` | Applications, attribute groups, resource associations, configuration |
| Service Quotas | `skills/aws-cli/service-quotas/` | Quota lookups, increase requests, templates, auto-management, utilization |
| SES v2 | `skills/aws-cli/sesv2/` | Email identities, configuration sets, contact lists, templates, sending, suppression |
| Shield | `skills/aws-cli/shield/` | Subscription, protections, attacks, DRT access, proactive engagement, automatic response |
| Snow Family | `skills/aws-cli/snowball/` | Snowball/Snowball Edge/Snowcone jobs, clusters, addresses, shipping |
| SNS | `skills/aws-cli/sns/` | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | `skills/aws-cli/sqs/` | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| STS | `skills/aws-cli/sts/` | Assume role, session tokens, federation, caller identity |
| Step Functions | `skills/aws-cli/stepfunctions/` | State machines, executions, activities, map runs, versions |
| Storage Gateway | `skills/aws-cli/storagegateway/` | Gateways, file shares, iSCSI volumes, tape gateway, cache, bandwidth |
| SWF | `skills/aws-cli/swf/` | Simple Workflow Service, domains, workflow types, activity types, executions, tasks |
| Systems Manager | `skills/aws-cli/ssm/` | Parameter Store, documents, Run Command, Session Manager, patch baselines, state manager |
| Systems Manager Incidents | `skills/aws-cli/ssm-incidents/` | Response plans, incidents, timeline events, contacts, engagements, rotations |
| Textract | `skills/aws-cli/textract/` | Document text detection, form/table analysis, expense analysis, ID analysis, lending analysis, custom adapters |
| Timestream | `skills/aws-cli/timestream/` | Databases, tables, write records, queries, scheduled queries |
| Transcribe | `skills/aws-cli/transcribe/` | Speech-to-text transcription, call analytics, medical transcription, custom vocabularies, language models |
| Transfer Family | `skills/aws-cli/transfer/` | SFTP/FTPS/FTP/AS2 servers, users, connectors, agreements, workflows, web apps |
| Translate | `skills/aws-cli/translate/` | Language translation, batch translation, custom terminologies, parallel data |
| Trusted Advisor | `skills/aws-cli/trustedadvisor/` | Recommendations, organization recommendations, support cases |
| Verified Permissions | `skills/aws-cli/verifiedpermissions/` | Policy stores, policies, policy templates, identity sources, authorization |
| WAF v2 | `skills/aws-cli/wafv2/` | Web ACLs, rule groups, IP sets, regex pattern sets, logging |
| Well-Architected | `skills/aws-cli/wellarchitected/` | Workloads, lenses, reviews, milestones, profiles |
| WorkMail | `skills/aws-cli/workmail/` | Organizations, users, groups, resources, mail domains, access control, impersonation, mobile devices |
| WorkSpaces | `skills/aws-cli/workspaces/` | Virtual desktops, bundles, images, directories, pools, web portals |
| X-Ray | `skills/aws-cli/xray/` | Traces, service graphs, sampling rules, groups, insights, indexing |

## Skill File Format

```
skills/aws-cli/
  SKILL.md              # Router: CLI conventions + routing protocol (the only registered skill)
  service-index.md      # Full friendly-name -> sub-skill lookup (read on demand)
  ec2/                  # One sub-skill directory per service (named after the `aws` command)
    SKILL.md            # Service overview + workflows + command-group index (+ YAML frontmatter)
    index.md            # Quick reference table + global options
    instances.md        # Per-command-group reference files
    vpc.md
    ...
  s3/
  dynamodb/
  ... (190 service directories)
```

**SKILL.md (router)** contains:
- YAML frontmatter with `name` and `description` (used by Claude Code for skill matching)
- General CLI conventions (output formats, `--query`, pagination, waiters, ARNs, env vars)
- A routing protocol: derive `<service>/SKILL.md` from the `aws` command, or consult `service-index.md`

**\<service\>/SKILL.md** contains:
- YAML frontmatter (`name: aws-<service>`, `description`)
- Service overview and common workflow examples
- Covered command groups, and a command reference table mapping each group to its file

**\<service\>/index.md** contains:
- Quick reference table of all subcommands
- Global options reference

**\<service\>/\<group\>.md** files each contain:
- All commands in that group with description, required/optional parameter tables, and JSON output schema

Progressive disclosure — router -> `<service>/SKILL.md` -> group files — means Claude loads only the specific command groups needed for a task, instead of a monolithic reference.