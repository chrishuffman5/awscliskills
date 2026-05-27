# Assets

### 5.1 `list-assets`

Lists the hardware assets for the specified Outpost. **Paginated operation.**

**Synopsis:**
```bash
aws outposts list-assets \
    --outpost-identifier <value> \
    [--host-id-filter <value>] \
    [--status-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-identifier` | **Yes** | string | -- | ID or ARN of the Outpost |
| `--host-id-filter` | No | list(string) | None | Filter by host IDs |
| `--status-filter` | No | list(string) | None | Filter by asset status: `ACTIVE`, `RETIRING`, `ISOLATED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Assets": [
        {
            "AssetId": "string",
            "RackId": "string",
            "AssetType": "COMPUTE",
            "ComputeAttributes": {
                "HostId": "string",
                "State": "ACTIVE|ISOLATED|RETIRING",
                "InstanceFamilies": ["string"]
            },
            "AssetLocation": {
                "RackElevation": "float"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### Asset Status Values

| Status | Description |
|--------|-------------|
| `ACTIVE` | Asset is operational and available |
| `ISOLATED` | Asset is isolated from the network |
| `RETIRING` | Asset is being retired |
