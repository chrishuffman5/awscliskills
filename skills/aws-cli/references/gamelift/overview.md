# AWS CLI v2 — GameLift

## Overview

Complete reference for all `aws gamelift` subcommands in AWS CLI v2. Covers game server hosting with EC2 and container fleets, custom game builds and scripts, game session management, player sessions, FlexMatch matchmaking, FleetIQ game server groups, aliases, custom locations, VPC peering, scaling policies, and Anywhere/container compute registration.

## Quick Reference — Common Workflows

### Upload a game server build
```bash
aws gamelift upload-build \
  --name "MyGameServer-v1.2" \
  --build-version "1.2.0" \
  --build-root ./build-output \
  --operating-system AMAZON_LINUX_2023
```

### Create an EC2 fleet
```bash
aws gamelift create-fleet \
  --name MyFleet \
  --build-id build-1234abcd-56ef-78gh-90ij-klmnopqrstuv \
  --ec2-instance-type c5.large \
  --fleet-type ON_DEMAND \
  --runtime-configuration 'ServerProcesses=[{LaunchPath=/local/game/MyServer,ConcurrentExecutions=1}]' \
  --ec2-inbound-permissions 'FromPort=7777,ToPort=7777,IpRange=0.0.0.0/0,Protocol=UDP'
```

### Create a game session
```bash
aws gamelift create-game-session \
  --fleet-id fleet-1234abcd-56ef-78gh-90ij-klmnopqrstuv \
  --maximum-player-session-count 10 \
  --name "MyGameSession"
```

### Start matchmaking
```bash
aws gamelift start-matchmaking \
  --configuration-name my-matchmaking-config \
  --players 'PlayerAttributes={skill={N=50}},PlayerId=player-1'
```

### Create a container fleet
```bash
aws gamelift create-container-fleet \
  --fleet-role-arn arn:aws:iam::123456789012:role/GameLiftContainerRole \
  --game-server-container-group-definition-name my-game-server-group \
  --instance-type c5.large
```

### Set up target-based auto-scaling
```bash
aws gamelift put-scaling-policy \
  --name KeepBuffer \
  --fleet-id fleet-1234abcd-56ef-78gh-90ij-klmnopqrstuv \
  --metric-name PercentAvailableGameSessions \
  --policy-type TargetBased \
  --target-configuration TargetValue=20
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Builds & Scripts | [`builds-scripts.md`](builds-scripts.md) | create-build, delete-build, describe-build, list-builds, update-build, upload-build, request-upload-credentials, create-script, delete-script, describe-script, list-scripts, update-script |
| Fleets | [`fleets.md`](fleets.md) | create-fleet, delete-fleet, describe-fleet-attributes, describe-fleet-capacity, describe-fleet-utilization, describe-fleet-events, describe-fleet-port-settings, describe-fleet-location-attributes, describe-fleet-location-capacity, describe-fleet-location-utilization, list-fleets, update-fleet-attributes, update-fleet-capacity, update-fleet-port-settings, create-fleet-locations, delete-fleet-locations, describe-fleet-deployment, list-fleet-deployments, describe-ec2-instance-limits, describe-instances, get-instance-access, describe-runtime-configuration, update-runtime-configuration |
| Container Fleets | [`container-fleets.md`](container-fleets.md) | create-container-fleet, delete-container-fleet, describe-container-fleet, list-container-fleets, update-container-fleet, create-container-group-definition, delete-container-group-definition, describe-container-group-definition, list-container-group-definitions, list-container-group-definition-versions, update-container-group-definition |
| Game Sessions | [`game-sessions.md`](game-sessions.md) | create-game-session, describe-game-sessions, describe-game-session-details, search-game-sessions, update-game-session, terminate-game-session, get-game-session-log, get-game-session-log-url, describe-game-session-placement, start-game-session-placement, stop-game-session-placement, create-game-session-queue, delete-game-session-queue, describe-game-session-queues, update-game-session-queue |
| Player Sessions | [`player-sessions.md`](player-sessions.md) | create-player-session, create-player-sessions, describe-player-sessions |
| Matchmaking | [`matchmaking.md`](matchmaking.md) | create-matchmaking-configuration, delete-matchmaking-configuration, describe-matchmaking-configurations, update-matchmaking-configuration, create-matchmaking-rule-set, delete-matchmaking-rule-set, describe-matchmaking-rule-sets, validate-matchmaking-rule-set, start-matchmaking, stop-matchmaking, start-match-backfill, describe-matchmaking, accept-match |
| Game Server Groups | [`game-server-groups.md`](game-server-groups.md) | create-game-server-group, delete-game-server-group, describe-game-server-group, list-game-server-groups, update-game-server-group, suspend-game-server-group, resume-game-server-group, register-game-server, deregister-game-server, describe-game-server, list-game-servers, update-game-server, describe-game-server-instances, claim-game-server |
| Aliases | [`aliases.md`](aliases.md) | create-alias, delete-alias, describe-alias, list-aliases, update-alias, resolve-alias |
| Locations | [`locations.md`](locations.md) | create-location, delete-location, list-locations |
| Scaling | [`scaling.md`](scaling.md) | put-scaling-policy, delete-scaling-policy, describe-scaling-policies, start-fleet-actions, stop-fleet-actions |
| Compute | [`compute.md`](compute.md) | register-compute, deregister-compute, describe-compute, list-compute, get-compute-access, get-compute-auth-token |
| VPC Peering | [`vpc-peering.md`](vpc-peering.md) | create-vpc-peering-authorization, delete-vpc-peering-authorization, describe-vpc-peering-authorizations, create-vpc-peering-connection, delete-vpc-peering-connection, describe-vpc-peering-connections |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
