# AWS CLI v2 -- CodeCommit Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/codecommit/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-repository` | Repository | Create a new repository |
| `delete-repository` | Repository | Delete a repository |
| `get-repository` | Repository | Get information about a repository |
| `list-repositories` | Repository | List repositories |
| `batch-get-repositories` | Repository | Get information about multiple repositories |
| `update-repository-description` | Repository | Update a repository description |
| `update-repository-name` | Repository | Rename a repository |
| `create-branch` | Branch | Create a new branch |
| `delete-branch` | Branch | Delete a branch |
| `get-branch` | Branch | Get information about a branch |
| `list-branches` | Branch | List branches in a repository |
| `update-default-branch` | Branch | Change the default branch |
| `create-commit` | Commit | Create a commit with file changes |
| `get-commit` | Commit | Get information about a commit |
| `batch-get-commits` | Commit | Get information about multiple commits |
| `get-differences` | Commit | Get differences between commits |
| `get-blob` | File | Get the content of a blob |
| `get-file` | File | Get the content of a file |
| `get-folder` | File | Get the contents of a folder |
| `put-file` | File | Add or update a file in a repository |
| `delete-file` | File | Delete a file from a repository |
| `create-pull-request` | Pull Request | Create a pull request |
| `get-pull-request` | Pull Request | Get information about a pull request |
| `list-pull-requests` | Pull Request | List pull requests |
| `update-pull-request-title` | Pull Request | Update a pull request title |
| `update-pull-request-description` | Pull Request | Update a pull request description |
| `update-pull-request-status` | Pull Request | Update a pull request status |
| `describe-pull-request-events` | Pull Request | Describe pull request events |
| `evaluate-pull-request-approval-rules` | Pull Request | Evaluate approval rules for a PR |
| `create-approval-rule-template` | Approval Rule | Create an approval rule template |
| `delete-approval-rule-template` | Approval Rule | Delete an approval rule template |
| `get-approval-rule-template` | Approval Rule | Get an approval rule template |
| `list-approval-rule-templates` | Approval Rule | List approval rule templates |
| `update-approval-rule-template-content` | Approval Rule | Update approval rule template content |
| `associate-approval-rule-template-with-repository` | Approval Rule | Associate template with repository |
| `disassociate-approval-rule-template-from-repository` | Approval Rule | Disassociate template from repository |
| `list-associated-approval-rule-templates-for-repository` | Approval Rule | List templates for a repository |
| `list-repositories-for-approval-rule-template` | Approval Rule | List repositories for a template |
| `get-merge-options` | Merge | Get available merge options |
| `get-merge-conflicts` | Merge | Get merge conflicts |
| `get-merge-commit` | Merge | Get merge commit information |
| `merge-branches-by-fast-forward` | Merge | Merge branches by fast-forward |
| `merge-branches-by-squash` | Merge | Merge branches by squash |
| `merge-branches-by-three-way` | Merge | Merge branches by three-way merge |
| `merge-pull-request-by-fast-forward` | Merge | Merge PR by fast-forward |
| `merge-pull-request-by-squash` | Merge | Merge PR by squash |
| `merge-pull-request-by-three-way` | Merge | Merge PR by three-way merge |
| `post-comment-for-compared-commit` | Comment | Post a comment on a commit comparison |
| `post-comment-for-pull-request` | Comment | Post a comment on a pull request |
| `post-comment-reply` | Comment | Reply to a comment |
| `get-comment` | Comment | Get a comment |
| `get-comments-for-compared-commit` | Comment | Get comments for a commit comparison |
| `get-comments-for-pull-request` | Comment | Get comments for a pull request |
| `update-comment` | Comment | Update a comment |
| `delete-comment-content` | Comment | Delete a comment's content |
| `get-repository-triggers` | Trigger | Get repository triggers |
| `put-repository-triggers` | Trigger | Set repository triggers |
| `test-repository-triggers` | Trigger | Test repository triggers |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws codecommit` commands.

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

### Pull Request Status Values
| Status | Description |
|--------|-------------|
| `OPEN` | Pull request is open and can be reviewed/merged |
| `CLOSED` | Pull request has been closed without merging |

### Merge Strategy Types
| Strategy | Description |
|----------|-------------|
| `FAST_FORWARD_MERGE` | Fast-forward merge (no merge commit) |
| `SQUASH_MERGE` | Squash all commits into a single commit |
| `THREE_WAY_MERGE` | Standard three-way merge with merge commit |

### Conflict Resolution Strategy
| Strategy | Description |
|----------|-------------|
| `NONE` | No automatic resolution |
| `ACCEPT_SOURCE` | Accept source branch changes |
| `ACCEPT_DESTINATION` | Accept destination branch changes |
| `AUTOMERGE` | Attempt automatic merge |

### Sort By / Order By
| Sort By | Description |
|---------|-------------|
| `repositoryName` | Sort by repository name |
| `lastModifiedDate` | Sort by last modified date |

| Order | Description |
|-------|-------------|
| `ascending` | Sort in ascending order |
| `descending` | Sort in descending order |
