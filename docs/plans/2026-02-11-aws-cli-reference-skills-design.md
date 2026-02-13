# AWS CLI Reference Skills Design

## Date: 2026-02-11

## Purpose

Create a hierarchical set of Claude skills that provide comprehensive AWS CLI v2 command reference for ECS, EC2, and ECR services. These skills serve as ground-truth reference when building the ecsagent deployment tool.

## Architecture

```
skills/
  aws-cli/           # Router skill — general CLI conventions, service index
    SKILL.md
  aws-cli-ecs/       # Full ECS CLI reference
    SKILL.md          # Overview + workflows
    reference.md      # Complete command reference (all flags + output schemas)
  aws-cli-ec2/       # EC2 CLI reference (scoped to ECS-relevant commands)
    SKILL.md
    reference.md
  aws-cli-ecr/       # Full ECR CLI reference
    SKILL.md
    reference.md
```

## Skill Details

### aws-cli (Router)
- General AWS CLI v2 conventions (output formats, --query JMESPath, pagination, waiters, --region, --profile)
- Service index table mapping to per-service skills
- No command details — routing only

### aws-cli-ecs
- All `aws ecs` subcommands with full flag signatures (required/optional, types, defaults)
- JSON output schemas for each command
- Covers: clusters, services, tasks, task definitions, container instances, capacity providers

### aws-cli-ec2
- Scoped to ECS-relevant EC2 commands (instances, security groups, VPCs, subnets, key pairs, AMIs, launch templates)
- Full flag signatures and output schemas for scoped commands

### aws-cli-ecr
- All `aws ecr` subcommands (repositories, images, lifecycle policies, login)
- Full flag signatures and output schemas

## Data Source
- Pre-authored from official AWS CLI v2 documentation
- Curated at skill creation time, stored statically in skill files

## Detail Level
- Commands + all flags (required vs optional, types) + JSON output schemas
