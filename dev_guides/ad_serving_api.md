# Ooyala Pulse REST API

Find out how to integrate Ooyala Pulse, leverage its power and export data to external systems. For example, using Ooyala Pulse REST API to integrate with a standalone booking system that handles both display and video campaigns.

## Overview

The Ooyala Pulse REST API is organised around the main resources available in the Ooyala Pulse user interface. In order to use it, you need to be familiar with the key concepts, representing the endpoints \(campaign, goal, client, targeting rules, campaign/inventory forecast ...\), for the Ooyala Pulse platform available in the [Ooyala Pulse User Guide](../ug/introduction.md).

You need to have an [Ooyala Pulse account](../ug/getting_started.md) that you can test the API against and an authentication token or an API key \(only for Ad API\) so that you can make API calls. For more information, refer to [Authentication](rest_api_authentication.md#).

Different Pulse API components have different:

-   base URLs,
-   authentication,
-   communication formats,
-   documentation locations.

The table belows provides a general overview of the main differences.

|Pulse REST API component|Base URL|Authentication|Input/Output Format|Available Swagger Documentation|
|------------------------|--------|--------------|-------------------|-------------------------------|
|[Booking API](rest_booking_api.md#)|https://api.videoplaza.com/1.0|Authentication token \(**X-VP-AUTH** header\)|XML|No available swagger documentation but you can find examples for all endpoints at [Booking REST API Endpoints](rest_booking_api_endpoints.md#).|
|[Goal Rules API v2](http://community.ooyala.com/t5/Adtech-Knowledge-Articles/Pulse-Goal-Rules-REST-API-V2/ta-p/8926)|https://api.videoplaza.com/api/v2|Authentication token \(**X-VP-AUTH** header\)|JSON|No available swagger documentation but you can find examples for all endpoints at [Pulse Goal Rules REST API V2](http://community.ooyala.com/t5/Adtech-Knowledge-Articles/Pulse-Goal-Rules-REST-API-V2/ta-p/8926)|
|[Ad API](rest_ad_api.md#)|https://api.videoplaza.com/v1|API key \(**x-o-api-key** header\)|JSON|[https://api.videoplaza.com/v1/swagger](https://api.videoplaza.com/v1/swagger)|
|[Reporting API](rest_reporting_api.md#)|https://api.videoplaza.com/api/2.0|Authentication token \(**X-VP-AUTH** header\)|JSON|[http://api.videoplaza.com/docs](http://api.videoplaza.com/docs)|
|[Targeting Template API](rest_targeting_template_api.md#)|https://api.videoplaza.com/api/2.0|Authentication token \(**X-VP-AUTH** header\)|JSON|[http://api.videoplaza.com/docs](http://api.videoplaza.com/docs)|
|[Forecast API](rest_forecast_api.md#)|https://api.videoplaza.com/api/2.0|Authentication token \(**X-VP-AUTH** header\)|JSON|[http://api.videoplaza.com/docs](http://api.videoplaza.com/docs)|

## Errors

The Ooyala Pulse REST API communicates errors through standard [HTTP status codes](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) to indicate the success or failure of an API request. Generally, the following pattern applies:

-   2xx: Pulse received, understood, and accepted a request.
-   3xx: The user agent must take further action in order to complete the request.
-   4xx: An error occurred in handling the request. The most common cause of this error is an invalid parameter.
-   5xx: Pulse received and accepted the request, but an error occurred in the Pulse service while handling it.

**Example Errors**

```
HTTP status:
  403 (Forbidden)

Body:
{
  "type": "ForbiddenError",
  "message": "You have used 5 (100%) of your 5 templates. Please remove obsolete templates in order to create new ones."
}
```

## Things Every Developer Should Know

1.  **One request at a time**: Only one request at a time towards Ooyala Pulse REST endpoints is allowed for a client.
2.  **Updates overwrite data**: Update requests replace data with the one sent in this request. If a field is not included, it is cleared in the Ooyala Pulse backend. Best practice is to first retrieve data for an entity, change values in that entity and then send it back in an update.

**HTTP Verbs**

|Verb|Description|
|----|-----------|
|GET|Used for retrieving resources.|
|POST|Used for creating resources.|
|PUT|Used for replacing resources or collections.|
|DELETE|Used for deleting resources.|

-   **[Authentication](../../../oadtech/ad_serving/dg/rest_api_authentication.md)**  

-   **[Booking API](../../../oadtech/ad_serving/dg/rest_booking_api.md)**  

-   **[Ad API](../../../oadtech/ad_serving/dg/rest_ad_api.md)**  

-   **[Reporting API](../../../oadtech/ad_serving/dg/rest_reporting_api.md)**  

-   **[Targeting Template API](../../../oadtech/ad_serving/dg/rest_targeting_template_api.md)**  

-   **[Forecast API](../../../oadtech/ad_serving/dg/rest_forecast_api.md)**  


**Parent topic:**[Developer Guides](../../../oadtech/ad_serving/dg/dg_introduction.md)

