# Examples: Forecast Job Requests

This page gives examples of using the Forecast API endpoints for checking the status of forecasts and canceling forecasts.

## Check Job Status

**Example: Check the status of the "Campaign Test Request" forecast**

*Request header:*

```
GET /api/2.0/forecast/job/1ebd2817-2f71-43f0-afa4-9818aece71ac HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
        201 (Created)  
Header:
  Location: <URI with the location of your campaign forecast report>
```

Possible HTTP status responses and their meaning:

-   200 \(OK\): job has status QUEUED, PREPARING\_SIMULATION, PROCESSING or FAILED.
-   201 \(Created\): job completed. The location header contains the location of the finished forecast report.
-   404 \(Not Found\): no job with the given id found.

## Cancel Forecast Job

**Example: Cancel the "Campaign Test Request" forecast**

*Request header:*

```
POST /api/2.0/forecast/job/1ebd2817-2f71-43f0-afa4-9818aece71ac/cancel HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)
```

**Parent topic:**[Forecast API](../../../oadtech/ad_serving/dg/rest_forecast_api.md)

