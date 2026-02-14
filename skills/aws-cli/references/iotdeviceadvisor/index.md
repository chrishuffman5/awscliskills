# IoT Device Advisor — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-suite-definition` | Create a test suite definition |
| `delete-suite-definition` | Delete a test suite definition |
| `get-endpoint` | Get the Device Advisor test endpoint |
| `get-suite-definition` | Get details of a test suite definition |
| `get-suite-run` | Get details and results of a test suite run |
| `get-suite-run-report` | Get the qualification report download URL |
| `list-suite-definitions` | List all test suite definitions |
| `list-suite-runs` | List test suite runs |
| `list-tags-for-resource` | List tags for a resource |
| `start-suite-run` | Start a test suite run |
| `stop-suite-run` | Stop a running test suite |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `update-suite-definition` | Update a test suite definition |

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

### Check test run status
```bash
aws iotdeviceadvisor get-suite-run \
    --suite-definition-id qqcsmtyyjabl \
    --suite-run-id nzlfyhaa18oa \
    --query '{Status:status,Passed:testResult.groups[].tests[?status==`PASS`]|[]|length(@),Failed:testResult.groups[].tests[?status==`FAIL`]|[]|length(@)}'
```

### List all running test suites
```bash
aws iotdeviceadvisor list-suite-runs \
    --query 'suiteRunsList[?status==`RUNNING`].{Id:suiteRunId,Suite:suiteDefinitionName}'
```

### Get device-level endpoint for testing
```bash
aws iotdeviceadvisor get-endpoint \
    --thing-arn arn:aws:iot:us-east-1:123456789012:thing/MyDevice \
    --authentication-method X509ClientCertificate
```
