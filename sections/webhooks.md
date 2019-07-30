# Webhooks

**NOTE: These requests require the *CentrePoint* API scope. (see [Scopes](scopes.md))**

## CentrePoint WebHooks System

For more info on CentrePoint Webhooks System, visit https://github.com/actigraph/CentrePointWebhookDocumentation

## List Webhook Registrations

Retrieves a list of webhooks to which a study is subscribed.

**Request:**

```http
GET /centrepoint/v3/Studies/{studyId}/Webhooks
```

**Response:**

This response is paginated. See [Pagination](pagination.md) for a description of pagination related fields returned.

|Field|Type|Description|
|-----|----|-----------|
|**id**|Number|Webhook Registration ID|
|**studyId**|Number|CentrePoint Study ID (see [Studies](studies.md))|
|**url**|String (URL)|Webhook URL|
|**createdDate**|String (ISO8601 Date)|Date webhook registration was created|
|**isDisabled**|Boolean|Is webhook disabled|
|**webhookEvents**|Array([Webhook Event](webhook_events.md))|List of webhook events for which webhook is registered (see [Webhook Events](webhook_events.md))

## Get Webhook Registration by ID

Retrieves a webhook registration to which a study is subscribed.

**Request:**

```http
GET /centrepoint/v3/Studies/{studyId}/Webhooks/{webhookId}
```

**Response:**

|Field|Type|Description|
|-----|----|-----------|
|**id**|Number|Webhook Registration ID|
|**studyId**|Number|CentrePoint Study ID (see [Studies](studies.md))|
|**url**|String (URL)|Webhook URL|
|**createdDate**|String (ISO8601 Date)|Date webhook registration was created|
|**isDisabled**|Boolean|Is webhook disabled|
|**webhookEvents**|Array([Webhook Event](webhook_events.md))|List of webhook events for which webhook is registered (see [Webhook Events](webhook_events.md))

## Webhooks History

Returns a history log of Webhook requests for a given study.

**Request:**

```http
GET /centrepoint/v3/Studies/{studyId}/Webhooks/{webhookId}/history
```

**Response:**

This response is paginated. See [Pagination](pagination.md) for a description of pagination related fields returned.

```json
{
    "items": [
      {
          "id": 34,
          "studyId": 236,
          "url": "https://www.example.com/",
          "createdDate": "2019-06-03T20:41:01",
          "isDisabled": false,
          "webhookEvents": [
              {
                  "id": 5,
                  "name": "raw_processing_complete"
              }
          ]
      }
    ],
    "links": {},
    "totalCount": 1,
    "limit": 100,
    "offset": 0
}
```