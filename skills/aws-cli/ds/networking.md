# Networking

### 6.1 `add-ip-routes`

Adds IP address routes to a directory to allow clients from public or on-premises networks to access the directory.

**Synopsis:**
```bash
aws ds add-ip-routes \
    --directory-id <value> \
    --ip-routes <value> \
    [--update-security-group-for-directory-controllers | --no-update-security-group-for-directory-controllers] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--ip-routes` | **Yes** | list(structure) | -- | IP routes to add |
| `--update-security-group-for-directory-controllers` | No | boolean | true | Update the security group for directory controllers |

**IP Route Structure:**
```json
{
    "CidrIp": "string",
    "Description": "string"
}
```

**Output Schema:**

No output on success (HTTP 200).

---

### 6.2 `remove-ip-routes`

Removes IP address routes from a directory.

**Synopsis:**
```bash
aws ds remove-ip-routes \
    --directory-id <value> \
    --cidr-ips <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--cidr-ips` | **Yes** | list(string) | -- | CIDR IP addresses to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 6.3 `list-ip-routes`

Lists the IP routes that have been added to a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds list-ip-routes \
    --directory-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "IpRoutesInfo": [
        {
            "DirectoryId": "string",
            "CidrIp": "string",
            "IpRouteStatusMsg": "Adding|Added|Removing|Removed|AddFailed|RemoveFailed",
            "AddedDateTime": "timestamp",
            "IpRouteStatusReason": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```
