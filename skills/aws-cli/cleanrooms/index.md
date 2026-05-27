# AWS CLI v2 -- Clean Rooms Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/cleanrooms/ , https://docs.aws.amazon.com/cli/latest/reference/cleanroomsml/

---

## Quick Reference — `aws cleanrooms`

| Command | Category | Description |
|---------|----------|-------------|
| `create-collaboration` | Collaboration | Create a new collaboration |
| `delete-collaboration` | Collaboration | Delete a collaboration |
| `get-collaboration` | Collaboration | Get collaboration details |
| `list-collaborations` | Collaboration | List collaborations |
| `update-collaboration` | Collaboration | Update a collaboration |
| `create-collaboration-change-request` | Collaboration | Create a change request |
| `get-collaboration-change-request` | Collaboration | Get a change request |
| `list-collaboration-change-requests` | Collaboration | List change requests |
| `update-collaboration-change-request` | Collaboration | Update a change request |
| `create-membership` | Membership | Join a collaboration |
| `delete-membership` | Membership | Leave a collaboration |
| `get-membership` | Membership | Get membership details |
| `list-memberships` | Membership | List memberships |
| `update-membership` | Membership | Update membership settings |
| `delete-member` | Membership | Remove a member from a collaboration |
| `list-members` | Membership | List members in a collaboration |
| `create-configured-table` | Configured Table | Create a configured table |
| `delete-configured-table` | Configured Table | Delete a configured table |
| `get-configured-table` | Configured Table | Get configured table details |
| `list-configured-tables` | Configured Table | List configured tables |
| `update-configured-table` | Configured Table | Update a configured table |
| `create-configured-table-analysis-rule` | Configured Table | Create an analysis rule |
| `delete-configured-table-analysis-rule` | Configured Table | Delete an analysis rule |
| `get-configured-table-analysis-rule` | Configured Table | Get an analysis rule |
| `update-configured-table-analysis-rule` | Configured Table | Update an analysis rule |
| `create-configured-table-association` | Configured Table | Associate table with membership |
| `delete-configured-table-association` | Configured Table | Delete table association |
| `get-configured-table-association` | Configured Table | Get table association |
| `list-configured-table-associations` | Configured Table | List table associations |
| `update-configured-table-association` | Configured Table | Update table association |
| `create-configured-table-association-analysis-rule` | Configured Table | Create association analysis rule |
| `delete-configured-table-association-analysis-rule` | Configured Table | Delete association analysis rule |
| `get-configured-table-association-analysis-rule` | Configured Table | Get association analysis rule |
| `update-configured-table-association-analysis-rule` | Configured Table | Update association analysis rule |
| `create-analysis-template` | Analysis Template | Create an analysis template |
| `delete-analysis-template` | Analysis Template | Delete an analysis template |
| `get-analysis-template` | Analysis Template | Get analysis template details |
| `list-analysis-templates` | Analysis Template | List analysis templates |
| `update-analysis-template` | Analysis Template | Update an analysis template |
| `batch-get-collaboration-analysis-template` | Analysis Template | Batch get collaboration analysis templates |
| `get-collaboration-analysis-template` | Analysis Template | Get collaboration analysis template |
| `list-collaboration-analysis-templates` | Analysis Template | List collaboration analysis templates |
| `batch-get-schema` | Schema | Batch get schemas |
| `batch-get-schema-analysis-rule` | Schema | Batch get schema analysis rules |
| `get-schema` | Schema | Get a schema |
| `get-schema-analysis-rule` | Schema | Get schema analysis rule |
| `list-schemas` | Schema | List schemas in a collaboration |
| `start-protected-query` | Protected Query | Start a protected query |
| `get-protected-query` | Protected Query | Get protected query details |
| `list-protected-queries` | Protected Query | List protected queries |
| `update-protected-query` | Protected Query | Cancel a protected query |
| `start-protected-job` | Protected Job | Start a protected job |
| `get-protected-job` | Protected Job | Get protected job details |
| `list-protected-jobs` | Protected Job | List protected jobs |
| `update-protected-job` | Protected Job | Update a protected job |
| `create-privacy-budget-template` | Privacy Budget | Create privacy budget template |
| `delete-privacy-budget-template` | Privacy Budget | Delete privacy budget template |
| `get-privacy-budget-template` | Privacy Budget | Get privacy budget template |
| `list-privacy-budget-templates` | Privacy Budget | List privacy budget templates |
| `list-privacy-budgets` | Privacy Budget | List privacy budgets |
| `update-privacy-budget-template` | Privacy Budget | Update privacy budget template |
| `get-collaboration-privacy-budget-template` | Privacy Budget | Get collaboration privacy budget template |
| `list-collaboration-privacy-budget-templates` | Privacy Budget | List collaboration privacy budget templates |
| `list-collaboration-privacy-budgets` | Privacy Budget | List collaboration privacy budgets |
| `preview-privacy-impact` | Privacy Budget | Preview privacy impact of a query |
| `create-id-mapping-table` | ID Mapping | Create an ID mapping table |
| `delete-id-mapping-table` | ID Mapping | Delete an ID mapping table |
| `get-id-mapping-table` | ID Mapping | Get ID mapping table details |
| `list-id-mapping-tables` | ID Mapping | List ID mapping tables |
| `populate-id-mapping-table` | ID Mapping | Populate an ID mapping table |
| `update-id-mapping-table` | ID Mapping | Update an ID mapping table |
| `create-id-namespace-association` | ID Mapping | Create an ID namespace association |
| `delete-id-namespace-association` | ID Mapping | Delete ID namespace association |
| `get-id-namespace-association` | ID Mapping | Get ID namespace association |
| `list-id-namespace-associations` | ID Mapping | List ID namespace associations |
| `update-id-namespace-association` | ID Mapping | Update ID namespace association |
| `get-collaboration-id-namespace-association` | ID Mapping | Get collaboration ID namespace association |
| `list-collaboration-id-namespace-associations` | ID Mapping | List collaboration ID namespace associations |
| `create-configured-audience-model-association` | Audience Model | Associate audience model with membership |
| `delete-configured-audience-model-association` | Audience Model | Delete audience model association |
| `get-configured-audience-model-association` | Audience Model | Get audience model association |
| `list-configured-audience-model-associations` | Audience Model | List audience model associations |
| `update-configured-audience-model-association` | Audience Model | Update audience model association |
| `get-collaboration-configured-audience-model-association` | Audience Model | Get collaboration audience model |
| `list-collaboration-configured-audience-model-associations` | Audience Model | List collaboration audience models |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — `aws cleanroomsml`

| Command | Category | Description |
|---------|----------|-------------|
| `create-audience-model` | Audience Model | Create an audience model |
| `delete-audience-model` | Audience Model | Delete an audience model |
| `get-audience-model` | Audience Model | Get audience model details |
| `list-audience-models` | Audience Model | List audience models |
| `create-configured-audience-model` | Audience Model | Create a configured audience model |
| `delete-configured-audience-model` | Audience Model | Delete a configured audience model |
| `get-configured-audience-model` | Audience Model | Get configured audience model |
| `list-configured-audience-models` | Audience Model | List configured audience models |
| `update-configured-audience-model` | Audience Model | Update configured audience model |
| `create-training-dataset` | Training | Create a training dataset |
| `delete-training-dataset` | Training | Delete a training dataset |
| `get-training-dataset` | Training | Get training dataset details |
| `list-training-datasets` | Training | List training datasets |
| `create-ml-input-channel` | Training | Create an ML input channel |
| `delete-ml-input-channel-data` | Training | Delete ML input channel data |
| `get-ml-input-channel` | Training | Get ML input channel details |
| `list-ml-input-channels` | Training | List ML input channels |
| `get-collaboration-ml-input-channel` | Training | Get collaboration ML input channel |
| `list-collaboration-ml-input-channels` | Training | List collaboration ML input channels |
| `create-trained-model` | Trained Model | Create a trained model |
| `cancel-trained-model` | Trained Model | Cancel trained model creation |
| `delete-trained-model-output` | Trained Model | Delete trained model output |
| `get-trained-model` | Trained Model | Get trained model details |
| `list-trained-models` | Trained Model | List trained models |
| `list-trained-model-versions` | Trained Model | List trained model versions |
| `get-collaboration-trained-model` | Trained Model | Get collaboration trained model |
| `list-collaboration-trained-models` | Trained Model | List collaboration trained models |
| `start-trained-model-inference-job` | Inference | Start an inference job |
| `cancel-trained-model-inference-job` | Inference | Cancel an inference job |
| `get-trained-model-inference-job` | Inference | Get inference job details |
| `list-trained-model-inference-jobs` | Inference | List inference jobs |
| `start-trained-model-export-job` | Inference | Start a model export job |
| `list-collaboration-trained-model-export-jobs` | Inference | List collaboration export jobs |
| `list-collaboration-trained-model-inference-jobs` | Inference | List collaboration inference jobs |
| `create-configured-model-algorithm` | Algorithm | Create a configured model algorithm |
| `delete-configured-model-algorithm` | Algorithm | Delete a configured model algorithm |
| `get-configured-model-algorithm` | Algorithm | Get algorithm details |
| `list-configured-model-algorithms` | Algorithm | List configured model algorithms |
| `create-configured-model-algorithm-association` | Algorithm | Create algorithm association |
| `delete-configured-model-algorithm-association` | Algorithm | Delete algorithm association |
| `get-configured-model-algorithm-association` | Algorithm | Get algorithm association |
| `list-configured-model-algorithm-associations` | Algorithm | List algorithm associations |
| `get-collaboration-configured-model-algorithm-association` | Algorithm | Get collaboration algorithm association |
| `list-collaboration-configured-model-algorithm-associations` | Algorithm | List collaboration algorithm associations |
| `start-audience-generation-job` | Audience Gen | Start audience generation job |
| `delete-audience-generation-job` | Audience Gen | Delete audience generation job |
| `get-audience-generation-job` | Audience Gen | Get audience generation job details |
| `list-audience-generation-jobs` | Audience Gen | List audience generation jobs |
| `start-audience-export-job` | Audience Gen | Start audience export job |
| `list-audience-export-jobs` | Audience Gen | List audience export jobs |
| `delete-configured-audience-model-policy` | Policy | Delete audience model policy |
| `get-configured-audience-model-policy` | Policy | Get audience model policy |
| `put-configured-audience-model-policy` | Policy | Set audience model policy |
| `delete-ml-configuration` | Config | Delete ML configuration |
| `get-ml-configuration` | Config | Get ML configuration |
| `put-ml-configuration` | Config | Set ML configuration |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws cleanrooms` and `aws cleanroomsml` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from JSON string or `file://` |
| `--cli-input-yaml` | string | -- | Read arguments from YAML string or `file://` |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Collaboration Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Collaboration is active |
| `CREATE_IN_PROGRESS` | Collaboration is being created |
| `CREATE_FAILED` | Collaboration creation failed |
| `UPDATE_IN_PROGRESS` | Collaboration is being updated |
| `UPDATE_FAILED` | Update failed |
| `DELETE_IN_PROGRESS` | Collaboration is being deleted |
| `DELETE_FAILED` | Deletion failed |
| `DELETED` | Collaboration has been deleted |

### Member Abilities
| Ability | Description |
|---------|-------------|
| `CAN_QUERY` | Member can run queries |
| `CAN_RECEIVE_RESULTS` | Member can receive query results |

### Analysis Rule Types
| Type | Description |
|------|-------------|
| `AGGREGATION` | Only aggregation queries allowed |
| `LIST` | List-style queries with row-level output |
| `CUSTOM` | Custom SQL with analysis template constraints |

### Protected Query States
| State | Description |
|-------|-------------|
| `SUBMITTED` | Query has been submitted |
| `STARTED` | Query execution started |
| `COMPUTING` | Query is computing |
| `RESULT_READY` | Results are ready |
| `COMPLETED` | Query completed successfully |
| `FAILED` | Query failed |
| `CANCELLED` | Query was cancelled |
| `TIMED_OUT` | Query timed out |
