# Access Points

### 3.1 `create-access-point`

Creates an EFS access point. An access point is an application-specific view into a file system that applies an operating system user and group, and a file system path, to any request made through the access point.

**Synopsis:**
```bash
aws efs create-access-point \
    --client-token <value> \
    --file-system-id <value> \
    [--tags <value>] \
    [--posix-user <value>] \
    [--root-directory <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | **Yes** | string | -- | Idempotency token (up to 64 ASCII chars) |
| `--file-system-id` | **Yes** | string | -- | ID of the EFS file system |
| `--tags` | No | list | None | Tags to add. Shorthand: `Key=string,Value=string ...` |
| `--posix-user` | No | structure | None | POSIX user/group identity. Shorthand: `Uid=long,Gid=long,SecondaryGids=long,long` |
| `--root-directory` | No | structure | None | Root directory for the access point |

**Root Directory Structure:**
```json
{
    "Path": "string",
    "CreationInfo": {
        "OwnerUid": "long",
        "OwnerGid": "long",
        "Permissions": "string"
    }
}
```

Shorthand: `Path=/data,CreationInfo={OwnerUid=1000,OwnerGid=1000,Permissions=755}`

**Output Schema:**
```json
{
    "ClientToken": "string",
    "Name": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "AccessPointId": "string",
    "AccessPointArn": "string",
    "FileSystemId": "string",
    "PosixUser": {
        "Uid": "long",
        "Gid": "long",
        "SecondaryGids": ["long"]
    },
    "RootDirectory": {
        "Path": "string",
        "CreationInfo": {
            "OwnerUid": "long",
            "OwnerGid": "long",
            "Permissions": "string"
        }
    },
    "OwnerId": "string",
    "LifeCycleState": "creating|available|updating|deleting|deleted|error"
}
```

---

### 3.2 `delete-access-point`

Deletes the specified access point.

**Synopsis:**
```bash
aws efs delete-access-point \
    --access-point-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-point-id` | **Yes** | string | -- | ID of the access point to delete |

**Output:** None on success.

---

### 3.3 `describe-access-points`

Returns the description of a specific or all EFS access points in an account. **Paginated operation.**

**Synopsis:**
```bash
aws efs describe-access-points \
    [--max-results <value>] \
    [--next-token <value>] \
    [--access-point-id <value>] \
    [--file-system-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-point-id` | No | string | -- | Specific access point ID to describe |
| `--file-system-id` | No | string | -- | File system ID to list access points for |
| `--max-results` | No | integer | None | Maximum number of results (1-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "AccessPoints": [
        {
            "ClientToken": "string",
            "Name": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "AccessPointId": "string",
            "AccessPointArn": "string",
            "FileSystemId": "string",
            "PosixUser": {
                "Uid": "long",
                "Gid": "long",
                "SecondaryGids": ["long"]
            },
            "RootDirectory": {
                "Path": "string",
                "CreationInfo": {
                    "OwnerUid": "long",
                    "OwnerGid": "long",
                    "Permissions": "string"
                }
            },
            "OwnerId": "string",
            "LifeCycleState": "creating|available|updating|deleting|deleted|error"
        }
    ],
    "NextToken": "string"
}
```
