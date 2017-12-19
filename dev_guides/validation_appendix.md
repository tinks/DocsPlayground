# Appendix: Guide to Events and Params

You might find it useful to know what is under the hood of the ad request and the tracking events. These two tables show events and parameters usually found and used in most of the integrations.

## Events

|EVENT TYPE ID|EVENT TYPE NAME|EVENT TYPE DESCRIPTION|
|-------------|---------------|----------------------|
|**0**|**IMPRESSION**|**Mandatory. Fired at ad start.**|
|1|ACCEPT\_INVITATION| |
|2|COLLAPSE| |
|3|IMPRESSION2|Applicable to interactive spots.|
|4|ACCEPT\_INVITATION2| |
|7|CLOSE|Optional. Fired when the user clicks the skip/close button.|
|**10**|**INTERACTION**|**Optional. Fired on ad interaction. Can be triggered on click through, fullscreen, volume change, or whatever makes sense for your implementation.**|
|**14**|**AD\_START**|**Optional. Fired at ad start.**|
|**15**|**AD\_FIRST\_QUARTILE**|**Optional. Fired after 25% of ad is played.**|
|**16**|**AD\_MIDPOINT**|**Optional. Fired after 50% of ad is played.**|
|**17**|**AD\_THIRD\_QUARTILE**|**Optional. Fired after 75% of ad is played.**|
|**18**|**AD\_COMPLETE**|**Optional. Fired when ad finishes.**|
|**20**|**CLICK\_THROUGH**|**Mandatory. Fired on ad click.**|
|31|EXPAND| |
|32|MUTE| |
|33|UNMUTE| |
|34|PAUSE| |
|35|REWIND| |
|36|RESUME| |
|37|FULLSCREEN| |
|90|COMPANION\_IMPRESSION| |
|91|COMPANION\_IMPRESSION2| |
|100|TIME\_SPENT\_AD| |

Usually, you need to implement the bolded ones. The other events are not so commonly used or might depend on the type of integration. If you are unsure, implement the bolded ones and we will advise you if others might be useful for your scenario.

## Parameters

|PARAMETER NAME|PARAMETER DESCRIPTION|
|--------------|---------------------|
|tt|TICKET TYPE

Indicates type of the ad:

-   p - pre-roll
-   m - mid-roll
-   po - post-roll
-   o - overlay
-   pa - pause ad

|
|rt|RESPONSE TEMPLATE

The format of the response \(vp\_2.0, vast\_2.0, and so on\)

|
|rnd|RANDOM

Random string used for cache busting.

|
|cf|CONTENT FORM

Values:

-   short\_form
-   long\_form

It can configure different ad behaviour for different content form.

|
|s|SHARES

Comma separated list of categories targeted by the ad request.

|
|t|TAGS

Comma separated list of tags targeted by the ad request.

|
|m|MODEL

The model of the device, for example Nexus 7, iPhone, and so on.

|
|st|SUPPORTED TRACKING

Set by the SDK if you are using one.

|
|tid|TICKET ID|
|pid|PERSISTENT ID

Set it through a cookie or pass it as a request parameter. It is used for frequency capping.

|
|pf|PLATFORM

Required for non-HTML integrations.

|
|afr|ASSET FILTERING

-   0: filter off
-   1: filter on

Enables the filtering of the best asset type for your specific integration. It is turned on by default.

|
|cd|CONTENT DURATION|
|cv|CALLER VERSIONFilled by the SDKs.

|
|dcid|DEVICE CONTAINER IDENTIFIER

You can override the device container with the desired id or short name.

|
|ci|CONTENT ID

It can be used to request a specific ad.

|
|vbw|VIDEO BANDWIDTH

Maximum bandwidth of requested videos.

|
|vwt|VIDEO WIDTH

Expected width of video in pixels.

|
|vht|VIDEO HEIGHT

Expected height of video in pixels.

|
|xpb|VPAID PASSBACKS

Set to 1 to enable it.

|
|bp|BREAK POSITIONS

Comma separated numbers that indicate the times when cuepoints are triggered.

|
|tbbl|TIME BASED BREAKS LENGTH

Maximum duration in seconds for pre-, mid- and post-roll ad breaks.

|
|trs|TRACKING SCHEME

It can be used to override the scheme \(HTTP or HTTPS\) for the tracking links returned in an ad response.

|

**Parent topic:**[Validation Importance and Process](../../../oadtech/ad_serving/dg/validation_importance_process.md)

