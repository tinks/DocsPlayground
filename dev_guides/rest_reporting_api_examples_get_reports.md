# Examples: Report Requests

This page gives examples of using the Reporting API endpoints for requesting new reports, checking new report status, and retrieving report data.

## Request a New Report from a Report Definition

To create a new report, you need to supply a body to the request with the following format:

```
{
  "filters": [
    {}
  ],
  "id": "string" (The id of the report defintion to use)
}
```

The entries in the filter map should have one of the following structures:

```
{ "type":  "CAMPAIGN", 
  "id": ID 
},
{ "type":  "ADVERTISER",
  "id": ID 
},
{ "type":  "BRAND", 
  "id": ID 
},
{ "type":  "AGENCY", 
  "id": ID 
},
{ "type":  "CONTENT_PARTNER", 
  "id": ID
},
{ "type":  "CATEGORY", 
  "id":ID 
},
{ "type":  "TIME_PERIOD", 
  "dynamicTimePeriodType": dynamicTimePeriodType 
},
{ "type":  "TIME_PERIOD", 
  "start":  "2013-01-01T00:00:00", 
  "end":  "2013-01-02T00:00:00"
}

```

Possible `dynamicTimePeriodTypes`:

```
SO_FAR_THIS_WEEK, SO_FAR_THIS_MONTH, SO_FAR_THIS_QUARTER, SO_FAR_THIS_YEAR, YESTERDAY, LAST_WEEK, LAST_MONTH, LAST_QUARTER, LAST_YEAR, LAST_7_DAYS, LAST_30_DAYS, LAST_90_DAYS, LAST_365_DAYS
```

**Example: Request "Campaign performance by creative" report**

*Request header:*

```
POST /api/2.0/report?useNames=false HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
Content-Type: application/JSON
Content-Length: 114
```

**Note:** The `**useNames**` query parameter can have the following values:

-   **false**: this returns entity id, for example `"4068c007-a3df-484b-b9a6-b62813f3ea89"`.
-   **true**: this returns entity name, for example `"royco_sauce_2016"`.

*Request body:*

```
{
  "filters": [
  {"type": "CAMPAIGN", "id": "1cc9f23e-6b18-494b-a638-4f1fd5b45e09"}],
  "id": "56de9277498ed663342784c7"
}
```

*Success response:*

```
HTTP status:
  202 (Accepted)

Header:
  Location: <URI with the location of your report>
```

## Check job status

**Example: check the status of the new "Campaign performance by creative" report**

*Request header:*

```
GET /api/2.0/report/job/5767b716498e988a95177567 HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
   201 (Created)

Header:
  Location: <URI with the location of your report>
```

## Fetch report data

**Example: retrieve the data from the new "Campaign performance by creative" report**

*Request header:*

```
GET /api/2.0/report/5767b716498e988a95177567?repeatDimensionValues=true HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

**Note:** The `**repeatDimensionValues**` query parameter can have the following values:

-   **false**: this does not repeat the entity id or entity name when getting a report for a structure, for example multiple category breakdowns. Instead, it returns the value "null".
-   **true**: this repeats the entity id or entity name when getting a report for a structure.

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)
 
Body:
{
    "id": "57614e85498e01b4aeb3cbaa",
    "headers": [
        "Ad",
        "Impressions",
        "Click-throughs",
        "CTR",
        "Completion_rate"
    ],
    "rows": [
        [
            "4068c007-a3df-484b-b9a6-b62813f3ea89",
            31984,
            563,
            0.0176,
            0.457
        ],
        [
            "60c60e4a-60e7-48bc-84d8-0e03e78dcd0b",
            546504,
            7870,
            0.0144,
            0.8771
        ]
    ]
}

```

**Note:** This returns a completed report, without subtotals.

**Parent topic:**[Reporting API](../../../oadtech/ad_serving/dg/rest_reporting_api.md)

