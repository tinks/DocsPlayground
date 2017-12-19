# Getting Started

## Base URL

The Base URL for the Ad API endpoints is https://api.videoplaza.com/v\#, where \# is the version number of the API.

The current version of the Ad API is 1.

## Requests

GET, POST and PUT requests are all used. You pass parameters by using common REST parameters like PATH and QUERY, as well as HTTP HEADERS.

The body of the requests should be provided in JSON format and encoded using UTF-8. The only exception to this rule is when you provided a serialised format of an asset when uploading it to Pulse. In this case, the body is an octet-stream.

## Responses

All responses contain an HTTP status code in the header and the body is in JSON format.

## Limitations

The following limitations apply to the Ad API:

-   When updating an ad \(PUT request\), all fields must be set. For example, if you exclude setting the start and/or end date for the ad, then they are unset and the ad inherits the start and end date from its goal.
-   Uploaded assets are only transcoded after they have been associated with at least one ad. The progress of transcoding can be followed in the asset factory in Pulse.
-   You cannot upload pre-transcoded assets through the API, which is possible if you upload them through Pulse.
-   Associating ads with goals is done through the Ad API, but dealing with goals and campaigns can only be done through the [Booking API](rest_booking_api.md).
-   Ads have two kinds of weights: explicit weights and proportional split \(no weight set\). All ads with proportional split share the remaining weight \(100% - explicit weights\). This means that explicitly setting the weight of an ad affects the weight of other ads that have proportional split. For example:

    You have 2 ads with no weight set. You add a third ad with weight 50%. The two previously added ads will now have 25% each \(they split the remaining 50%\).


**Parent topic:**[Ad API](../../../oadtech/ad_serving/dg/rest_ad_api.md)

