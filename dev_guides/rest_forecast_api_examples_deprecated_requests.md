# Examples: Deprecated Requests

**Warning:** Deprecated request.

This page gives an example of using the Forecast API endpoint for getting a finished forecast report based on forecast id.

**Note:** This request applies only to campaign forecasts.

## Get a Finished Forecast Report

**Example: Get the "Campaign Test Request" report**

*Request header:*

```
GET /api/2.0/forecast/report/650d41ed-aa77-4099-8bde-4a6271587dea HTTP/1.1
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
  "jobId": "c40efacd-b9f8-42d2-9e49-c31f864c22c7"
}
```

**Parent topic:**[Forecast API](../../../oadtech/ad_serving/dg/rest_forecast_api.md)

