# Error Handling In the Ooyala Ad Products SDKs

Even though we do everything we can to prevent errors from happening, they still occur and each application that integrates with Ooyala Ad Products needs to be able to recover when the unexpected happens. Ooyala can only offer support and guarantee reliable statistics if we know that your applications are stable and are integrated in a sound manner. For this reason Ooyala requires that all integrations with the Ooyala Pulse ad server be validated and approved by Ooyala before they are put into production.

## What Can Go Wrong?

A lot can go wrong, especially in mobile applications. For this reason Ooyala always checks certain critical points in an application. Below we have listed the scenarios that could potentially occur in your application and what you need to do about them.

Each of the scenarios below are tested during our validation process and your application has to pass all of these tests to be approved by Ooyala.

## Scenarios

|Error|Expected Action|How to Test|
|-----|---------------|-----------|
|404 response during ad request to Ooyala.|If for some reason the Ooyala server does not respond or returns a 404 result the application needs to be able to recover from this and resume the playback of the main content.|We test this by redirecting request to the Ooyala ad server to http://httpstat.us/404.|
|Timeout during ad request to Ooyala.|If for some reason the Ooyala server does not respond in a timely fashion, the application needs to be able to recover from this and resume the playback of the main content.|We test this by throttling requests to Pulse to 0.1 kbps. This effectively prevents the ad request from completing without actually blocking it.|
|Empty ad response.|If the add request returns a ticket without any ads in it, the application needs to behave as normal and resume the playback of the main content.|Adding the flag "nocom” \(no commercials\) to the ad request tells Pulse that no ads should be displayed and the ad response will be an empty XML ticket.|
|Ad response only contains "inventory".|An ad response may contain one or more "inventory” ads. These ads are placeholders for where a real ad could have been shown. When these are encountered the application should:-   Track the inventory as an error.
-   Move on to the next ad if there are more ads in the break or resume the playback of the main content.

|Add a targeting parameter, for example a tag that you know does not have any ads targeted to it.|
|404 when loading the video ad.|If for some reason the video creative included in an ad returns a 404 response, the application needs to be able to recover from this. When this occurs, the application should:-   Track the event "creative not found", or "invalid creative URI" for older SDKs, for that creative.
-   Move on to the next ad if there are more ads in the break or resume the playback of the main content.

|We test this by targeting a 3rd party VAST ad that we know has a faulty creative url. Alternatively, this can be tested by redirecting the creative ad request to http://httpstat.us/404.|
|Timeout when loading the video ad.|If for some reason the video creative included in an ad does not respond in a timely fashion, the application needs to be able to recover from this. When this occurs, the application should:-   Track the event "creative timeout", or "invalid creative" for older SDKs, for that creative.
-   Move on to the next ad if there are more ads in the break or resume the playback of the main content.

|We test this by throttling the request for the video creative to 0.1 kbps. This effectively prevents the ad creative from loading without actually blocking it.|
|Get an unsupported video ad.|If for some reason the video creative included in an ad is incompatible with the device and playback is not possible, the application needs to be able to recover from this. When this occurs, the application should:-   Track the event "creative display error", or "invalid creative" for older SDKs, for that creative.
-   Move on to the next ad if there are more ads in the break or resume the playback of the main content.

|We test this by targeting a 3rd party VAST ad that we know has a creative that is incompatible with the device or platform we are testing.|

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 2.x\)](../../../oadtech/ad_serving/dg/html5_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

