# CloudWatch Evidently — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-project` | Create an Evidently project |
| `get-project` | Retrieve project details |
| `list-projects` | List all projects |
| `update-project` | Modify a project |
| `delete-project` | Delete a project |
| `put-project-events` | Send evaluation or custom events to a project |
| `create-feature` | Create a feature with variations |
| `get-feature` | Retrieve feature details |
| `list-features` | List features in a project |
| `update-feature` | Modify a feature |
| `delete-feature` | Delete a feature |
| `evaluate-feature` | Evaluate a feature for a specific entity |
| `batch-evaluate-feature` | Evaluate features for multiple entities |
| `create-experiment` | Create an A/B experiment |
| `get-experiment` | Retrieve experiment details |
| `list-experiments` | List experiments in a project |
| `update-experiment` | Modify an experiment |
| `delete-experiment` | Delete an experiment |
| `start-experiment` | Start an experiment |
| `stop-experiment` | Stop a running experiment |
| `get-experiment-results` | Retrieve experiment results and metrics |
| `create-launch` | Create a gradual launch |
| `get-launch` | Retrieve launch details |
| `list-launches` | List launches in a project |
| `update-launch` | Modify a launch |
| `delete-launch` | Delete a launch |
| `start-launch` | Start a launch |
| `stop-launch` | Stop a running launch |
| `create-segment` | Create an audience segment |
| `get-segment` | Retrieve segment details |
| `list-segments` | List all segments |
| `delete-segment` | Delete a segment |
| `test-segment-pattern` | Test a segment pattern against a payload |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

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

## Common Patterns

### Get experiment status and results
```bash
aws evidently get-experiment \
    --project my-project \
    --experiment my-experiment \
    --query '{Status:experiment.status,Started:experiment.execution.startedTime}'

aws evidently get-experiment-results \
    --project my-project \
    --experiment my-experiment \
    --metric-names conversion \
    --treatment-names control treatment \
    --result-stats BaseStat TreatmentEffect PValue
```

### List all running launches
```bash
aws evidently list-launches \
    --project my-project \
    --status RUNNING \
    --query 'launches[].{Name:name,Status:status}'
```

### Evaluate feature with segment context
```bash
aws evidently evaluate-feature \
    --project my-project \
    --feature new-checkout \
    --entity-id user-12345 \
    --evaluation-context '{"location":"US","plan":"premium"}'
```
