# Getting Started

## Base URL

The Base URL for the Reporting API endpoints is https:// api.videoplaza.com/api/2.0.

## Requests

GET and POST requests are used. You pass parameters by using common REST parameters like PATH and QUERY, as well as HTTP HEADERS.

The body of the requests should be provided in JSON format and encoded using UTF-8.

## Responses

All responses contain an HTTP status code in the header and the body is in JSON format.

## Limitations

The following limitations apply to the Reporting API:

-   You can only create reports based on existing report definitions. You cannot create new custom reports.
-   Retrieving a report returns report data without subtotals.
-   You cannot pull a report as Excel or view a report in browser.
-   You cannot share a report.
-   You cannot add a report to a relevant menu, for example the "Campaign performance by creative" report cannot be added to the campaign menu.

**Parent topic:**[Reporting API](../../../oadtech/ad_serving/dg/rest_reporting_api.md)

