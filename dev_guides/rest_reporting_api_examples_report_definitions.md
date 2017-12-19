# Examples: Report Definitions Requests

This page gives examples of using the Reporting API endpoints for managing report definitions.

## List All Report Definitions

**Example: list all reports in Insight**

*Request header:*

```
GET /api/2.0/report-definition HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)  

Body:
[
    {
        "id": "56de9277498e2bd57afc71ed",
        "name": "Campaign performance by device group",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "CAMPAIGN",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498e2bd57afc71ef",
        "name": "Category performance by campaign",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "TIME_PERIOD"
            },
            {
                "type": "CATEGORY",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498e2bd57afc71f1",
        "name": "Account performance by device group",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "TIME_PERIOD"
            }
        ]
    },
    {
        "id": "56de9277498e6096ecfa2aad",
        "name": "Advertiser performance by creative and day",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "ADVERTISER",
                "id": null
            },
            {
                "type": "TIME_PERIOD"
            }
        ]
    },
    {
        "id": "56de9277498e31479f896d89",
        "name": "Category performance by subcategory",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "CATEGORY",
                "id": null
            },
            {
                "type": "TIME_PERIOD"
            }
        ]
    },
    {
        "id": "56de9277498ed663342784c7",
        "name": "Campaign performance by creative",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "CAMPAIGN",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498e31479f896d87",
        "name": "Campaign performance by category",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "CAMPAIGN",
                "id": null
            },
            {
                "type": "CATEGORY",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498e31479f896d8b",
        "name": "Brand performance by creative and day",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "BRAND",
                "id": null
            },
            {
                "type": "TIME_PERIOD"
            }
        ]
    },
    {
        "id": "56de9277498e6096ecfa2aa9",
        "name": "Campaign performance by day",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "CAMPAIGN",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498ed663342784c9",
        "name": "Category performance by day",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "TIME_PERIOD"
            },
            {
                "type": "CATEGORY",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498ed663342784cb",
        "name": "Agency performance by creative and day",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "TIME_PERIOD"
            },
            {
                "type": "AGENCY",
                "id": null
            }
        ]
    },
    {
        "id": "56de9277498e6096ecfa2aab",
        "name": "Campaign performance by content partner",
        "created": null,
        "type": "default",
        "filters": [
            {
                "type": "CAMPAIGN",
                "id": null
            }
        ]
    }
]

```

## Fetch a report definition by id

**Example: retrieve specific report definition**

*Request header:*

```
GET /api/2.0/report-definition/56de9277498ed663342784c7 HTTP/1.1
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
    "id": "56de9277498ed663342784c7",
    "name": "Campaign performance by creative",
    "created": null,
    "type": "default",
    "filters": [
        {
            "type": "CAMPAIGN",
            "id": null
        }
    ]
}

```

**Parent topic:**[Reporting API](../../../oadtech/ad_serving/dg/rest_reporting_api.md)

