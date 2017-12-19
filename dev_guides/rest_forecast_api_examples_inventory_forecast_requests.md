# Examples: Inventory Forecast Requests

This page gives examples of using the Forecast API endpoints for creating inventory forecasts and retrieving data from the finished inventory forecast reports.

## Create an Inventory Forecast Job

**Example: Create a new inventory forecast called "Inventory Test Request"**

*Request header:*

```
POST /api/2.0/forecast/inventory HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
{
    "targeting": {
        "targetingTemplates": null,
        "targetingRules": {
            "locationRules": [{
                "locationId": "11358",
                "locationType": "REGION",
                "locationName": "stockholms lan",
                "access": "ALLOW"
            }],
            "tagAndPartnerRules": [],
            "categoryRules": [{
                "categoryId": "dc74b090-c275-4646-a37f-4d5cff09997a",
                "categoryName": "Entertainment",
                "ruleType": "AT_LEAST_ONE_OF"
            }],
            "ipRules": [],
            "userAgentRules": [],
            "timeRules": [],
            "frequencyRules": [],
            "audienceRules": {}
        },
        "parentOverrides": {
            "contentRules": true
        }
    },
    "formatTypes": ["COMPANION_BANNER", "OVERLAY", "PREROLL", "PAUSE_AD", "POSTROLL", "MIDROLL", "SEEKROLL"],
    "deviceContainers": ["a6b5b571-c517-4597-861b-24d2d190d642", "27375d12-e3ad-46ce-ad78-eece92928c90", "145299c6-ba02-45de-9995-c2dfaba44c8c"],
    "startDate": 1467756000000,
    "endDate": 1468447199000,
    "trafficEstimate": 150,
    "name": "Inventory Test Request"
}
```

*Success response:*

```
HTTP status:
    202 (Accepted)

Header:
  Location: <URI with the location of your inventory forecast report>
```

## Get a Finished Inventory Forecast Report

**Example: Get the "Inventory Test Request" report**

*Request header:*

```
GET /api/2.0/forecast/report/inventory/c4c5e81c-eff6-46fe-82c1-06d3c100c7c4
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)  
  
Body:
{
  "totalInventory": {
    "total": 0,
    "inventoryByDate": {
      "2016-07-11T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      },
      "2016-07-09T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      },
      "2016-07-08T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      },
      "2016-07-10T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      }
    }
  },
  "unusedInventory": {
    "total": 0,
    "inventoryByDate": {
      "2016-07-11T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      },
      "2016-07-09T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      },
      "2016-07-08T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      },
      "2016-07-10T00:00:00.000+02:00": {
        "total": 0,
        "inventoryByFormat": {
          "PREROLL": {
            "total": 0
          },
          "MIDROLL": {
            "total": 0
          },
          "POSTROLL": {
            "total": 0
          }
        }
      }
    }
  },
  "name": "Inventory Test Request",
  "jobId": "51167264-f14d-43ca-8f7d-0914b25805c1"
}
```

**Parent topic:**[Forecast API](../../../oadtech/ad_serving/dg/rest_forecast_api.md)

