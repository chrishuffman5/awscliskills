# Origination Numbers

### 9.1 `list-origination-numbers`

Lists the calling account's dedicated origination numbers and their metadata. **Paginated operation.**

**Synopsis:**
```bash
aws sns list-origination-numbers \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "PhoneNumbers": [
        {
            "PhoneNumber": "string",
            "Status": "string",
            "CreatedAt": "timestamp",
            "Iso2CountryCode": "string",
            "RouteType": "Transactional|Promotional|Premium",
            "NumberCapabilities": ["SMS", "MMS", "VOICE"]
        }
    ],
    "NextToken": "string"
}
```
