# Split Reference Files by Command Group — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Split each skill's monolithic `references/reference.md` into per-command-group files to reduce token cost by ~70-80% when agents load specific commands.

**Architecture:** Each skill's `references/reference.md` gets split into: one file per command group (named with kebab-case group name), plus an `index.md` containing shared content (Quick Reference table, Global Options, Common Patterns). SKILL.md gets updated to replace grep patterns with a command reference table mapping groups to files. The old `reference.md` is deleted after splitting.

**Tech Stack:** Markdown, Git, Agent Teams with Haiku model

---

## Pre-Flight

### Task 0: Push current state to remote

Ensure all prior audit-fix commits are pushed before starting new work.

**Step 1: Verify clean state**
```bash
git status
git log --oneline -5
```

**Step 2: Push if needed**
```bash
git push
```

---

## Transformation Spec

Every skill follows the same pattern. Each agent receives this spec plus the skill-specific data.

### What to produce

Given `skills/aws-cli-<service>/references/reference.md`, produce:

```
skills/aws-cli-<service>/references/
  index.md                    # Shared content (Quick Ref table, Global Options, Common Patterns)
  <group-1-kebab>.md          # Command group 1 content
  <group-2-kebab>.md          # Command group 2 content
  ...
```

Then delete `reference.md`.

### How to build index.md

Extract these non-group sections from `reference.md` and combine them into `index.md`:

```markdown
# AWS CLI v2 — <Service> Command Reference Index

> Source: AWS CLI v2 official documentation. [version line from original]

## Quick Reference

[The "All <Service> Subcommands (Quick Reference)" table from original]

## Global Options

[The "Global Options Reference" section from original]

## Common Patterns

[The "Common Patterns" section if present, otherwise omit]
```

### How to build each group file

For each numbered group section (e.g., `## 1. Clusters`), extract the full section content (from `## N.` to just before the next `## N+1.` or non-group section) into its own file:

```markdown
# <Group Name>

[All content from the group section, preserving ### subcommand headers, tables, code blocks]
```

Strip the `## N.` numbering prefix — use just the group name as the `#` title (e.g., `## 1. Clusters` → `# Clusters`).

### How to update SKILL.md

Replace the existing `## Full Command Reference` section (which has grep patterns) with a command reference table:

```markdown
## Command Reference

See [`references/index.md`](references/index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](references/clusters.md) | create-cluster, delete-cluster, describe-clusters, list-clusters, ... |
| Services | [`services.md`](references/services.md) | create-service, update-service, delete-service, ... |
| ... | ... | ... |
```

The "Commands" column should list the `### N.N \`command-name\`` entries from each group (just the command names, comma-separated).

---

## Per-Skill Data

### aws-cli-ecs (13 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Clusters | clusters.md | 89-493 |
| 2. Services | services.md | 494-1015 |
| 3. Tasks | tasks.md | 1016-1432 |
| 4. Task Definitions | task-definitions.md | 1433-1891 |
| 5. Container Instances | container-instances.md | 1892-2207 |
| 6. Capacity Providers | capacity-providers.md | 2208-2416 |
| 7. Task Sets | task-sets.md | 2417-2648 |
| 8. Account Settings | account-settings.md | 2649-2801 |
| 9. Service Deployments | service-deployments.md | 2802-2984 |
| 10. Tags | tags.md | 2985-3066 |
| 11. Attributes | attributes.md | 3067-3197 |
| 12. Execute Command | execute-command.md | 3198-3231 |
| 13. Task Protection | task-protection.md | 3232-3321 |

Non-group: TOC (7-25), Quick Ref (26-88), Global Options (3322-3351), Common Patterns (3352-end)

### aws-cli-ec2 (7 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Instances | instances.md | 47-461 |
| 2. Security Groups | security-groups.md | 462-772 |
| 3. VPC | vpc.md | 773-1603 |
| 4. Key Pairs | key-pairs.md | 1604-1719 |
| 5. AMIs | amis.md | 1720-1802 |
| 6. Launch Templates | launch-templates.md | 1803-2111 |
| 7. Auto Scaling | auto-scaling.md | 2112-2460 |

Non-group: TOC (8-19), Global Options (20-46)
Note: EC2 has "Global Options (apply to all commands)" at the top instead of the bottom.

### aws-cli-ecr (7 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Repository Management | repository-management.md | 85-392 |
| 2. Image Management | image-management.md | 393-707 |
| 3. Image Scanning | image-scanning.md | 708-948 |
| 4. Lifecycle Policies | lifecycle-policies.md | 949-1170 |
| 5. Authentication | authentication.md | 1171-1234 |
| 6. Registry Management | registry-management.md | 1235-1679 |
| 7. Tags | tags.md | 1680-1761 |

Non-group: TOC (7-19), Quick Ref (20-84), Global Options (1762-1791), Common Patterns (1792-end)

### aws-cli-s3 (5 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. High-Level Commands (`aws s3`) | high-level-commands.md | 101-362 |
| 2. Bucket Management (`aws s3api`) | bucket-management.md | 363-531 |
| 3. Bucket Configuration | bucket-configuration.md | 532-1794 |
| 4. Object Operations | object-operations.md | 1795-2706 |
| 5. Multipart Uploads | multipart-uploads.md | 2707-3145 |

Non-group: TOC (7-17), Quick Ref (18-100), Global Options (3146-3175), Common Patterns (3176-end)

### aws-cli-rds (11 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. DB Instances | db-instances.md | 109-500 |
| 2. DB Clusters (Aurora) | db-clusters.md | 501-899 |
| 3. Snapshots | snapshots.md | 900-1305 |
| 4. Parameter Groups | parameter-groups.md | 1306-1660 |
| 5. Subnet Groups | subnet-groups.md | 1661-1777 |
| 6. Option Groups | option-groups.md | 1778-2002 |
| 7. Event Subscriptions | event-subscriptions.md | 2003-2193 |
| 8. Automated Backups | automated-backups.md | 2194-2323 |
| 9. RDS Proxy | rds-proxy.md | 2324-2614 |
| 10. Tags | tags.md | 2615-2683 |
| 11. Maintenance & Engine Info | maintenance-engine-info.md | 2684-2936 |

Non-group: TOC (7-23), Quick Ref (24-108), Global Options (2937-2966), Common Patterns (2967-end)

### aws-cli-route53 (9 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Hosted Zones | hosted-zones.md | 140-607 |
| 2. Records | records.md | 608-875 |
| 3. Health Checks | health-checks.md | 876-1288 |
| 4. Traffic Policies | traffic-policies.md | 1289-1872 |
| 5. DNSSEC | dnssec.md | 1873-2149 |
| 6. Query Logging | query-logging.md | 2150-2280 |
| 7. Reusable Delegation Sets | reusable-delegation-sets.md | 2281-2408 |
| 8. Domain Registration (`route53domains`) | domain-registration.md | 2409-3087 |
| 9. Tags | tags.md | 3088-3282 |

Non-group: TOC (7-21), Quick Ref (22-139), Global Options (3283-3312), Common Patterns (3313-end)

### aws-cli-iam (21 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Users | users.md | 200-369 |
| 2. Groups | groups.md | 370-598 |
| 3. Roles | roles.md | 599-821 |
| 4. Managed Policies | managed-policies.md | 822-1093 |
| 5. Policy Attachment | policy-attachment.md | 1094-1272 |
| 6. Inline Policies | inline-policies.md | 1273-1483 |
| 7. Instance Profiles | instance-profiles.md | 1484-1632 |
| 8. Access Keys | access-keys.md | 1633-1756 |
| 9. Login Profiles | login-profiles.md | 1757-1830 |
| 10. MFA Devices | mfa-devices.md | 1831-2023 |
| 11. Signing Certificates | signing-certificates.md | 2024-2117 |
| 12. SSH Public Keys | ssh-public-keys.md | 2118-2225 |
| 13. Server Certificates | server-certificates.md | 2226-2355 |
| 14. OIDC Providers | oidc-providers.md | 2356-2489 |
| 15. SAML Providers | saml-providers.md | 2490-2597 |
| 16. Service-Linked Roles | service-linked-roles.md | 2598-2681 |
| 17. Service-Specific Credentials | service-specific-credentials.md | 2682-2782 |
| 18. Permissions Boundaries | permissions-boundaries.md | 2783-2843 |
| 19. Account & Reporting | account-reporting.md | 2844-3271 |
| 20. Policy Simulation | policy-simulation.md | 3272-3406 |
| 21. Tags | tags.md | 3407-3477 |

Non-group: TOC (7-33), Quick Ref (34-199), Global Options (3478-end)

### aws-cli-cloudwatch (20 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Metrics | metrics.md | 144-380 |
| 2. Alarms | alarms.md | 381-816 |
| 3. Dashboards | dashboards.md | 817-936 |
| 4. Anomaly Detection | anomaly-detection.md | 937-1065 |
| 5. Insight Rules | insight-rules.md | 1066-1292 |
| 6. Metric Streams | metric-streams.md | 1293-1476 |
| 7. Tags (cloudwatch) | tags-cloudwatch.md | 1477-1556 |
| 8. Log Groups | log-groups.md | 1557-1749 |
| 9. Log Streams | log-streams.md | 1750-1846 |
| 10. Log Events | log-events.md | 1847-2072 |
| 11. Metric Filters | metric-filters.md | 2073-2222 |
| 12. Subscription Filters | subscription-filters.md | 2223-2320 |
| 13. Destinations | destinations.md | 2321-2445 |
| 14. Logs Insights | logs-insights.md | 2446-2596 |
| 15. Export Tasks | export-tasks.md | 2597-2707 |
| 16. Resource Policies | resource-policies.md | 2708-2796 |
| 17. Log Data Protection | log-data-protection.md | 2797-2874 |
| 18. Query Definitions | query-definitions.md | 2875-2976 |
| 19. Log Anomaly Detection | log-anomaly-detection.md | 2977-3226 |
| 20. Tags (logs) | tags-logs.md | 3227-3299 |

Non-group: TOC (7-37), Quick Ref (38-143), Global Options (3300-end)

### aws-cli-elbv2 (10 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Load Balancers | load-balancers.md | 82-581 |
| 2. Target Groups | target-groups.md | 582-1014 |
| 3. Listeners | listeners.md | 1015-1288 |
| 4. Rules | rules.md | 1289-1531 |
| 5. Certificates | certificates.md | 1532-1624 |
| 6. SSL Policies | ssl-policies.md | 1625-1672 |
| 7. Trust Stores | trust-stores.md | 1673-2023 |
| 8. Tags | tags.md | 2024-2104 |
| 9. Account Limits | account-limits.md | 2105-2141 |
| 10. Wait Commands | wait-commands.md | 2142-2208 |

Non-group: TOC (7-22), Quick Ref (23-81), Global Options (2209-end)

### aws-cli-lambda (14 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Functions | functions.md | 100-749 |
| 2. Invocation | invocation.md | 750-802 |
| 3. Layers | layers.md | 803-1123 |
| 4. Event Source Mappings | event-source-mappings.md | 1124-1363 |
| 5. Aliases | aliases.md | 1364-1534 |
| 6. Versions | versions.md | 1535-1600 |
| 7. Concurrency | concurrency.md | 1601-1808 |
| 8. Function URLs | function-urls.md | 1809-1979 |
| 9. Permissions | permissions.md | 1980-2086 |
| 10. Code Signing | code-signing.md | 2087-2363 |
| 11. Tags | tags.md | 2364-2440 |
| 12. Account | account.md | 2441-2474 |
| 13. Runtime Management | runtime-management.md | 2475-2542 |
| 14. Wait Commands | wait-commands.md | 2543-2596 |

Non-group: TOC (7-26), Quick Ref (27-99), Global Options (2597-end)

### aws-cli-dynamodb (18 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Table Management | table-management.md | 105-439 |
| 2. Item Operations | item-operations.md | 440-653 |
| 3. Query & Scan | query-scan.md | 654-772 |
| 4. Batch Operations | batch-operations.md | 773-879 |
| 5. Transactions | transactions.md | 880-984 |
| 6. PartiQL (SQL-Compatible Access) | partiql.md | 986-1116 |
| 7. DynamoDB Streams | dynamodb-streams.md | 1117-1292 |
| 8. Backups | backups.md | 1293-1512 |
| 9. Continuous Backups / PITR | continuous-backups-pitr.md | 1513-1627 |
| 10. Global Tables | global-tables.md | 1628-1832 |
| 11. TTL (Time to Live) | ttl.md | 1833-1896 |
| 12. Import / Export | import-export.md | 1897-2149 |
| 13. Contributor Insights | contributor-insights.md | 2150-2259 |
| 14. Kinesis Streaming Destination | kinesis-streaming-destination.md | 2260-2394 |
| 15. Resource Policies | resource-policies.md | 2395-2486 |
| 16. Endpoints & Limits | endpoints-limits.md | 2487-2540 |
| 17. Tags | tags.md | 2541-2625 |
| 18. Wait Commands | wait-commands.md | 2626-2645 |

Non-group: TOC (7-30), Quick Ref (31-104), Global Options (2646-end)

### aws-cli-kms (9 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Key Management | key-management.md | 82-479 |
| 2. Cryptographic Operations | cryptographic-operations.md | 480-979 |
| 3. Grants | grants.md | 980-1149 |
| 4. Aliases | aliases.md | 1150-1255 |
| 5. Key Rotation | key-rotation.md | 1256-1390 |
| 6. Multi-Region Keys | multi-region-keys.md | 1391-1468 |
| 7. Custom Key Stores | custom-key-stores.md | 1469-1659 |
| 8. Import Key Material | import-key-material.md | 1660-1752 |
| 9. Tags | tags.md | 1753-1836 |

Non-group: TOC (7-21), Quick Ref (22-81), Global Options (1837-end)

### aws-cli-sns (11 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Topics | topics.md | 73-263 |
| 2. Subscriptions | subscriptions.md | 264-514 |
| 3. Publishing | publishing.md | 515-619 |
| 4. Permissions | permissions.md | 620-673 |
| 5. Platform Applications | platform-applications.md | 674-839 |
| 6. Platform Endpoints | platform-endpoints.md | 840-993 |
| 7. SMS | sms.md | 994-1144 |
| 8. SMS Sandbox | sms-sandbox.md | 1145-1276 |
| 9. Origination Numbers | origination-numbers.md | 1277-1320 |
| 10. Data Protection | data-protection.md | 1321-1373 |
| 11. Tags | tags.md | 1374-1455 |

Non-group: TOC (7-23), Quick Ref (24-72), Global Options (1456-end)

### aws-cli-sqs (5 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Queue Management | queue-management.md | 48-286 |
| 2. Messages | messages.md | 287-663 |
| 3. Dead-Letter Queue Redrive | dead-letter-queue-redrive.md | 664-816 |
| 4. Permissions | permissions.md | 817-875 |
| 5. Tags | tags.md | 876-954 |

Non-group: TOC (7-17), Quick Ref (18-47), Global Options (955-end)

### aws-cli-cloudfront (18 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Distributions | distributions.md | 148-659 |
| 2. Invalidations | invalidations.md | 660-801 |
| 3. Functions | functions.md | 802-1105 |
| 4. Cache Policies | cache-policies.md | 1106-1323 |
| 5. Origin Request Policies | origin-request-policies.md | 1324-1529 |
| 6. Response Headers Policies | response-headers-policies.md | 1530-1754 |
| 7. Origin Access Control | origin-access-control.md | 1755-1958 |
| 8. Origin Access Identity (Legacy) | origin-access-identity.md | 1959-2162 |
| 9. Continuous Deployment | continuous-deployment.md | 2163-2399 |
| 10. Key Groups | key-groups.md | 2400-2598 |
| 11. Public Keys | public-keys.md | 2599-2799 |
| 12. Real-Time Logs | real-time-logs.md | 2800-2993 |
| 13. Key Value Stores | key-value-stores.md | 2994-3165 |
| 14. Monitoring Subscriptions | monitoring-subscriptions.md | 3166-3244 |
| 15. Field-Level Encryption | field-level-encryption.md | 3245-3402 |
| 16. Streaming Distributions (Legacy) | streaming-distributions.md | 3403-3479 |
| 17. Tags | tags.md | 3480-3563 |
| 18. Wait Commands | wait-commands.md | 3564-3633 |

Non-group: TOC (7-30), Quick Ref (31-147), Global Options (3634-end)

### aws-cli-secretsmanager (8 groups)

| Group | Filename | Lines |
|-------|----------|-------|
| 1. Secret Lifecycle | secret-lifecycle.md | 51-390 |
| 2. Secret Retrieval | secret-retrieval.md | 391-490 |
| 3. Versions | versions.md | 491-570 |
| 4. Rotation | rotation.md | 571-653 |
| 5. Replication | replication.md | 654-770 |
| 6. Resource Policies | resource-policies.md | 771-896 |
| 7. Random Password | random-password.md | 897-939 |
| 8. Tags | tags.md | 940-993 |

Non-group: TOC (7-20), Quick Ref (21-50), Global Options (994-end)

---

## Task Execution

### Agent Team Strategy

4 Haiku agents, 4 skills each. Each agent receives the Transformation Spec (above) plus its 4 skills' data.

| Agent | Skills |
|-------|--------|
| split-1 | aws-cli-ecs (13), aws-cli-ec2 (7), aws-cli-ecr (7), aws-cli-s3 (5) |
| split-2 | aws-cli-rds (11), aws-cli-route53 (9), aws-cli-iam (21), aws-cli-cloudwatch (20) |
| split-3 | aws-cli-elbv2 (10), aws-cli-lambda (14), aws-cli-dynamodb (18), aws-cli-kms (9) |
| split-4 | aws-cli-sns (11), aws-cli-sqs (5), aws-cli-cloudfront (18), aws-cli-secretsmanager (8) |

### Tasks 1-4: Split reference files (parallel, Haiku agents)

Each agent does the following for each of its 4 skills:

**Step 1: Read the current reference.md**
```bash
# Read the file to get exact content
```

**Step 2: Create group files**

For each command group in the per-skill data table:
- Read the lines for that group from reference.md
- Write to `references/<group-filename>.md`
- Use `# <Group Name>` as the title (strip the `## N.` prefix)

**Step 3: Create index.md**

Combine the non-group sections into `references/index.md`:
- Version/source line from the top of reference.md
- Quick Reference table
- Global Options section
- Common Patterns section (if present)

**Step 4: Update SKILL.md**

Replace the `## Full Command Reference` section (including grep patterns) with:
```markdown
## Command Reference

See [`references/index.md`](references/index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| <Group> | [`<filename>`](references/<filename>) | cmd1, cmd2, ... |
```

Populate the "Commands" column by extracting the `### N.N \`command-name\`` headers from each group.

**Step 5: Delete reference.md**
```bash
git rm skills/aws-cli-<service>/references/reference.md
```

**Step 6: Commit**
```bash
git add skills/aws-cli-<service>/
git commit -m "refactor(aws-cli-<service>): split reference into per-command-group files

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>"
```

Repeat Steps 1-6 for each of the agent's 4 skills.

### Task 5: Update CLAUDE.md and README.md (leader)

**Files:**
- Modify: `CLAUDE.md`
- Modify: `README.md`

**Step 1: Update CLAUDE.md**

In the skill hierarchy tree, update the service skill entries from:
```
  aws-cli-ecs/
    SKILL.md
    references/
      reference.md
```
To:
```
  aws-cli-ecs/
    SKILL.md
    references/
      index.md
      <group-files>.md
```

Only show one representative example with the full file list, then use `...` for the rest.

Update the "How Skills Work" bullet about reference files.

**Step 2: Update README.md**

Update the "Skill File Format" section to reflect the new structure:
```
skills/aws-cli-<service>/
  SKILL.md              # YAML frontmatter + overview + command reference table
  references/
    index.md            # Quick reference table + global options
    <group>.md          # Per-command-group reference files
```

Update the descriptions.

**Step 3: Commit**
```bash
git add CLAUDE.md README.md
git commit -m "docs: update CLAUDE.md and README.md for split reference structure

Co-Authored-By: Claude Opus 4.6 <noreply@anthropic.com>"
```

### Task 6: Push to remote (leader)

```bash
git push
```

---

## Parallelization

- Tasks 1-4 are fully independent (separate skill directories). Run all 4 Haiku agents in parallel.
- Task 5 depends on Tasks 1-4 completing. Leader handles directly.
- Task 6 depends on Task 5. Leader handles directly.

## Expected Outcome

- 176 new command group files across 16 skills
- 16 new index.md files
- 16 reference.md files deleted
- 16 SKILL.md files updated with command reference tables
- CLAUDE.md and README.md updated
- Token cost for loading a specific command group: ~500-2,000 tokens (down from ~5,000-15,000)
