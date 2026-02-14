# MediaConvert — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `associate-certificate` | Associate an ACM certificate with MediaConvert for DRM |
| `cancel-job` | Cancel a transcoding job |
| `create-job` | Create a new transcoding job |
| `create-job-template` | Create a reusable job template |
| `create-preset` | Create an output preset |
| `create-queue` | Create a processing queue |
| `create-resource-share` | Share a job with AWS Support via a support case |
| `delete-job-template` | Delete a job template |
| `delete-policy` | Delete the input source policy |
| `delete-preset` | Delete an output preset |
| `delete-queue` | Delete a processing queue |
| `disassociate-certificate` | Disassociate an ACM certificate from MediaConvert |
| `get-job` | Get details for a transcoding job |
| `get-job-template` | Get details for a job template |
| `get-jobs-query-results` | Retrieve results from an advanced jobs query |
| `get-policy` | Get the current input source policy |
| `get-preset` | Get details for an output preset |
| `get-queue` | Get details for a processing queue |
| `list-job-templates` | List job templates |
| `list-jobs` | List transcoding jobs |
| `list-presets` | List output presets |
| `list-queues` | List processing queues |
| `list-tags-for-resource` | List tags for a resource |
| `list-versions` | List available job engine versions |
| `probe` | Probe media files for track and format information |
| `put-policy` | Create or update the input source policy |
| `search-jobs` | Search jobs by input file, queue, or status |
| `start-jobs-query` | Start an advanced query for jobs with filters |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `update-job-template` | Update a job template |
| `update-preset` | Update an output preset |
| `update-queue` | Update a processing queue |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |
| `--endpoint-url` | Override default endpoint URL (required for account-specific endpoints) |

## Common Patterns

### Get the account-specific endpoint
```bash
aws mediaconvert describe-endpoints --query 'Endpoints[0].Url' --output text
```

### List failed jobs with error details
```bash
aws mediaconvert list-jobs --status ERROR \
    --query 'Jobs[].{Id:Id,Error:ErrorMessage,Input:Settings.Inputs[0].FileInput}'
```

### Check job progress
```bash
aws mediaconvert get-job --id 1234567890123-abcdef \
    --query 'Job.{Status:Status,Phase:CurrentPhase,Percent:JobPercentComplete}'
```

### List all custom presets sorted by name
```bash
aws mediaconvert list-presets --list-by NAME --order ASCENDING \
    --query 'Presets[?Type==`CUSTOM`].{Name:Name,Description:Description}'
```
