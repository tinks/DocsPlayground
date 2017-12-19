# Getting Started

## Base URL

The base URL for the Booking API is https://api.videoplaza.com/api/1.0.

## Requests

GET, POST, PUT, and DELETE requests are all used, although most tasks can be accomplished with just GET and POST. You pass parameters by using common REST parameters like PATH, QUERY, and MATRIX, as well as HTTP HEADERS.

The body of the requests should be provided in XML format and encoded using UTF-8.

You generally retrieve lists of resources by making a GET request to:

**Example**

```
https://api.videoplaza.com/api/1.0/[resource_name]
```

You generally retrieve specific resources by making a GET request and adding matrix parameters like "id":

**Example**

```
https://api.videoplaza.com/api/1.0/[resource_name]/by_[resource_name]_id;id=123
```

## Responses

All responses contain an HTTP status code in the header and the body is in XML format.

**Parent topic:**[Booking API](../../../oadtech/ad_serving/dg/rest_booking_api.md)

