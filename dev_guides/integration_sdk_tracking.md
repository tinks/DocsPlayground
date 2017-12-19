# Tracking with the Ooyala Ad Products SDKs

When an ad is displayed, and a user sees or interacts with an ad in some way, all of this information has to be reported to someone. These statistics are the foundation for understanding the users behaviour and more importantly, is the basis for the whole economic model of ads.

This means that it is extremely important to make sure that each integration sends the correct tracking information at the correct time. Since the same information can be tracked by several parties in different ways it is vital to agree upon standardised definitions of when each individual event should be triggered to minimise discrepancies in numbers across companies. IAB has defined an industry standard for video ad serving called VAST. Ooyala strongly adheres to the definitions set in the VAST 2 and 3 standard, but also tracks additional events not included in the industry standard. You can find the VAST specification [here](http://www.iab.net/vast).

## Extended External tracking, 3rd Party Ads and Nested VAST Wrappers

Not only Ooyala is interested in what the viewers are doing. Ad agencies, 3rd party ad networks, and custom trackers all want to know when a user has seen an ad and interacted with an ad. For this reason the developer always needs to assume that there can be more than one tracking link that needs to be triggered. Our SDKs handle this behind the scenes and makes sure to trigger all the URLs that apply to an ad event.

## Capping of Tracking Events

All tracking events should only be triggered the first time an event occurs. This means that if an ad is rewinded and displayed again, no new impression or quartile events should be triggered. The exception to the capping rule is "interaction” events that can be triggered multiple times. An example of an "interaction” is the click-through event.

When using our SDKs, Ooyala automatically manages the capping of all the tracking events. This means that as long as you are using our SDKs, no additional logic is needed to manage the tracking capping. This also means that it is very important not to reuse ads and always make new ad requests when you have a new ad break.

## Tracking Events in the Ooyala Ad Products SDKs

The SDKs offer a tracking module to assist the tracking of an ad or creative object. Events are tracked by calling a method on the tracker using as arguments 1\) the ad or creative to track and 2\) what event to track. The tracker will extract the relevant URLs from the object and perform the tracking requests.

1.  **Ad Impression \(ad\)**

    Ad impression is used to track how many times a specific ad has been displayed to a viewer and is tracked as soon as the ad becomes visible to the user. This event is the single most important event to track because the impression metric is the basis for the financial model of ad delivery.

    In addition to monetary reasons, impression is key to managing the distribution of ads in the Ooyala Pulse ad server. Each ad campaign has been configured to deliver a fixed number of times during its lifetime and tracking the impression event when an ad is displayed counts against that ad's total delivery goal. Equally important is to track the impression event of all empty "inventory" ad objects encountered. Tracking impressions on an inventory ad object tells the Ooyala Pulse ad server that there was an opportunity to display an ad but that there were not enough ads booked in Pulse. Reporting this back to Pulse allows for the ad ops to better understand how much total "inventory" they have and put this in relation to how much Pulse has actually been able to deliver.

    Because the SDKs primarily support standard linear video ads, the ad impression event is usually triggered together with the quartile event, "ad started".

    VAST declares that the impression event be triggered at the moment the ad becomes visible to the user. Traditionally, the impression event is triggered when the first frame of a video ad has been displayed. It is important to make sure that the video actually starts playing before triggering this event.

2.  **Quartile Events \(creative\)**

    The quartile events are triggered when the ad playback has reached a specific playback position. The positions are set at 25% intervals of the ad's total duration:

    -   Ad started: 0%
    -   First quartile: 25%
    -   Mid point: 50%
    -   Third quartile: 75%
    -   Ad complete: 100%
    The quartile events should be triggered in sequence and as close to the quartile's playback position as possible. If a quartile event is skipped, the SDKs makes sure that any preceding untriggered quartile events are tracked as well to ensure that the statistics in Ooyala Pulse are consistent.

    **Example:** If the integration tracks "ad started” and then "third quartile” for an ad, the SDK will automatically track the "first quartile” and "mid point” events as well.


If the users skips or closes an ad, no further quartile events should be tracked.

## Close \(creative\)

The close event is triggered when the user clicks the skip button or in some other way actively closes the ad playback to see the main video content.

## Click-though \(creative\)

The click-through event is triggered when a viewer clicks on a linear video ad. This event can be triggered more than once.

## Creative View \(companion creative\)

Creative view is the equivalent to the impression event, but for a companion banner. This event should be triggered when the companion banner is added to the view.

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 2.x\)](../../../oadtech/ad_serving/dg/html5_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 1.x\)](../../../oadtech/ad_serving/dg/html5_deprecated_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

