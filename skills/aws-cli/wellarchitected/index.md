# AWS CLI v2 -- Well-Architected Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/wellarchitected/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `associate-lenses` | Lens | Associate lenses with a workload |
| `associate-profiles` | Profile | Associate profiles with a workload |
| `create-lens-share` | Lens | Share a custom lens with another account |
| `create-lens-version` | Lens | Create a new version of a custom lens |
| `create-milestone` | Milestone | Create a workload milestone |
| `create-profile` | Profile | Create a Well-Architected profile |
| `create-profile-share` | Profile | Share a profile with another account |
| `create-review-template` | Review Template | Create a review template |
| `create-template-share` | Review Template | Share a review template |
| `create-workload` | Workload | Create a new workload |
| `create-workload-share` | Workload | Share a workload with another account |
| `delete-lens` | Lens | Delete a custom lens |
| `delete-lens-share` | Lens | Delete a lens share |
| `delete-profile` | Profile | Delete a profile |
| `delete-profile-share` | Profile | Delete a profile share |
| `delete-review-template` | Review Template | Delete a review template |
| `delete-template-share` | Review Template | Delete a template share |
| `delete-workload` | Workload | Delete a workload |
| `delete-workload-share` | Workload | Delete a workload share |
| `disassociate-lenses` | Lens | Disassociate lenses from a workload |
| `disassociate-profiles` | Profile | Disassociate profiles from a workload |
| `export-lens` | Lens | Export a custom lens as JSON |
| `get-answer` | Answer | Get an answer to a specific question |
| `get-consolidated-report` | Report | Get a consolidated report across workloads |
| `get-global-settings` | Settings | Get global settings for the account |
| `get-lens` | Lens | Get a lens by alias or ARN |
| `get-lens-review` | Review | Get a lens review for a workload |
| `get-lens-review-report` | Review | Get a lens review report |
| `get-lens-version-difference` | Lens | Get version differences for a lens |
| `get-milestone` | Milestone | Get a milestone for a workload |
| `get-profile` | Profile | Get a profile |
| `get-profile-template` | Profile | Get the profile template |
| `get-review-template` | Review Template | Get a review template |
| `get-review-template-answer` | Review Template | Get a review template answer |
| `get-review-template-lens-review` | Review Template | Get a review template lens review |
| `get-workload` | Workload | Get a workload |
| `import-lens` | Lens | Import a custom lens from JSON |
| `list-answers` | Answer | List answers for a lens review |
| `list-check-details` | Report | List Trusted Advisor check details |
| `list-check-summaries` | Report | List Trusted Advisor check summaries |
| `list-lens-review-improvements` | Review | List improvement recommendations |
| `list-lens-reviews` | Review | List lens reviews for a workload |
| `list-lens-shares` | Lens | List shares for a lens |
| `list-lenses` | Lens | List available lenses |
| `list-milestones` | Milestone | List milestones for a workload |
| `list-notifications` | Report | List notifications for a workload |
| `list-profile-notifications` | Profile | List profile notifications |
| `list-profile-shares` | Profile | List shares for a profile |
| `list-profiles` | Profile | List profiles |
| `list-review-template-answers` | Review Template | List review template answers |
| `list-review-templates` | Review Template | List review templates |
| `list-share-invitations` | Share | List share invitations |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `list-template-shares` | Review Template | List shares for a template |
| `list-workload-shares` | Workload | List shares for a workload |
| `list-workloads` | Workload | List workloads |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `update-answer` | Answer | Update an answer |
| `update-global-settings` | Settings | Update global settings |
| `update-integration` | Settings | Update integration settings |
| `update-lens-review` | Review | Update a lens review |
| `update-profile` | Profile | Update a profile |
| `update-review-template` | Review Template | Update a review template |
| `update-review-template-answer` | Review Template | Update a review template answer |
| `update-review-template-lens-review` | Review Template | Update a review template lens review |
| `update-share-invitation` | Share | Accept or reject a share invitation |
| `update-workload` | Workload | Update a workload |
| `update-workload-share` | Workload | Update a workload share |
| `upgrade-lens-review` | Review | Upgrade a lens review to latest version |
| `upgrade-profile-version` | Profile | Upgrade a profile to latest version |
| `upgrade-review-template-lens-review` | Review Template | Upgrade a review template lens review |

---

## Global Options

These options are available on ALL `aws wellarchitected` commands.

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

### Risk Levels
| Risk | Description |
|------|-------------|
| `UNANSWERED` | Question has not been answered |
| `HIGH` | High risk identified |
| `MEDIUM` | Medium risk identified |
| `NONE` | No risk identified |
| `NOT_APPLICABLE` | Question is not applicable |

### Lens Status Values
| Status | Description |
|--------|-------------|
| `CURRENT` | Lens is the current version |
| `NOT_CURRENT` | Newer version available |
| `DEPRECATED` | Lens is deprecated |
| `DELETED` | Lens has been deleted |
| `UNSHARED` | Lens share has been revoked |

### Share Permission Types
| Permission | Description |
|------------|-------------|
| `READONLY` | Can view but not modify |
| `CONTRIBUTOR` | Can view and modify answers |

### Share Status Values
| Status | Description |
|--------|-------------|
| `ACCEPTED` | Share invitation accepted |
| `REJECTED` | Share invitation rejected |
| `PENDING` | Awaiting response |
| `REVOKED` | Share was revoked |
| `EXPIRED` | Invitation expired |
| `ASSOCIATING` | Share is being set up |
| `ASSOCIATED` | Share is active |
| `FAILED` | Share setup failed |
