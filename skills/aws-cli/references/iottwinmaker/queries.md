# Queries

### 8.1 `execute-query`

Queries the digital twin knowledge graph using a SQL-like syntax. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker execute-query \
    --workspace-id <value> \
    --query-statement <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--query-statement` | **Yes** | string | -- | Query statement (1-1000 chars) |
| `--max-results` | No | integer | 50 | Max results (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "columnDescriptions": [
        {
            "name": "string",
            "type": "NODE|EDGE|VALUE"
        }
    ],
    "rows": [
        {
            "rowData": ["document"]
        }
    ],
    "nextToken": "string"
}
```

**Query Examples:**
```sql
-- Find all entities
SELECT e FROM EntityGraph MATCH (e)

-- Find entity by name
SELECT e FROM EntityGraph MATCH (e) WHERE e.entityName = 'Conveyor Belt 1'

-- Find entities by component type
SELECT e FROM EntityGraph MATCH (e) -[:hasComponent]-> (c) WHERE c.componentTypeId = 'com.example.Sensor'

-- Find parent-child relationships
SELECT parent, child FROM EntityGraph MATCH (parent) -[:isParentOf]-> (child)
```
