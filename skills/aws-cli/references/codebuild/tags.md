# Tags

CodeBuild resources (projects, report groups, fleets) support tagging via the standard `tag-resource` / `untag-resource` pattern. Tags on a resource can also be retrieved via the corresponding `batch-get-*` command.

---

### 9.1 `tag-resource` (codebuild)

> **Note:** The CodeBuild CLI does not have a standalone `tag-resource` subcommand. Tags are set during resource creation (`create-project`, `create-report-group`, `create-fleet`) and can be updated via the corresponding `update-*` command using the `--tags` parameter.

**Setting tags on a project:**
```bash
aws codebuild update-project --name my-project \
  --tags key=Environment,value=Production key=Team,value=Backend
```

**Setting tags on a report group:**
```bash
aws codebuild update-report-group --arn arn:aws:codebuild:us-east-1:123456789012:report-group/my-group \
  --tags key=Environment,value=Production
```

**Setting tags on a fleet:**
```bash
aws codebuild update-fleet --arn arn:aws:codebuild:us-east-1:123456789012:fleet/my-fleet \
  --tags key=Environment,value=Production
```

**Tag Structure (shorthand):**
```
key=string,value=string key=string,value=string ...
```

**Tag Structure (JSON):**
```json
[
    {
        "key": "string",
        "value": "string"
    }
]
```

**Constraints:**
- Maximum 50 tags per resource
- Tag key: 1-128 characters
- Tag value: 0-256 characters
- Tag keys must be unique per resource

---

### 9.2 Retrieving tags

Tags are included in the output of `batch-get-projects`, `batch-get-report-groups`, and `batch-get-fleets` within each resource object's `tags` array.

**Example — get tags for a project:**
```bash
aws codebuild batch-get-projects --names my-project \
  --query 'projects[0].tags'
```

**Example — get tags for a fleet:**
```bash
aws codebuild batch-get-fleets --names my-fleet \
  --query 'fleets[0].tags'
```
