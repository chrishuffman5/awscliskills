# Amazon IVS — Quick Reference

## All Commands — IVS (Low-Latency Streaming)

| Command | Description |
|---------|-------------|
| `ivs create-channel` | Create a channel for live streaming |
| `ivs get-channel` | Get channel details |
| `ivs batch-get-channel` | Get multiple channels at once |
| `ivs list-channels` | List all channels |
| `ivs update-channel` | Update channel configuration |
| `ivs delete-channel` | Delete a channel |
| `ivs create-stream-key` | Create a stream key for a channel |
| `ivs get-stream-key` | Get stream key details |
| `ivs batch-get-stream-key` | Get multiple stream keys at once |
| `ivs list-stream-keys` | List stream keys for a channel |
| `ivs delete-stream-key` | Delete a stream key |
| `ivs get-stream` | Get current stream details |
| `ivs list-streams` | List all active streams |
| `ivs get-stream-session` | Get stream session details |
| `ivs list-stream-sessions` | List stream sessions for a channel |
| `ivs stop-stream` | Stop an active stream |
| `ivs put-metadata` | Send timed metadata during a stream |
| `ivs create-recording-configuration` | Create a recording configuration |
| `ivs get-recording-configuration` | Get recording configuration details |
| `ivs list-recording-configurations` | List recording configurations |
| `ivs delete-recording-configuration` | Delete a recording configuration |
| `ivs import-playback-key-pair` | Import a playback key pair |
| `ivs get-playback-key-pair` | Get playback key pair details |
| `ivs list-playback-key-pairs` | List playback key pairs |
| `ivs delete-playback-key-pair` | Delete a playback key pair |
| `ivs create-playback-restriction-policy` | Create a playback restriction policy |
| `ivs get-playback-restriction-policy` | Get playback restriction policy |
| `ivs list-playback-restriction-policies` | List playback restriction policies |
| `ivs update-playback-restriction-policy` | Update a playback restriction policy |
| `ivs delete-playback-restriction-policy` | Delete a playback restriction policy |
| `ivs start-viewer-session-revocation` | Revoke a viewer session |
| `ivs batch-start-viewer-session-revocation` | Revoke multiple viewer sessions |
| `ivs tag-resource` | Add tags to a resource |
| `ivs untag-resource` | Remove tags from a resource |
| `ivs list-tags-for-resource` | List tags for a resource |

## All Commands — IVS Real-Time

| Command | Description |
|---------|-------------|
| `ivs-realtime create-stage` | Create a real-time stage |
| `ivs-realtime get-stage` | Get stage details |
| `ivs-realtime list-stages` | List all stages |
| `ivs-realtime update-stage` | Update a stage |
| `ivs-realtime delete-stage` | Delete a stage |
| `ivs-realtime get-stage-session` | Get stage session details |
| `ivs-realtime list-stage-sessions` | List stage sessions |
| `ivs-realtime create-participant-token` | Create a participant token |
| `ivs-realtime get-participant` | Get participant details |
| `ivs-realtime list-participants` | List participants in a session |
| `ivs-realtime list-participant-events` | List participant events |
| `ivs-realtime disconnect-participant` | Disconnect a participant |
| `ivs-realtime start-participant-replication` | Start participant replication |
| `ivs-realtime stop-participant-replication` | Stop participant replication |
| `ivs-realtime list-participant-replicas` | List participant replicas |
| `ivs-realtime start-composition` | Start a server-side composition |
| `ivs-realtime get-composition` | Get composition details |
| `ivs-realtime list-compositions` | List compositions |
| `ivs-realtime stop-composition` | Stop a composition |
| `ivs-realtime create-ingest-configuration` | Create an ingest configuration |
| `ivs-realtime get-ingest-configuration` | Get ingest configuration details |
| `ivs-realtime list-ingest-configurations` | List ingest configurations |
| `ivs-realtime update-ingest-configuration` | Update an ingest configuration |
| `ivs-realtime delete-ingest-configuration` | Delete an ingest configuration |
| `ivs-realtime create-encoder-configuration` | Create an encoder configuration |
| `ivs-realtime get-encoder-configuration` | Get encoder configuration details |
| `ivs-realtime list-encoder-configurations` | List encoder configurations |
| `ivs-realtime delete-encoder-configuration` | Delete an encoder configuration |
| `ivs-realtime create-storage-configuration` | Create a storage configuration |
| `ivs-realtime get-storage-configuration` | Get storage configuration details |
| `ivs-realtime list-storage-configurations` | List storage configurations |
| `ivs-realtime delete-storage-configuration` | Delete a storage configuration |
| `ivs-realtime import-public-key` | Import a public key |
| `ivs-realtime get-public-key` | Get public key details |
| `ivs-realtime list-public-keys` | List public keys |
| `ivs-realtime delete-public-key` | Delete a public key |
| `ivs-realtime tag-resource` | Add tags to a resource |
| `ivs-realtime untag-resource` | Remove tags from a resource |
| `ivs-realtime list-tags-for-resource` | List tags for a resource |

## All Commands — IVS Chat

| Command | Description |
|---------|-------------|
| `ivschat create-room` | Create a chat room |
| `ivschat get-room` | Get chat room details |
| `ivschat list-rooms` | List all chat rooms |
| `ivschat update-room` | Update a chat room |
| `ivschat delete-room` | Delete a chat room |
| `ivschat create-chat-token` | Create a chat access token |
| `ivschat send-event` | Send an event to a chat room |
| `ivschat delete-message` | Delete a message from a room |
| `ivschat disconnect-user` | Disconnect a user from a room |
| `ivschat create-logging-configuration` | Create a chat logging configuration |
| `ivschat get-logging-configuration` | Get logging configuration details |
| `ivschat list-logging-configurations` | List logging configurations |
| `ivschat update-logging-configuration` | Update a logging configuration |
| `ivschat delete-logging-configuration` | Delete a logging configuration |
| `ivschat tag-resource` | Add tags to a resource |
| `ivschat untag-resource` | Remove tags from a resource |
| `ivschat list-tags-for-resource` | List tags for a resource |

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

### Get playback URL for a channel
```bash
aws ivs get-channel \
    --arn arn:aws:ivs:us-east-1:123456789012:channel/abcABC \
    --query 'channel.playbackUrl' --output text
```

### List all active streams with viewer counts
```bash
aws ivs list-streams \
    --filter-by health=HEALTHY \
    --query 'streams[].{Channel:channelArn,Viewers:viewerCount,State:state}'
```

### Get all stage participants
```bash
aws ivs-realtime list-participants \
    --stage-arn arn:aws:ivs:us-east-1:123456789012:stage/abcDEF \
    --session-id session123
```
