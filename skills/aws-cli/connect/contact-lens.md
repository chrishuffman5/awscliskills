# Contact Lens

Commands from the `aws connect-contact-lens` service.

### 29.1 `list-realtime-contact-analysis-segments`

Lists real-time contact analysis segments for a contact.

**Synopsis:**
```bash
aws connect-contact-lens list-realtime-contact-analysis-segments \
    --instance-id <value> \
    --contact-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID (1-256 chars) |
| `--contact-id` | **Yes** | string | -- | Contact ID (1-256 chars) |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token (1-131070 chars) |

**Output Schema:**
```json
{
    "Segments": [
        {
            "Transcript": {
                "Id": "string",
                "ParticipantId": "string",
                "ParticipantRole": "string",
                "Content": "string",
                "BeginOffsetMillis": "integer",
                "EndOffsetMillis": "integer",
                "Sentiment": "POSITIVE|NEGATIVE|NEUTRAL",
                "IssuesDetected": [
                    {
                        "CharacterOffsets": { "BeginOffsetChar": "integer", "EndOffsetChar": "integer" }
                    }
                ]
            },
            "Categories": {
                "MatchedCategories": ["string"],
                "MatchedDetails": {
                    "key": {
                        "PointsOfInterest": [ { "BeginOffsetMillis": "integer", "EndOffsetMillis": "integer" } ]
                    }
                }
            },
            "PostContactSummary": {
                "Content": "string",
                "Status": "FAILED|COMPLETED",
                "FailureCode": "QUOTA_EXCEEDED|INSUFFICIENT_CONVERSATION_CONTENT|FAILED_SAFETY_GUIDELINES|INVALID_ANALYSIS_CONFIGURATION|INTERNAL_ERROR"
            }
        }
    ],
    "NextToken": "string"
}
```

**Notes:**
- This API provides real-time transcription with sentiment analysis
- Categories are matched based on Contact Lens rules
- Post-contact summaries are generated after the contact ends
- Use the v2 API (`list-realtime-contact-analysis-segments-v2` in the `connect` service) for enhanced features
