# AWS CLI v2 — Location Services

## Overview

Complete reference for `aws location`, `aws geo-maps`, `aws geo-places`, and `aws geo-routes` subcommands in AWS CLI v2. Covers location-based services including trackers, geofence collections, maps, place indexes, route calculators, API keys (v1 `location` namespace), and next-generation geo APIs for maps (tiles, sprites, static maps), places (geocoding, search), and routes (routing, isolines, waypoint optimization). This is a merged reference combining four CLI namespaces.

## Quick Reference — Common Workflows

### Create a tracker and update device position
```bash
aws location create-tracker --tracker-name MyTracker
aws location batch-update-device-position --tracker-name MyTracker \
  --updates '[{"DeviceId":"device1","Position":[-123.115,49.285],"SampleTime":"2026-01-15T10:30:00Z"}]'
```

### Create a geofence collection and add a geofence
```bash
aws location create-geofence-collection --collection-name MyGeofences
aws location put-geofence --collection-name MyGeofences --geofence-id warehouse-1 \
  --geometry '{"Circle":{"Center":[-123.115,49.285],"Radius":500}}'
```

### Geocode an address (v2 Places API)
```bash
aws geo-places geocode --query-text "1600 Pennsylvania Ave NW, Washington, DC"
```

### Calculate a route (v2 Routes API)
```bash
aws geo-routes calculate-routes \
  --origin "[-123.115,49.285]" \
  --destination "[-122.339,47.615]" \
  --travel-mode Car
```

### Get a static map image (v2 Maps API)
```bash
aws geo-maps get-static-map \
  --center "49.285,-123.115" --zoom 12 \
  --width 800 --height 600 --file-name map \
  --style Standard output.png
```

### Create an API key for frontend access
```bash
aws location create-key --key-name MyAppKey --no-expiry \
  --restrictions '{"AllowActions":["geo-maps:*","geo-places:*"],"AllowResources":["*"]}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Trackers | [`trackers.md`](trackers.md) | `location`: create-tracker, delete-tracker, describe-tracker, list-trackers, update-tracker, batch-update-device-position, batch-get-device-position, batch-delete-device-position-history, get-device-position, get-device-position-history, list-device-positions, verify-device-position, associate-tracker-consumer, disassociate-tracker-consumer, list-tracker-consumers |
| Geofences | [`geofences.md`](geofences.md) | `location`: create-geofence-collection, delete-geofence-collection, describe-geofence-collection, list-geofence-collections, update-geofence-collection, put-geofence, get-geofence, list-geofences, batch-put-geofence, batch-delete-geofence, batch-evaluate-geofences, forecast-geofence-events |
| Maps | [`maps.md`](maps.md) | `location`: create-map, delete-map, describe-map, list-maps, update-map, get-map-tile, get-map-glyphs, get-map-sprites, get-map-style-descriptor |
| Place Indexes | [`place-indexes.md`](place-indexes.md) | `location`: create-place-index, delete-place-index, describe-place-index, list-place-indexes, update-place-index, search-place-index-for-text, search-place-index-for-position, search-place-index-for-suggestions, get-place |
| Route Calculators | [`route-calculators.md`](route-calculators.md) | `location`: create-route-calculator, delete-route-calculator, describe-route-calculator, list-route-calculators, update-route-calculator, calculate-route, calculate-route-matrix |
| Keys | [`keys.md`](keys.md) | `location`: create-key, delete-key, describe-key, list-keys, update-key |
| Geo Maps | [`geo-maps.md`](geo-maps.md) | `geo-maps`: get-tile, get-glyphs, get-sprites, get-style-descriptor, get-static-map |
| Geo Places | [`geo-places.md`](geo-places.md) | `geo-places`: geocode, reverse-geocode, search-text, search-nearby, get-place, autocomplete, suggest |
| Geo Routes | [`geo-routes.md`](geo-routes.md) | `geo-routes`: calculate-routes, calculate-route-matrix, calculate-isolines, optimize-waypoints, snap-to-roads |
| Tags | [`tags.md`](tags.md) | `location`: tag-resource, untag-resource, list-tags-for-resource |
