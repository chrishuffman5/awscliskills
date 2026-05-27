# Runtime

### 10.1 `get-recommendations`

Gets item recommendations for a user (User-Personalization) or related items (Related-Items). Use either `--campaign-arn` for custom solutions or `--recommender-arn` for Domain dataset groups.

**Synopsis:**
```bash
aws personalize-runtime get-recommendations \
    [--campaign-arn <value>] \
    [--recommender-arn <value>] \
    [--user-id <value>] \
    [--item-id <value>] \
    [--num-results <value>] \
    [--context <value>] \
    [--filter-arn <value>] \
    [--filter-values <value>] \
    [--promotions <value>] \
    [--metadata-columns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--campaign-arn` | No* | string | None | ARN of campaign (custom solutions) |
| `--recommender-arn` | No* | string | None | ARN of recommender (Domain dataset groups) |
| `--user-id` | No** | string | None | User ID for personalized recommendations |
| `--item-id` | No** | string | None | Item ID for related items recommendations |
| `--num-results` | No | integer | 25 | Number of results (max 500, or 50 with metadata) |
| `--context` | No | map | None | Contextual metadata (location, device, etc.) |
| `--filter-arn` | No | string | None | ARN of filter to apply |
| `--filter-values` | No | map | None | Values for filter placeholders (max 25) |
| `--promotions` | No | list | None | Promotions to apply (max 1) |
| `--metadata-columns` | No | map | None | Item metadata columns to include (max 10) |

*Either `--campaign-arn` or `--recommender-arn` is required.
**`--user-id` required for User-Personalization; `--item-id` required for Related-Items.

**Output Schema:**
```json
{
    "itemList": [
        {
            "itemId": "string",
            "score": "double",
            "promotionName": "string",
            "metadata": {"string": "string"},
            "reason": ["string"]
        }
    ],
    "recommendationId": "string"
}
```

---

### 10.2 `get-personalized-ranking`

Re-ranks a list of items for a specific user. The input list is re-ordered by predicted relevance.

**Synopsis:**
```bash
aws personalize-runtime get-personalized-ranking \
    --campaign-arn <value> \
    --input-list <value> \
    --user-id <value> \
    [--context <value>] \
    [--filter-arn <value>] \
    [--filter-values <value>] \
    [--metadata-columns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--campaign-arn` | **Yes** | string | -- | ARN of the campaign (Personalized-Ranking recipe) |
| `--input-list` | **Yes** | list(string) | -- | List of item IDs to re-rank (max 500) |
| `--user-id` | **Yes** | string | -- | User ID for personalized ranking |
| `--context` | No | map | None | Contextual metadata |
| `--filter-arn` | No | string | None | ARN of filter to apply |
| `--filter-values` | No | map | None | Values for filter placeholders |
| `--metadata-columns` | No | map | None | Item metadata columns to include |

**Output Schema:**
```json
{
    "personalizedRanking": [
        {
            "itemId": "string",
            "score": "double",
            "promotionName": "string",
            "metadata": {"string": "string"},
            "reason": ["string"]
        }
    ],
    "recommendationId": "string"
}
```

---

### 10.3 `get-action-recommendations`

Gets action recommendations for a user.

**Synopsis:**
```bash
aws personalize-runtime get-action-recommendations \
    [--campaign-arn <value>] \
    [--user-id <value>] \
    [--num-results <value>] \
    [--filter-arn <value>] \
    [--filter-values <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--campaign-arn` | No | string | None | ARN of the campaign |
| `--user-id` | No | string | None | User ID for action recommendations |
| `--num-results` | No | integer | 25 | Number of action results to return |
| `--filter-arn` | No | string | None | ARN of filter to apply |
| `--filter-values` | No | map | None | Values for filter placeholders |

**Output Schema:**
```json
{
    "actionList": [
        {
            "actionId": "string",
            "score": "double"
        }
    ],
    "recommendationId": "string"
}
```
