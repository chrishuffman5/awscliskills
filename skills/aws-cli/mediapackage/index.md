# MediaPackage — Quick Reference

## All Commands — MediaPackage v2 (Live)

| Command | Description |
|---------|-------------|
| `mediapackagev2 create-channel-group` | Create a channel group |
| `mediapackagev2 get-channel-group` | Get channel group details |
| `mediapackagev2 list-channel-groups` | List all channel groups |
| `mediapackagev2 update-channel-group` | Update a channel group |
| `mediapackagev2 delete-channel-group` | Delete a channel group |
| `mediapackagev2 create-channel` | Create a channel in a channel group |
| `mediapackagev2 get-channel` | Get channel details |
| `mediapackagev2 list-channels` | List channels in a channel group |
| `mediapackagev2 update-channel` | Update a channel |
| `mediapackagev2 delete-channel` | Delete a channel |
| `mediapackagev2 put-channel-policy` | Attach or update a channel policy |
| `mediapackagev2 get-channel-policy` | Get a channel policy |
| `mediapackagev2 delete-channel-policy` | Delete a channel policy |
| `mediapackagev2 reset-channel-state` | Reset a channel's state |
| `mediapackagev2 create-origin-endpoint` | Create an origin endpoint |
| `mediapackagev2 get-origin-endpoint` | Get origin endpoint details |
| `mediapackagev2 list-origin-endpoints` | List origin endpoints for a channel |
| `mediapackagev2 update-origin-endpoint` | Update an origin endpoint |
| `mediapackagev2 delete-origin-endpoint` | Delete an origin endpoint |
| `mediapackagev2 put-origin-endpoint-policy` | Attach or update an origin endpoint policy |
| `mediapackagev2 get-origin-endpoint-policy` | Get an origin endpoint policy |
| `mediapackagev2 delete-origin-endpoint-policy` | Delete an origin endpoint policy |
| `mediapackagev2 reset-origin-endpoint-state` | Reset an origin endpoint's state |
| `mediapackagev2 create-harvest-job` | Create a harvest job |
| `mediapackagev2 get-harvest-job` | Get harvest job details |
| `mediapackagev2 list-harvest-jobs` | List harvest jobs |
| `mediapackagev2 cancel-harvest-job` | Cancel a harvest job |
| `mediapackagev2 tag-resource` | Add tags to a resource |
| `mediapackagev2 untag-resource` | Remove tags from a resource |
| `mediapackagev2 list-tags-for-resource` | List tags for a resource |

## All Commands — MediaPackage VOD

| Command | Description |
|---------|-------------|
| `mediapackage-vod create-packaging-group` | Create a packaging group |
| `mediapackage-vod describe-packaging-group` | Describe a packaging group |
| `mediapackage-vod list-packaging-groups` | List all packaging groups |
| `mediapackage-vod update-packaging-group` | Update a packaging group |
| `mediapackage-vod delete-packaging-group` | Delete a packaging group |
| `mediapackage-vod configure-logs` | Configure logging for a packaging group |
| `mediapackage-vod create-packaging-configuration` | Create a packaging configuration |
| `mediapackage-vod describe-packaging-configuration` | Describe a packaging configuration |
| `mediapackage-vod list-packaging-configurations` | List packaging configurations |
| `mediapackage-vod delete-packaging-configuration` | Delete a packaging configuration |
| `mediapackage-vod create-asset` | Create a VOD asset |
| `mediapackage-vod describe-asset` | Describe a VOD asset |
| `mediapackage-vod list-assets` | List all VOD assets |
| `mediapackage-vod delete-asset` | Delete a VOD asset |
| `mediapackage-vod tag-resource` | Add tags to a resource |
| `mediapackage-vod untag-resource` | Remove tags from a resource |
| `mediapackage-vod list-tags-for-resource` | List tags for a resource |

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

### List all channels across a channel group
```bash
aws mediapackagev2 list-channels \
    --channel-group-name my-channel-group \
    --query 'Items[].{Name:ChannelName,Type:InputType,Created:CreatedAt}'
```

### Get origin endpoint playback URLs
```bash
aws mediapackagev2 get-origin-endpoint \
    --channel-group-name my-channel-group \
    --channel-name my-channel \
    --origin-endpoint-name my-endpoint \
    --query '{HLS:HlsManifests[].Url,DASH:DashManifests[].Url}'
```

### List all VOD assets in a packaging group
```bash
aws mediapackage-vod list-assets \
    --packaging-group-id my-vod-group \
    --query 'Assets[].{Id:Id,Source:SourceArn}'
```
