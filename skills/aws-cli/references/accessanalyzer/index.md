# AWS CLI v2 -- IAM Access Analyzer (accessanalyzer) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/accessanalyzer/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-analyzer` | Analyzer | Create an analyzer |
| `get-analyzer` | Analyzer | Get analyzer details |
| `list-analyzers` | Analyzer | List all analyzers |
| `update-analyzer` | Analyzer | Update an analyzer |
| `delete-analyzer` | Analyzer | Delete an analyzer |
| `get-analyzed-resource` | Analyzer | Get an analyzed resource |
| `list-analyzed-resources` | Analyzer | List analyzed resources |
| `start-resource-scan` | Analyzer | Start a resource scan |
| `list-findings` | Finding | List findings (external access analyzers) |
| `get-finding` | Finding | Get finding details (external access analyzers) |
| `list-findings-v2` | Finding | List findings (all analyzer types) |
| `get-finding-v2` | Finding | Get finding details (all analyzer types) |
| `get-findings-statistics` | Finding | Get findings statistics |
| `update-findings` | Finding | Update finding status (archive/activate) |
| `generate-finding-recommendation` | Finding | Generate a finding recommendation |
| `get-finding-recommendation` | Finding | Get a finding recommendation |
| `create-archive-rule` | Archive Rule | Create an archive rule |
| `get-archive-rule` | Archive Rule | Get archive rule details |
| `list-archive-rules` | Archive Rule | List archive rules |
| `update-archive-rule` | Archive Rule | Update an archive rule |
| `delete-archive-rule` | Archive Rule | Delete an archive rule |
| `apply-archive-rule` | Archive Rule | Apply an archive rule to existing findings |
| `create-access-preview` | Access Preview | Create an access preview |
| `get-access-preview` | Access Preview | Get access preview details |
| `list-access-previews` | Access Preview | List access previews |
| `list-access-preview-findings` | Access Preview | List findings for an access preview |
| `validate-policy` | Policy Tool | Validate a policy document |
| `check-access-not-granted` | Policy Tool | Check policy does not grant specific access |
| `check-no-new-access` | Policy Tool | Check for no new access compared to reference |
| `check-no-public-access` | Policy Tool | Check policy does not grant public access |
| `start-policy-generation` | Policy Tool | Start policy generation from CloudTrail |
| `get-generated-policy` | Policy Tool | Get a generated policy |
| `list-policy-generations` | Policy Tool | List policy generation requests |
| `cancel-policy-generation` | Policy Tool | Cancel a policy generation request |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws accessanalyzer` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Analyzer Types
| Type | Description |
|------|-------------|
| `ACCOUNT` | Analyzes resources in a single account for external access |
| `ORGANIZATION` | Analyzes resources across the organization for external access |
| `ACCOUNT_UNUSED_ACCESS` | Analyzes unused access in a single account |
| `ORGANIZATION_UNUSED_ACCESS` | Analyzes unused access across the organization |
| `ACCOUNT_INTERNAL_ACCESS` | Analyzes internal access in a single account |
| `ORGANIZATION_INTERNAL_ACCESS` | Analyzes internal access across the organization |

### Analyzer Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Analyzer is active and generating findings |
| `CREATING` | Analyzer is being created |
| `DISABLED` | Analyzer is disabled |
| `FAILED` | Analyzer creation failed |

### Finding Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Finding is active and requires attention |
| `ARCHIVED` | Finding has been archived |
| `RESOLVED` | Finding has been resolved (resource access removed) |

### Supported Resource Types
| Resource Type | Service |
|---------------|---------|
| `AWS::S3::Bucket` | Amazon S3 |
| `AWS::IAM::Role` | IAM |
| `AWS::SQS::Queue` | Amazon SQS |
| `AWS::Lambda::Function` | Lambda |
| `AWS::Lambda::LayerVersion` | Lambda |
| `AWS::KMS::Key` | KMS |
| `AWS::SecretsManager::Secret` | Secrets Manager |
| `AWS::EFS::FileSystem` | EFS |
| `AWS::EC2::Snapshot` | EC2 |
| `AWS::ECR::Repository` | ECR |
| `AWS::RDS::DBSnapshot` | RDS |
| `AWS::RDS::DBClusterSnapshot` | RDS |
| `AWS::SNS::Topic` | SNS |
| `AWS::S3Express::DirectoryBucket` | S3 Express |
| `AWS::DynamoDB::Table` | DynamoDB |
| `AWS::DynamoDB::Stream` | DynamoDB |
| `AWS::IAM::User` | IAM |

### Filter Operators
Filters used in `list-findings`, `create-archive-rule`, and related commands support:
| Operator | Description |
|----------|-------------|
| `eq` | Equals (list of values) |
| `neq` | Not equals (list of values) |
| `contains` | Contains (list of values) |
| `exists` | Exists (boolean) |
