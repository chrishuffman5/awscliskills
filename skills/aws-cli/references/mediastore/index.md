# MediaStore — Quick Reference

## All Commands — MediaStore (Control Plane)

| Command | Description |
|---------|-------------|
| `mediastore create-container` | Create a container for media storage |
| `mediastore describe-container` | Describe a container |
| `mediastore list-containers` | List all containers |
| `mediastore delete-container` | Delete a container |
| `mediastore put-container-policy` | Create or update a container access policy |
| `mediastore get-container-policy` | Get a container access policy |
| `mediastore delete-container-policy` | Delete a container access policy |
| `mediastore put-cors-policy` | Create or update a CORS policy |
| `mediastore get-cors-policy` | Get a CORS policy |
| `mediastore delete-cors-policy` | Delete a CORS policy |
| `mediastore put-lifecycle-policy` | Create or update an object lifecycle policy |
| `mediastore get-lifecycle-policy` | Get an object lifecycle policy |
| `mediastore delete-lifecycle-policy` | Delete an object lifecycle policy |
| `mediastore put-metric-policy` | Create or update a metric policy |
| `mediastore get-metric-policy` | Get a metric policy |
| `mediastore delete-metric-policy` | Delete a metric policy |
| `mediastore start-access-logging` | Enable access logging |
| `mediastore stop-access-logging` | Disable access logging |
| `mediastore tag-resource` | Add tags to a resource |
| `mediastore untag-resource` | Remove tags from a resource |
| `mediastore list-tags-for-resource` | List tags for a resource |

## All Commands — MediaStore Data (Data Plane)

| Command | Description |
|---------|-------------|
| `mediastore-data put-object` | Upload an object to a container |
| `mediastore-data get-object` | Download an object from a container |
| `mediastore-data describe-object` | Get metadata for an object |
| `mediastore-data list-items` | List objects and folders in a container |
| `mediastore-data delete-object` | Delete an object from a container |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Patterns

### Get container endpoint URL
```bash
aws mediastore describe-container \
    --container-name my-container \
    --query 'Container.Endpoint' --output text
```

### List all active containers
```bash
aws mediastore list-containers \
    --query 'Containers[?Status==`ACTIVE`].{Name:Name,Endpoint:Endpoint}'
```

### List objects in a folder
```bash
aws mediastore-data list-items \
    --endpoint https://aaabbbcccdddee.data.mediastore.us-west-2.amazonaws.com \
    --path /media/ \
    --query 'Items[].{Name:Name,Type:Type,Size:ContentLength}'
```
