# AWS CLI Skills for Claude Code

A unified AWS CLI v2 reference skill for [Claude Code](https://claude.ai/code). Provides comprehensive command references — flags, types, defaults, and JSON output schemas — for 190 AWS services, sourced from official AWS documentation.

## Covered Services

| Service | Reference | Scope |
|---------|-----------|-------|
| ACM | `references/acm/` | Certificates, import/export, validation, tags, account configuration |
| Amazon MQ | `references/mq/` | ActiveMQ and RabbitMQ brokers, configurations, users, engine types |
| Amplify | `references/amplify/` | Apps, branches, domain associations, jobs, deployments, webhooks |
| API Gateway | `references/apigateway/` | REST APIs, HTTP APIs, resources, methods, stages, authorizers, API keys, usage plans |
| App Mesh | `references/appmesh/` | Meshes, virtual nodes, virtual services, virtual routers, routes, virtual gateways |
| App Runner | `references/apprunner/` | Services, connections, auto scaling, observability, VPC connectors, custom domains |
| AppConfig | `references/appconfig/` | Feature flags, configuration profiles, deployment strategies, environments, extensions, runtime data |
| AppStream 2.0 | `references/appstream/` | Fleets, stacks, images, image builders, app blocks, applications |
| AppSync | `references/appsync/` | GraphQL and Events APIs, data sources, resolvers, functions, types, API keys, caching, domain names, merged APIs |
| Application Auto Scaling | `references/application-autoscaling/` | Scalable targets, scaling policies, scheduled actions, predictive scaling |
| Application Discovery | `references/discovery/` | Agents, configurations, applications, export/import tasks |
| Application Insights | `references/application-insights/` | Applications, components, log patterns, problems, workloads |
| Artifact | `references/artifact/` | Reports, agreements, account settings |
| Athena | `references/athena/` | Query execution, workgroups, named queries, data catalogs, notebooks, sessions |
| Audit Manager | `references/auditmanager/` | Assessments, frameworks, controls, reports, evidence, delegations, insights |
| Auto Scaling | `references/autoscaling/` | Auto Scaling groups, launch configs, scaling policies, lifecycle hooks, instance refresh |
| AWS Health | `references/health/` | Events, affected entities, organization events |
| Backup | `references/backup/` | Backup plans, vaults, jobs, recovery points, frameworks, reports, Backup Gateway |
| Batch | `references/batch/` | Jobs, job definitions, job queues, compute environments, scheduling policies |
| Bedrock | `references/bedrock/` | Foundation models, custom models, guardrails, inference profiles, agents, knowledge bases, prompts, flows, RAG, runtime inference |
| Billing | `references/billing/` | Billing views, source views, resource policies |
| Budgets | `references/budgets/` | Budgets, budget actions, notifications, subscribers |
| Chime SDK | `references/chime/` | App instances, meetings, attendees, messaging channels, voice connectors, phone numbers, SIP, voice profiles |
| Clean Rooms | `references/cleanrooms/` | Collaborations, memberships, configured tables, protected queries, ML models |
| Cloud9 | `references/cloud9/` | Cloud IDE environments, memberships, environment status |
| Cloud Map | `references/servicediscovery/` | Namespaces, services, instances, service discovery, health status |
| CloudFormation | `references/cloudformation/` | Stacks, change sets, stack sets, drift detection, resource scanning, type registry |
| CloudFront | `references/cloudfront/` | Distributions, origins, cache behaviors, invalidations, functions, origin access control |
| CloudHSM | `references/cloudhsmv2/` | Clusters, HSMs, backups, resource policies |
| CloudTrail | `references/cloudtrail/` | Trails, event selectors, event data stores, queries, channels, imports |
| CloudWatch | `references/cloudwatch/` | Metrics, alarms, dashboards, log groups, log streams, metric filters, Insights queries |
| CloudWatch Evidently | `references/evidently/` | Feature flags, A/B testing, projects, features, experiments, launches, segments |
| CloudWatch Network Monitor | `references/networkmonitor/` | Network monitors, probes, performance monitoring |
| CloudWatch RUM | `references/rum/` | Real user monitoring, app monitors, custom metrics, resource policies |
| CloudWatch Synthetics | `references/synthetics/` | Canaries, canary runs, groups, runtime versions |
| CodeArtifact | `references/codeartifact/` | Domains, repositories, packages, package versions, package groups |
| CodeBuild | `references/codebuild/` | Projects, builds, build batches, report groups, source credentials, webhooks, fleets |
| CodeCommit | `references/codecommit/` | Repositories, branches, commits, files, pull requests, approval rules, merges |
| CodeDeploy | `references/codedeploy/` | Applications, deployment groups, deployments, deployment configs, revisions |
| CodeGuru | `references/codeguru/` | Code reviews, repository associations, recommendations, security scans |
| CodePipeline | `references/codepipeline/` | Pipelines, stages, actions, action types, webhooks |
| CodeStar Connections | `references/codestar/` | Source provider connections, hosts, repository links, sync configs |
| Cognito | `references/cognito/` | User pools, user pool clients, users, groups, identity providers, identity pools, MFA |
| Comprehend | `references/comprehend/` | NLP text analysis, entity detection, sentiment, key phrases, language detection, document classification, entity recognizers, flywheels |
| Comprehend Medical | `references/comprehendmedical/` | Medical entity detection, PHI detection, ICD-10-CM/RxNorm/SNOMED CT code inference, batch processing |
| Compute Optimizer | `references/compute-optimizer/` | Resource optimization recommendations for EC2, EBS, Lambda, ASG, ECS, RDS |
| Config | `references/configservice/` | Config rules, conformance packs, recorders, delivery channels, remediation, aggregators |
| Connect | `references/connect/` | Contact center instances, contact flows, contacts, users, queues, routing profiles, evaluation forms, metrics, cases |
| Control Tower | `references/controltower/` | Landing zones, controls, baselines |
| Cost and Usage Report | `references/cur/` | Report definitions, S3 delivery |
| Cost Explorer | `references/ce/` | Cost and usage, forecasts, anomalies, savings plans, reservations, rightsizing |
| Data Exchange | `references/dataexchange/` | Data sets, revisions, assets, jobs, data grants, event actions |
| Data Pipeline | `references/datapipeline/` | Pipelines, definitions, objects, task management (legacy service) |
| DataSync | `references/datasync/` | Agents, tasks, locations (S3, EFS, FSx, NFS, SMB, HDFS, Azure Blob) |
| Detective | `references/detective/` | Behavior graphs, members, investigations, data sources, organization |
| Device Farm | `references/devicefarm/` | Projects, device pools, runs, uploads, remote access, test grid |
| Direct Connect | `references/directconnect/` | Connections, gateways, virtual interfaces, LAGs, BGP peering, MACsec |
| Directory Service | `references/ds/` | Directories, hybrid AD, trusts, conditional forwarders, snapshots, certificates |
| DMS | `references/dms/` | Replication instances, endpoints, tasks, serverless replication, data migrations |
| DocumentDB | `references/docdb/` | Clusters, instances, snapshots, parameter groups, global clusters, Elastic Clusters |
| DynamoDB | `references/dynamodb/` | Tables, items, indexes, queries, scans, streams, backups, global tables, TTL |
| EC2 | `references/ec2/` | Instances, VPCs, subnets, security groups, key pairs, AMIs, launch templates, auto scaling |
| EC2 Image Builder | `references/imagebuilder/` | Image pipelines, recipes, components, images, infrastructure configs, lifecycle |
| ECR | `references/ecr/` | Repositories, images, lifecycle policies, scanning, authentication, registry |
| ECS | `references/ecs/` | Clusters, services, tasks, task definitions, container instances, capacity providers |
| EFS | `references/efs/` | File systems, mount targets, access points, replication, lifecycle |
| EKS | `references/eks/` | Clusters, node groups, Fargate profiles, add-ons, access management, Pod Identity |
| ELB Classic | `references/elb/` | Classic Load Balancers, listeners, health checks, stickiness policies, tags |
| ELBv2 | `references/elbv2/` | ALBs, NLBs, target groups, listeners, rules, health checks, SSL certificates |
| ElastiCache | `references/elasticache/` | Clusters, replication groups, parameter groups, snapshots, users, serverless |
| Elastic Beanstalk | `references/elasticbeanstalk/` | Applications, environments, versions, configuration templates, platforms |
| Elastic Disaster Recovery | `references/drs/` | Source servers, recovery instances, replication, launch config, failback |
| Elastic Transcoder | `references/elastictranscoder/` | Pipelines, presets, transcoding jobs (legacy service) |
| EMR | `references/emr/` | Clusters, instance fleets/groups, steps, scaling, studios, EMR on EKS, Serverless |
| Entity Resolution | `references/entityresolution/` | Entity matching workflows, ID mapping, ID namespaces, schema mappings, provider services |
| EventBridge | `references/eventbridge/` | Event buses, rules, targets, archives, replays, connections, API destinations, pipes |
| EventBridge Pipes | `references/pipes/` | Point-to-point event pipes, source-target connections, filtering, enrichment |
| EventBridge Scheduler | `references/scheduler/` | One-time and recurring schedules, schedule groups, universal target invocation |
| Firehose | `references/firehose/` | Delivery streams, data ingestion, destination management, encryption |
| FinSpace | `references/finspace/` | Kdb environments, databases, clusters, dataviews, changesets, scaling groups |
| Firewall Manager | `references/fms/` | Admin accounts, policies, apps/protocols lists, resource sets, third-party firewalls |
| FIS | `references/fis/` | Experiment templates, experiments, actions, target resources, safety levers |
| Forecast | `references/forecast/` | Time-series forecasting, datasets, AutoPredictors, forecasts, what-if analysis, explainability, monitors, queries |
| FSx | `references/fsx/` | File systems (Windows/Lustre/ONTAP/OpenZFS), volumes, snapshots, data repository |
| GameLift | `references/gamelift/` | Fleets, builds, game sessions, matchmaking, server groups |
| Glue | `references/glue/` | ETL jobs, crawlers, databases, tables, connections, workflows, schema registry |
| Global Accelerator | `references/globalaccelerator/` | Accelerators, listeners, endpoint groups, custom routing, BYOIP |
| Greengrass v2 | `references/greengrassv2/` | Core devices, components, deployments, client device associations |
| GuardDuty | `references/guardduty/` | Detectors, findings, filters, IP sets, threat intel sets, malware protection, members |
| HealthLake | `references/healthlake/` | FHIR R4 data stores, import/export jobs, SSE encryption, SMART on FHIR authorization |
| IAM | `references/iam/` | Users, groups, roles, policies, instance profiles, access keys, MFA, identity providers |
| IAM Access Analyzer | `references/accessanalyzer/` | Analyzers, findings, archive rules, access previews, policy tools |
| IAM Identity Center | `references/identity-center/` | Instances, permission sets, account assignments, applications, identity store |
| Inspector | `references/inspector/` | Enablement, findings, filters, coverage, CIS scans, code security, SBOM export |
| Internet Monitor | `references/internetmonitor/` | Monitors, health events, internet events, queries |
| IoT Core | `references/iot/` | Things, certificates, policies, rules, shadows, jobs, fleet indexing, security auditing, OTA updates |
| IoT Device Advisor | `references/iotdeviceadvisor/` | Suite definitions, suite runs, test reports, endpoint management |
| IoT Events | `references/iotevents/` | Detector models, inputs, alarm models, runtime detector and alarm operations |
| IoT FleetWise | `references/iotfleetwise/` | Signal catalogs, model manifests, vehicles, campaigns, decoder manifests, fleets |
| IoT SiteWise | `references/iotsitewise/` | Asset models, assets, portals, dashboards, gateways, projects, time series data |
| IoT TwinMaker | `references/iottwinmaker/` | Workspaces, entities, component types, scenes, sync jobs, metadata transfer |
| IoT Wireless | `references/iotwireless/` | LoRaWAN/Sidewalk devices, wireless gateways, destinations, multicast, FUOTA tasks |
| IVS | `references/ivs/` | Channels, streams, stages, compositions, participants, chat rooms, recording |
| Kendra | `references/kendra/` | Intelligent search indexes, data sources, FAQs, thesauri, query suggestions, featured results, experiences, ranking |
| Keyspaces | `references/keyspaces/` | Keyspaces, tables, user-defined types, auto scaling, point-in-time recovery |
| Kinesis | `references/kinesis/` | Data streams, shards, records, consumers, Kinesis Data Analytics |
| KMS | `references/kms/` | Encryption keys, key policies, grants, aliases, encrypt/decrypt, key rotation, multi-region |
| Lake Formation | `references/lakeformation/` | Permissions, LF-tags, data cell filters, resource registration, transactions |
| Lambda | `references/lambda/` | Functions, layers, event source mappings, aliases, versions, concurrency, URLs |
| Lex v2 | `references/lex/` | Conversational AI bots, intents, slots, locales, custom vocabulary, analytics |
| License Manager | `references/license-manager/` | Licenses, grants, configurations, Linux subscriptions, user subscriptions |
| Lightsail | `references/lightsail/` | Instances, disks, load balancers, databases, containers, distributions, domains |
| Lookout for Equipment | `references/lookoutequipment/` | Industrial equipment anomaly detection, datasets, models, inference schedulers, labels, retraining |
| Lookout for Metrics | `references/lookoutmetrics/` | Metric anomaly detection, detectors, metric sets, alerts, anomaly groups |
| Lookout for Vision | `references/lookoutvision/` | Visual anomaly detection, projects, models, datasets, model packaging |
| Location Services | `references/location/` | Maps, places, routes, geofences, trackers, API keys |
| Macie | `references/macie/` | Classification jobs, findings, filters, allow lists, data identifiers, buckets, automated discovery |
| Managed Grafana | `references/grafana/` | Workspaces, authentication, permissions, service accounts, API keys |
| Managed Prometheus | `references/amp/` | Workspaces, alert manager, rule groups, scrapers, logging |
| Marketplace Catalog | `references/marketplace-catalog/` | Entities, change sets, resource policies |
| MediaConnect | `references/mediaconnect/` | Flows, sources, outputs, entitlements, media streams, bridges, gateways |
| MediaConvert | `references/mediaconvert/` | Transcoding jobs, job templates, output presets, queues, policies |
| MediaLive | `references/medialive/` | Channels, inputs, multiplexes, clusters, networks, schedules, reservations, signal maps |
| MediaPackage | `references/mediapackage/` | Channel groups, channels, origin endpoints, harvest jobs, VOD packaging |
| MediaStore | `references/mediastore/` | Containers, policies, CORS, lifecycle, object operations |
| Migration | `references/migration/` | MGN source servers, replication, cutover, Migration Hub Config, Orchestrator |
| MSK | `references/msk/` | Kafka clusters, configurations, topics, brokers, replicators, MSK Connect |
| MWAA | `references/mwaa/` | Managed Apache Airflow environments, CLI tokens, web login, REST API |
| Neptune | `references/neptune/` | DB clusters, instances, snapshots, global clusters, Analytics graphs, import/export |
| Network Firewall | `references/network-firewall/` | Firewalls, firewall policies, rule groups, TLS inspection, logging |
| Network Manager | `references/networkmanager/` | Global networks, core networks, sites, devices, attachments, route analysis |
| OpenSearch | `references/opensearch/` | Domains, packages, VPC endpoints, indexes, Serverless collections/security |
| Organizations | `references/organizations/` | Organization management, accounts, OUs, policies (SCPs, tag, backup, AI opt-out) |
| Outposts | `references/outposts/` | Outpost management, sites, orders, capacity tasks, assets, catalog items |
| Payment Cryptography | `references/payment-cryptography/` | Keys, encryption, PIN/MAC operations, card validation |
| Personalize | `references/personalize/` | ML recommendations, dataset groups, schemas, solutions, campaigns, recommenders, batch jobs, event trackers |
| Pinpoint | `references/pinpoint/` | Customer engagement campaigns, journeys, segments, messaging channels, templates, endpoints, SMS/voice v2 |
| Polly | `references/polly/` | Text-to-speech synthesis, speech marks, lexicons, voice descriptions |
| Pricing | `references/pricing/` | Services, products, attribute values, price lists |
| Private CA | `references/acm-pca/` | Certificate authorities, certificates, audit reports, permissions, policies |
| Proton | `references/proton/` | Environments, services, templates, components, repositories, sync configs |
| Q Connect | `references/qconnect/` | AI-powered contact center assistant, knowledge bases, AI agents, guardrails, prompts, sessions |
| QLDB | `references/qldb/` | Ledgers, journal exports, journal streams, blocks, revisions (end of support) |
| QuickSight | `references/quicksight/` | Dashboards, analyses, templates, data sets, data sources, users, topics, embedding |
| RAM | `references/ram/` | Resource shares, invitations, permissions, organizations |
| RDS | `references/rds/` | DB instances, Aurora clusters, snapshots, parameter groups, subnet groups, replicas, proxies |
| Redshift | `references/redshift/` | Provisioned clusters, snapshots, parameter groups, data sharing, Data API, Serverless |
| Rekognition | `references/rekognition/` | Image/video analysis, face detection, collections, users, liveness, stream processors, media analysis, custom labels projects |
| Resilience Hub | `references/resiliencehub/` | Apps, resiliency policies, assessments, recommendations |
| Resource Explorer | `references/resource-explorer-2/` | Indexes, views, search, supported resource types |
| Resource Groups | `references/resource-groups/` | Resource groups, queries, configurations, tag-based grouping, tag sync |
| Resource Groups Tagging API | `references/resourcegroupstaggingapi/` | Cross-service tag management, resource discovery by tag, compliance reporting |
| Route 53 | `references/route53/` | Hosted zones, DNS records, health checks, routing policies, domain registration |
| Route 53 Recovery | `references/route53-recovery/` | Recovery clusters, control panels, routing controls, safety rules, readiness checks |
| Route 53 Resolver | `references/route53resolver/` | Resolver endpoints, rules, DNS Firewall, query logging, DNSSEC, Profiles |
| S3 | `references/s3/` | Buckets, objects, storage classes, lifecycle, versioning, website hosting, presigned URLs |
| S3 Control | `references/s3control/` | Access points, Object Lambda, Access Grants, Batch Operations, Storage Lens |
| S3 Outposts | `references/s3outposts/` | Endpoints, shared endpoints, Outposts with S3 capability |
| SageMaker | `references/sagemaker/` | Training jobs, models, endpoints, processing, hyperparameter tuning, AutoML, pipelines, experiments, Feature Store, model registry, monitoring, notebooks, HyperPod clusters |
| SageMaker A2I | `references/sagemaker-a2i-runtime/` | Human-in-the-loop review, human loops, flow definitions |
| Savings Plans | `references/savingsplans/` | Savings plans, rates, offerings |
| Security Hub | `references/securityhub/` | Hub management, findings, insights, standards, security controls, automation rules |
| Security Lake | `references/securitylake/` | Data lake configuration, log sources, subscribers, organization |
| Secrets Manager | `references/secretsmanager/` | Secrets, versions, rotation, replication, resource policies, batch retrieval |
| Service Catalog | `references/servicecatalog/` | Portfolios, products, provisioned products, constraints, service actions |
| Service Catalog AppRegistry | `references/servicecatalog-appregistry/` | Applications, attribute groups, resource associations, configuration |
| Service Quotas | `references/service-quotas/` | Quota lookups, increase requests, templates, auto-management, utilization |
| SES v2 | `references/sesv2/` | Email identities, configuration sets, contact lists, templates, sending, suppression |
| Shield | `references/shield/` | Subscription, protections, attacks, DRT access, proactive engagement, automatic response |
| Snow Family | `references/snowball/` | Snowball/Snowball Edge/Snowcone jobs, clusters, addresses, shipping |
| SNS | `references/sns/` | Topics, subscriptions, publishing, SMS, platform applications, message filtering |
| SQS | `references/sqs/` | Standard and FIFO queues, messages, dead-letter queues, visibility timeout, long polling |
| STS | `references/sts/` | Assume role, session tokens, federation, caller identity |
| Step Functions | `references/stepfunctions/` | State machines, executions, activities, map runs, versions |
| Storage Gateway | `references/storagegateway/` | Gateways, file shares, iSCSI volumes, tape gateway, cache, bandwidth |
| SWF | `references/swf/` | Simple Workflow Service, domains, workflow types, activity types, executions, tasks |
| Systems Manager | `references/ssm/` | Parameter Store, documents, Run Command, Session Manager, patch baselines, state manager |
| Systems Manager Incidents | `references/ssm-incidents/` | Response plans, incidents, timeline events, contacts, engagements, rotations |
| Textract | `references/textract/` | Document text detection, form/table analysis, expense analysis, ID analysis, lending analysis, custom adapters |
| Timestream | `references/timestream/` | Databases, tables, write records, queries, scheduled queries |
| Transcribe | `references/transcribe/` | Speech-to-text transcription, call analytics, medical transcription, custom vocabularies, language models |
| Transfer Family | `references/transfer/` | SFTP/FTPS/FTP/AS2 servers, users, connectors, agreements, workflows, web apps |
| Translate | `references/translate/` | Language translation, batch translation, custom terminologies, parallel data |
| Trusted Advisor | `references/trustedadvisor/` | Recommendations, organization recommendations, support cases |
| Verified Permissions | `references/verifiedpermissions/` | Policy stores, policies, policy templates, identity sources, authorization |
| WAF v2 | `references/wafv2/` | Web ACLs, rule groups, IP sets, regex pattern sets, logging |
| Well-Architected | `references/wellarchitected/` | Workloads, lenses, reviews, milestones, profiles |
| WorkMail | `references/workmail/` | Organizations, users, groups, resources, mail domains, access control, impersonation, mobile devices |
| WorkSpaces | `references/workspaces/` | Virtual desktops, bundles, images, directories, pools, web portals |
| X-Ray | `references/xray/` | Traces, service graphs, sampling rules, groups, insights, indexing |

## Adding the Skill to Your Project

Claude Code loads skills from a `skills/` directory in your project root. Copy the single `aws-cli` skill directory into your project:

```bash
# From your project root
cp -r /path/to/awscliskills/skills/aws-cli skills/
```

That's it — one directory gives you all 190 services.

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
    ... (190 service directories)
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
