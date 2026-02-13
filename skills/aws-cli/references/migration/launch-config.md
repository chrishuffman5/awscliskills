# Launch Configuration

### 3.1 `create-launch-configuration-template`

Creates a launch configuration template that defines default launch settings for migrated servers.

**Synopsis:**
```bash
aws mgn create-launch-configuration-template \
    [--launch-disposition <value>] \
    [--target-instance-type-right-sizing-method <value>] \
    [--copy-private-ip | --no-copy-private-ip] \
    [--copy-tags | --no-copy-tags] \
    [--licensing <value>] \
    [--boot-mode <value>] \
    [--small-volume-max-size <value>] \
    [--small-volume-conf <value>] \
    [--large-volume-conf <value>] \
    [--post-launch-actions <value>] \
    [--enable-map-auto-tagging | --no-enable-map-auto-tagging] \
    [--map-auto-tagging-mpe-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-disposition` | No | string | None | `STOPPED` or `STARTED` |
| `--target-instance-type-right-sizing-method` | No | string | None | `NONE` or `BASIC` or `IN_AWS` |
| `--copy-private-ip` | No | boolean | None | Copy private IP |
| `--copy-tags` | No | boolean | None | Copy source server tags |
| `--licensing` | No | structure | None | OS licensing. Shorthand: `osByol=true\|false` |
| `--boot-mode` | No | string | None | `LEGACY_BIOS`, `UEFI`, `USE_SOURCE` |
| `--small-volume-max-size` | No | long | None | Max size for small volumes (GB) |
| `--small-volume-conf` | No | structure | None | Small volume config. Shorthand: `volumeType=string,iops=long,throughput=long` |
| `--large-volume-conf` | No | structure | None | Large volume config |
| `--post-launch-actions` | No | structure | None | Post-launch actions configuration |
| `--enable-map-auto-tagging` | No | boolean | None | Enable MAP auto-tagging |
| `--map-auto-tagging-mpe-id` | No | string | None | MAP auto-tagging MPE ID |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "launchConfigurationTemplateID": "string",
    "arn": "string",
    "launchDisposition": "STOPPED|STARTED",
    "targetInstanceTypeRightSizingMethod": "NONE|BASIC|IN_AWS",
    "copyPrivateIp": true|false,
    "copyTags": true|false,
    "licensing": {"osByol": true|false},
    "bootMode": "LEGACY_BIOS|UEFI|USE_SOURCE",
    "smallVolumeMaxSize": "long",
    "smallVolumeConf": {"volumeType": "string", "iops": "long", "throughput": "long"},
    "largeVolumeConf": {"volumeType": "string", "iops": "long", "throughput": "long"},
    "postLaunchActions": {
        "deployment": "TEST_AND_CUTOVER|CUTOVER_ONLY|TEST_ONLY",
        "s3LogBucket": "string",
        "s3OutputKeyPrefix": "string",
        "cloudWatchLogGroupName": "string",
        "ssmDocuments": [
            {
                "ssmDocumentName": "string",
                "mustSucceedForCutover": true|false,
                "timeoutSeconds": "integer",
                "parameters": {},
                "externalParameters": {}
            }
        ]
    },
    "enableMapAutoTagging": true|false,
    "mapAutoTaggingMpeID": "string",
    "tags": {"key": "value"}
}
```

---

### 3.2 `delete-launch-configuration-template`

Deletes a launch configuration template.

**Synopsis:**
```bash
aws mgn delete-launch-configuration-template \
    --launch-configuration-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-template-id` | **Yes** | string | -- | Template ID |

**Output:** None

---

### 3.3 `describe-launch-configuration-templates`

Describes launch configuration templates. **Paginated.**

**Synopsis:**
```bash
aws mgn describe-launch-configuration-templates \
    [--launch-configuration-template-i-ds <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-template-i-ds` | No | list(string) | None | Filter by template IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [{"launchConfigurationTemplateID": "string", "...": "..."}],
    "nextToken": "string"
}
```

---

### 3.4 `update-launch-configuration-template`

Updates a launch configuration template.

**Synopsis:** Same parameters as create but with required `--launch-configuration-template-id`.

**Output Schema:** Same as create.

---

### 3.5 `get-launch-configuration`

Gets the launch configuration for a specific source server.

**Synopsis:**
```bash
aws mgn get-launch-configuration \
    --source-server-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--account-id` | No | string | None | Account ID |

**Output Schema:**
```json
{
    "sourceServerID": "string",
    "name": "string",
    "ec2LaunchTemplateID": "string",
    "launchDisposition": "STOPPED|STARTED",
    "targetInstanceTypeRightSizingMethod": "NONE|BASIC|IN_AWS",
    "copyPrivateIp": true|false,
    "copyTags": true|false,
    "licensing": {"osByol": true|false},
    "bootMode": "LEGACY_BIOS|UEFI|USE_SOURCE",
    "postLaunchActions": {},
    "enableMapAutoTagging": true|false,
    "mapAutoTaggingMpeID": "string"
}
```

---

### 3.6 `update-launch-configuration`

Updates the launch configuration for a specific source server.

**Synopsis:**
```bash
aws mgn update-launch-configuration \
    --source-server-id <value> \
    [--account-id <value>] \
    [--name <value>] \
    [--launch-disposition <value>] \
    [--target-instance-type-right-sizing-method <value>] \
    [--copy-private-ip | --no-copy-private-ip] \
    [--copy-tags | --no-copy-tags] \
    [--licensing <value>] \
    [--boot-mode <value>] \
    [--post-launch-actions <value>] \
    [--enable-map-auto-tagging | --no-enable-map-auto-tagging] \
    [--map-auto-tagging-mpe-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as get-launch-configuration output but all optional except `--source-server-id`.

**Output Schema:** Same as get-launch-configuration.
