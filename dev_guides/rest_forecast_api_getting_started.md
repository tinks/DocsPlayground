# Getting Started

## Base URL

The Base URL for the Forecast API endpoints is https:// api.videoplaza.com/api/2.0.

## Requests

GET and POST requests are used. You pass parameters by using common REST parameters like PATH and QUERY, as well as HTTP HEADERS.

The body of the requests should be provided in JSON format and encoded using UTF-8.

## Responses

All responses contain an HTTP status code in the header and the body is in JSON format.

## Limitations

The following limitations apply to the Forecast API:

-   Forecast requests are limited to date ranges between tomorrow and 100 days from tomorrow. This means that the start date has to be a date in the future and the end date has to be a date up to 100 days from tomorrow's date.
-   IP targeting, Browser/OS targeting, and Time of Day/Day of Week targeting are not supported for both campaign and inventory forecasts.
-   Frequency capping is not supported for inventory forecasts.
-   You cannot have more than 20 forecasts running at one time for your account.
-   Time based breaks are not taken into account when doing both campaign and inventory forecasts.

**Parent topic:**[Forecast API](../../../oadtech/ad_serving/dg/rest_forecast_api.md)

