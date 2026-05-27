# AWS CLI Plugin

AWS CLI v2 command reference for 190 AWS services, delivered as a lean router skill plus
per-service sub-skills.

## How it works

- `skills/aws-cli/SKILL.md` is the registered router: CLI conventions (output formats, `--query`,
  pagination, waiters, ARNs, env vars) plus a routing protocol. It is the only skill description
  loaded at session start.
- Each service is a bundled sub-skill at `skills/aws-cli/<aws-command>/SKILL.md` (e.g. `s3/`, `ec2/`,
  `dynamodb/`, `iam/`). The router reads only the service you need — the full catalog never loads up
  front, which keeps context small.
- Within a service, command-group files alongside `SKILL.md` (e.g. `instances.md`, `vpc.md`) hold the
  full per-command flags, types, defaults, and JSON output schemas.
- `skills/aws-cli/service-index.md` is the full friendly-name → sub-skill lookup, read only when the
  AWS CLI service name isn't already known (e.g. "which service gives me a CDN?").

## Usage

Just ask about any AWS service via the CLI ("create an S3 bucket", "list ECS services", "set up a
DynamoDB table with a GSI"). The router loads the matching service sub-skill on demand.
