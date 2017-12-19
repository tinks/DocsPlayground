# Ooyala Ad Products SDK Parameter Reference

This document is a non-technical overview of the configuration options available in the Ooyala Ad Products SDKs and what they are used for. This should be used as a complement to the reference and implementation documentation available for each individual SDK.

## The Ooyala Pulse Integration Toolkit SDKs

The Ooyala Pulse Integration Toolkit SDKs add support for requesting ads from the Ooyala Pulse Ad server, parsing the response into native objects for easy use and managing the tracking of the correct ad event URLs for a given ad in HTML5, iOS and Android. The naming conventions and some of the techniques used are aligned with the coding convention of their respective platform and may vary slightly. Coding conventions aside, the individual modules that comprise the SDKs provide the same assistance and manage the same basic set of information.

## The AdCall / AdRequestor / AdRequester Module

The main module that manages the requesting and parsing of ads utilises three settings objects to compose the final ad request to the Pulse ad server. I will describe each settings object and their importance below. The main ad requesting module is called the following on the different platforms:

-   adCallModule \(HTML5\)
-   VPAdCallModule \(iOS 1.x\) or VPAdRequester \(iOS 2.x\)
-   AdRequestor \(Android 1.x\) or AdRequester \(Android 2.x\)

**vphost or host:** When the ad requesting module is initialised, the host for the Ooyala Pulse account must be provided. This is used to identify which Pulse account to request ads from. The host is derived from the "sub-domain” found in the Pulse UI and is formulated like this:

```
http://[sub-domain].videoplaza.tv
```

## General Configuration of the AdCall / AdRequestor

There are additional, optional, settings that can be applied to each ad request. The SDK holds these setting in a custom object that is applied to the ad requesting module.

This settings object is called:

-   adCallModuleSetting\(HTML5\)
-   VPAdCallModuleSettings \(iOS 1.x\) or passed in as parameters for initialising the VPAdRequester \(iOS 2.x\)
-   AdRequestorSettings \(Android 1.x\) or passed in as parameters for initialising the AdRequester \(Android 2.x\)

This settings object holds the following parameters:

-   **device container:** The device container in Ooyala Pulse is used for targeting and reporting purposes. This device container attribute is only used if you want to override the Pulse device detection algorithm on the Pulse ad server. This should only be set if normal device detection does not work and only after consulting Ooyala personnel. An incorrect device container value can result in no ads being served or incorrect ad delivery and reports.

-   **persistent identifier:** The persistent identifier is used to identify the end user and is the basis for frequency capping, uniqueness, DMP targeting information and more. Ooyala will normally generate and attempt to save a persistent ID as a cookie on your device. In environments that do not support 3rd-party cookies, such as iOS and Android native applications, this automatic id management will not work and it is then up to the integration to provide an id that is consistent for the individual end user and that persists between sessions.

    This ID can be any string as long as it is unique to each individual end user, although the GUID or UUID format is recommended. If the application has a login or other user id that is consistent across devices, this ID can be used to track uniqueness across device and reuse DMP tracking data across devices and platforms.


## Request Setting

The previous section covered player specific settings and should never change for any one individual user over time. This section covers the technical conditions surrounding the actual ad request.

The Ooyala Pulse ad server has a built-in asset selection algorithm that attempts to select the best possible video creative for your device. Pulse uses device detection to determine the best codec for your device and these request setting values are key for determining the best size and weight of the video creatives for your particular situation.

These settings should be updated when the ad request's technical conditions change. The request setting values are configured in the object:

-   requestSettings \(HTML5\)
-   VPRequestSettings \(iOS 1.x and 2.x\)
-   RequestSettings \(Android 1.x and 2.x\)

The request settings object contains the following parameters:

-   **height:** The height of the video player. This is used to determine the best size of the delivered asset.

-   **insertion point type:** This is the point, in relation to the main content, where the ad spot should be inserted. This will determine what type of ads are requested by the SDK. The insertion point types are defined as constants in the SDKs and are as follows:

-   **On before content:** Linear ads that are played before the main content starts \(Pre-rolls\).

-   **On content end:** Linear ads that are played after the main content has ended \(Post-rolls\).

-   **On playback position:** Linear ads that are to be displayed at a certain point on the main content's timeline \(Mid-rolls\). This value requires that you also set the playback position \(see [playback position](#playbackPosition)\).

-   **On pause content:**Linear ads that are played when the content is paused.

-   **On playback time:** This is for non-linear ads that should be displayed after the user has viewed the main content for X seconds \(Overlays\). Overlays are only supported in the current version of the Ooyala Pulse Flash SDKs.

-   **max bandwidth:** The maximum bandwidth in Kbps that your device has access to. You should only set this value if you have a reliable way of determining the actual available bandwidth. If you do not set anything here we will default to 400 Kbps.

    The Ooyala Pulse HTML5 and mobile SDKs, by design, do not perform bandwidth tests because there is no reliable generic way to do this on HTML5 and we do not want consume unnecessary data volume on mobile devices. For this reason it is up to the individual developer to implement bandwidth detection if they choose to.

    The one exception to this is Ooyala Ad Products iOS 1.x SDK \(not available in version 2.x\). iOS has a reliable way of detecting if the device has access to WiFi, so if we detect that it is connected to WiFi, we will perform a bandwidth test for you. Explicitly providing a max bandwidth in the request settings will override any measured values.

-   **playback position:** This is the point on the main content timeline, in seconds, that the "on playback position" \(Mid-roll\) ad slot should be displayed. A warning may be triggered if this value is higher than the duration of the main content.

-   **width:** The width of the video player. This is used to determine the best size of the delivered asset.


## Content Metadata Settings

This final section covers content-specific metadata. These values define the specific video content's rules, targeting options and metadata. These values are added to the metadata object:

-   contentMetadata \(HTML5\)
-   VPContentMetadata \(iOS 1.x and 2.x\)
-   ContentMetadata \(Android 1.x and 2.x\)

The content metadata object contains the following parameters:

-   **category**: The category is a string that is used to associate content with a category that has been defined for the client's account in the Ooyala Pulse UI. The value of the category can be the Pulse native ID of the category found in the Pulse UI or a human readable "alias” that has been associated with the category in the Pulse UI. Categories are used for reporting and targeting purposes in Pulse UI. It is also possible to apply individual ad policies to each category, controlling how many and what type of ads are returned.

-   **content form**: A piece of video content can be defined as either long form or short form content. Long form content can be the entire episode of a program, a full-length feature movie, or just a piece of content that is more than 10 minutes long. It is up to the client to define the threshold between short and long form. In the Pulse UI it is possible to configure individual ad policies for long and short form, adding an additional ad policy dimension to a category.

-   **content ID**: Content ID is used for forwarding the ID of the main content to 3rd-party trackers. This value is not used or tracked by Ooyala Pulse but can be added to request URLs for 3rd-party ad requests or additional tracking URLs via a placeholder macro in the Pulse UI.

-   **content partner**: The content partner is used to add an additional reporting dimension to the ads that are displayed. The content partner value can use the Pulse native ID of the content partner found in the Pulse UI or a human readable "alias” that has been associated with the content partner in the Pulse UI.

-   **duration**: This is the total duration of the main content.

-   **flags**: The flags are used to apply special rules and conditions to an ad request. For example, a piece of premium content has been sponsored and no pre-rolls should be displayed. Adding the flag "noprerolls” will prevent pre-rolls from being returned but mid-rolls and post-rolls will be available as normal.

    Supported flags are:

    -   nocom: No ads are returned at all
    -   noprerolls: No pre-rolls are returned
    -   nomidrolls: No mid-rolls are returned
    -   nopostrolls: No post-rolls are returned
    -   nooverlays: No overlays are returned
-   **tags**: Tags are freeform keywords that can be used for targeting and reporting purposes. Although the tags keywords are able to handle UTF-8 characters, we recommend refraining from using special characters like quotes \(‘ and "\) ampersand \(&\) comma \(,\) semi-colon \(;\).


**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 2.x\)](../../../oadtech/ad_serving/dg/html5_2_phase2.md)

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 1.x\)](../../../oadtech/ad_serving/dg/html5_deprecated_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

