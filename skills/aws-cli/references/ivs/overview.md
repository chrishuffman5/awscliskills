# AWS CLI v2 — Amazon IVS

## Overview

Complete reference for `aws ivs`, `aws ivs-realtime`, and `aws ivschat` subcommands in AWS CLI v2. Covers low-latency live streaming channels, real-time interactive stages with server-side composition, and chat rooms. Amazon Interactive Video Service (IVS) makes it easy to set up live interactive video experiences with ultra-low latency.

## Quick Reference — Common Workflows

### Create a channel and get stream key (IVS)
```bash
aws ivs create-channel \
    --name my-live-channel \
    --type STANDARD \
    --latency-mode LOW

aws ivs list-stream-keys \
    --channel-arn arn:aws:ivs:us-east-1:123456789012:channel/abcABCdefDEg
```

### Set up recording to S3 (IVS)
```bash
aws ivs create-recording-configuration \
    --name my-recording \
    --destination-configuration s3={bucketName=my-recording-bucket} \
    --thumbnail-configuration recordingMode=INTERVAL,targetIntervalSeconds=30,storage=LATEST

aws ivs update-channel \
    --arn arn:aws:ivs:us-east-1:123456789012:channel/abcABCdefDEg \
    --recording-configuration-arn arn:aws:ivs:us-east-1:123456789012:recording-configuration/ABCD12cdEFgh
```

### Create a real-time stage with participant tokens (IVS Real-Time)
```bash
aws ivs-realtime create-stage \
    --name my-stage \
    --participant-token-configurations '[{"userId":"host","capabilities":["PUBLISH","SUBSCRIBE"]},{"userId":"viewer","capabilities":["SUBSCRIBE"]}]'
```

### Start a server-side composition (IVS Real-Time)
```bash
aws ivs-realtime start-composition \
    --stage-arn arn:aws:ivs:us-east-1:123456789012:stage/abcDEF123 \
    --destinations '[{"channel":{"channelArn":"arn:aws:ivs:us-east-1:123456789012:channel/abcABC","encoderConfigurationArn":"arn:aws:ivs:us-east-1:123456789012:encoder-configuration/ABab"}}]'
```

### Create a chat room (IVS Chat)
```bash
aws ivschat create-room \
    --name my-chat-room \
    --maximum-message-rate-per-second 10 \
    --maximum-message-length 500
```

### Create a chat token for a user (IVS Chat)
```bash
aws ivschat create-chat-token \
    --room-identifier arn:aws:ivschat:us-east-1:123456789012:room/abcDEF123 \
    --user-id user123 \
    --capabilities SEND_MESSAGE DELETE_MESSAGE
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Channels | [channels.md](channels.md) | `ivs create-channel`, `get-channel`, `batch-get-channel`, `list-channels`, `update-channel`, `delete-channel` |
| Stream Keys | [stream-keys.md](stream-keys.md) | `ivs create-stream-key`, `get-stream-key`, `batch-get-stream-key`, `list-stream-keys`, `delete-stream-key` |
| Streams | [streams.md](streams.md) | `ivs get-stream`, `list-streams`, `get-stream-session`, `list-stream-sessions`, `stop-stream`, `put-metadata` |
| Recording | [recording.md](recording.md) | `ivs create-recording-configuration`, `get-recording-configuration`, `list-recording-configurations`, `delete-recording-configuration` |
| Playback | [playback.md](playback.md) | `ivs import-playback-key-pair`, `get-playback-key-pair`, `list-playback-key-pairs`, `delete-playback-key-pair`, `create-playback-restriction-policy`, `get-playback-restriction-policy`, `list-playback-restriction-policies`, `update-playback-restriction-policy`, `delete-playback-restriction-policy`, `start-viewer-session-revocation`, `batch-start-viewer-session-revocation` |
| Stages | [stages.md](stages.md) | `ivs-realtime create-stage`, `get-stage`, `list-stages`, `update-stage`, `delete-stage`, `get-stage-session`, `list-stage-sessions` |
| Participants | [participants.md](participants.md) | `ivs-realtime create-participant-token`, `get-participant`, `list-participants`, `list-participant-events`, `disconnect-participant`, `start-participant-replication`, `stop-participant-replication`, `list-participant-replicas` |
| Compositions | [compositions.md](compositions.md) | `ivs-realtime start-composition`, `get-composition`, `list-compositions`, `stop-composition` |
| Ingest Configurations | [ingest.md](ingest.md) | `ivs-realtime create-ingest-configuration`, `get-ingest-configuration`, `list-ingest-configurations`, `update-ingest-configuration`, `delete-ingest-configuration` |
| Encoder & Storage | [encoder-storage.md](encoder-storage.md) | `ivs-realtime create-encoder-configuration`, `get-encoder-configuration`, `list-encoder-configurations`, `delete-encoder-configuration`, `create-storage-configuration`, `get-storage-configuration`, `list-storage-configurations`, `delete-storage-configuration`, `import-public-key`, `get-public-key`, `list-public-keys`, `delete-public-key` |
| Chat Rooms | [chat-rooms.md](chat-rooms.md) | `ivschat create-room`, `get-room`, `list-rooms`, `update-room`, `delete-room`, `create-chat-token`, `send-event`, `delete-message`, `disconnect-user` |
| Chat Logging | [chat-logging.md](chat-logging.md) | `ivschat create-logging-configuration`, `get-logging-configuration`, `list-logging-configurations`, `update-logging-configuration`, `delete-logging-configuration` |
| Tags | [tags.md](tags.md) | `ivs tag-resource`, `untag-resource`, `list-tags-for-resource`, `ivs-realtime tag-resource`, `untag-resource`, `list-tags-for-resource`, `ivschat tag-resource`, `untag-resource`, `list-tags-for-resource` |
