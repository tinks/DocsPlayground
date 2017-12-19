# Examples: Campaign Forecast Requests

This page gives examples of using the Forecast API endpoints for creating campaign forecasts and retrieving data from the finished campaign forecast reports.

## Create a Campaign Feasibility Job

**Example: Create a new campaign forecast called "Campaign Test Request"**

*Request header:*

```
POST /api/2.0/forecast/campaign HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
{
    "campaign": {
        "advertiser": null,
        "agency": null,
        "brand": null,
        "name": "Campaign Test Request",
        "customId": null,
        "frontload": null,
        "priority": 5,
        "targeting": {
            "targetingTemplates": null,
            "targetingRules": {
                "locationRules": [],
                "tagAndPartnerRules": [],
                "categoryRules": [],
                "ipRules": [],
                "userAgentRules": [],
                "timeRules": [],
                "frequencyRules": [{
                    "impressions": 1,
                    "timeUnit": "QUARTER_HOUR"
                }],
                "audienceRules": {}
            },
            "parentOverrides": {}
        },
        "goals": [{   
            "customId": null,
            "name": "goalName",
            "startDate": 1467756000000,
            "endDate": 1468447199000,
            "priority": null,
            "frontload": null,
            "targeting": {
                "targetingTemplates": null,
                "targetingRules": {
                    "locationRules": [],
                    "tagAndPartnerRules": [],
                    "categoryRules": [],
                    "ipRules": [],
                    "userAgentRules": [],
                    "timeRules": [],
                    "frequencyRules": [],
                    "audienceRules": {}
                },
                "parentOverrides": {}
            },
            "variant": "NORMAL",
            "positionRestriction": "ANY",
            "deliveryGoal": {
                "value": 150000.0,
                "type": "IMPRESSION"
            },
            "ads": [{
                "name": "Ad 1",
                "customId": null,
                "format": "preroll_standard",
                "deviceContainers": ["86d28d24-d025-4633-a081-bea93de04dc3"],
                "startDate": null,
                "endDate": null
            }],
            "sequence": null,
            "dailyCap": null
        }]
    },
    "startDate": null,
    "endDate": null
}
```

Possible deliveryGoal types: IMPRESSION, SHARE\_OF\_VOICE, UNLIMITED\_IMPRESSION, COMPLETE, FIRST\_QUARTILE, SECOND\_QUARTILE, THIRD\_QUARTILE, CLICK\_THROUGH.

Possible variants: NORMAL, BUMPER, FILLER.

Possible positionRestriction types: ANY, FIRST, LAST, FIRST\_OR\_LAST, BREAK\_EXCLUSIVE.

*Success response:*

```
HTTP status:
    202 (Accepted)

Header:
  Location: <URI with the location of your campaign forecast report>
```

## Get a Finished Campaign Forecast Report

**Example: Get the "Campaign Test Request" report**

*Request header:*

```
GET /api/2.0/forecast/report/campaign/5a9e835d-8b8f-4ce0-8857-939a3b22528f HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

**Note:** By default, competing goals are included in the campaign forecast report. You can add the `**exclude-competing-goals**` query parameter with the value `**true**` to exclude any competing goals from the campaign forecast report.

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)   

Body:
{
  "campaign": {
    "advertiser": null,
    "agency": null,
    "brand": null,
    "name": "Campaign Test Request",
    "customId": null,
    "frontload": null,
    "priority": 5,
    "targeting": {
      "targetingTemplates": null,
      "targetingRules": {
        "locationRules": [],
        "tagAndPartnerRules": [],
        "categoryRules": [],
        "ipRules": [],
        "userAgentRules": [],
        "timeRules": [],
        "frequencyRules": [
          {
            "impressions": 1,
            "timeUnit": "QUARTER_HOUR"
          }
        ],
        "audienceRules": {}
      },
      "parentOverrides": {
        "frequencyRules": false,
        "locationRules": false,
        "timeRules": false,
        "tagAndPartnerRules": false,
        "contentRules": false,
        "ipRules": false,
        "userAgentRules": false
      }
    },
    "goals": [
      {
        "customId": null,
        "name": "goalName",
        "startDate": 1467756000000,
        "endDate": 1468447199000,
        "priority": null,
        "frontload": null,
        "targeting": {
          "targetingTemplates": null,
          "targetingRules": {
            "locationRules": [],
            "tagAndPartnerRules": [],
            "categoryRules": [],
            "ipRules": [],
            "userAgentRules": [],
            "timeRules": [],
            "frequencyRules": [],
            "audienceRules": {}
          },
          "parentOverrides": {
            "frequencyRules": false,
            "locationRules": false,
            "timeRules": false,
            "tagAndPartnerRules": false,
            "contentRules": false,
            "ipRules": false,
            "userAgentRules": false
          }
        },
        "variant": "NORMAL",
        "positionRestriction": "ANY",
        "deliveryGoal": {
          "value": 150000,
          "type": "IMPRESSION"
        },
        "ads": [
          {
            "name": "Ad 1",
            "customId": null,
            "format": "preroll_standard",
            "deviceContainers": [
              "86d28d24-d025-4633-a081-bea93de04dc3"
            ],
            "startDate": null,
            "endDate": null
          }
        ],
        "sequence": null,
        "dailyCap": null
      }
    ]
  },
  "forecasts": {
    "goalName": {
      "deliveryGoal": {
        "value": 150000,
        "type": "IMPRESSION"
      },
      "customId": null,
      "name": "goalName",
      "forecastedDelivery": 0,
      "accessibleInventory": 0,
      "deliveryMargin": 0
    }
  },
  "unusedInventory": 0,
  "unusedInventoryByDay": {
    "2016-07-05T22:00:00.000+0000": 0,
    "2016-07-06T22:00:00.000+0000": 0,
    "2016-07-07T22:00:00.000+0000": 0,
    "2016-07-08T22:00:00.000+0000": 0,
    "2016-07-09T22:00:00.000+0000": 0,
    "2016-07-10T22:00:00.000+0000": 0,
    "2016-07-11T22:00:00.000+0000": 0,
    "2016-07-12T22:00:00.000+0000": 0
  },
  "maximumDelivery": 0,
  "maximumDeliveryByDay": {
    "2016-07-05T22:00:00.000+0000": 0,
    "2016-07-06T22:00:00.000+0000": 0,
    "2016-07-07T22:00:00.000+0000": 0,
    "2016-07-08T22:00:00.000+0000": 0,
    "2016-07-09T22:00:00.000+0000": 0,
    "2016-07-10T22:00:00.000+0000": 0,
    "2016-07-11T22:00:00.000+0000": 0,
    "2016-07-12T22:00:00.000+0000": 0
  },
  "competingGoals": {
    "impactedBy": []
  },
  "name": "Campaign Test Request",
  "jobId": "ae672b84-484a-409e-a4ff-0170240fe27d"
}
```

**Parent topic:**[Forecast API](../../../oadtech/ad_serving/dg/rest_forecast_api.md)

