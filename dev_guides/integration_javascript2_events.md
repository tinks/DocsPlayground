# JavaScript 2.0 Events

Background and description of JavaScript 2.0 events for the Ooyala Ad Products Platform.

## Introduction

When serving ads to a video player there are many states and processes to monitor. Ooyala supplies a set of basic methods and functions, which you set up as event listeners in JavaScript, for following the ads and monitoring the events that are triggered by Ooyala Ad Products Platform. The events are related to two main context objects that are available when ads are playing; session and ad.

The session is an abstract definition of all the ad breaks and their ads for a video clip. The session is allowed to have an unlimited set of slots, which are basically ad breaks. Each slot has a number of positions where each position may host one ad. This definition of position is common and applies to linear ads, such as pre-rolls or mid-rolls, which are interrupting the video playback.

Some ads in the session are non-linear and are triggered outside the slots, usually on a regular schedule, i.e. the non-linear ads don't affect the video playback. Instead they add a layer of interactive graphics over or around the video. The term position applies to non-linear ads too, but refers to the count in the display frequency, for example, a new overlay ad is displayed every 45 seconds. After 2 minutes and 15 seconds the third Overlay is displayed, hence it is using the third position.

Different types of functionality in the Ooyala Ad Products platform trigger session events or ad events and they return different types of datasets. The differences are discussed in the Context object chapter.

## Methods

**addEventListener**

The addEventListener method let you define a listener function that helps you trigger your own functions when the Ooyala Ad Products platform triggers built-in event. This method is used for triggering both session events and ad events by simply naming the events that you want to trigger.

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|events|list|AdImpression|Supported values:1.  A string containing one of the supported events.
2.  Supported events in an array.
3.  The string "all" which will be equal to an array with all supported events. Mainly useful in adding all events at once.

|
|listener|string|myCallbackFunction\(event, context\)|The listener will trigger one of your functions and supply two objects; the event object for the triggered event and the context object for the data around the triggered event. This object will look different for ad events and session events.|

**removeEventListener**

The removeEventListener method let you remove a previously set listener function, set by the function addEventListener. You need to supply which event or events and listener function that should be cancelled for listening.

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|events|list|AdImpression|Supported values:1.  A string containing one of the supported events.
2.  One or more of the supported events in an array.
3.  The string "all" which will be equal to an array with all supported events.

|
|listener|string|myCallbackFunction\(event, context\)|The listener needs to supply the full identification; function name and parameters, meaning the event object and context object.|

**Methods Examples**

To understand the functionality and signature of add/remove listener we will go through few examples. Below is the given listener, which will be executed for every event that is triggered.

```
function myListener(eventObj, contextObj){
    // An Event Listener which will get the event object
    // and the context object
    .....
    .....
}
```

**Adding an event listener "AdImpression” to a function myListener.**

```
videoplaza_js_support.addEventListener(videoplaza_js_support.event.adimpression, myListener); 
```

**Add listener for multiple events to the function myListener**

```
var events = [videoplaza_js_support.event.adimpression, videoplaza_js_support.event.adstarted];
videoplaza_js_support.addEventListener( events, myListener);
```

**Adding all events in one go, to the function myListener**

```
videoplaza_js_support.addEventListener(videoplaza_js_support.event.all, myListener); 
```

**Removing an event listener "AdImpression” to a function myListener**

```
videoplaza_js_support.removeEventListener(videoplaza_js_support.event.adimpression, myListener); 
```

**Removing listener for multiple events to the function myListener**

```
var events = [videoplaza_js_support.event.adimpression, videoplaza_js_support.event.adstarted];
videoplaza_js_support.removeEventListener( events, myListener);
```

**Removing all events in one go, to the function myListener**

```
 videoplaza_js_support.removeEventListener(videoplaza_js_support.event.all, myListener); 
```

**Add and remove event listener**

In a situation in which there is a need to register a listener to all event except AdRemainingTimeChange and AdVolumeChange event, the quickest way is by adding all events and then remove the events which you don't want to listen to. For example:

```
videoplaza_js_support.addEventListener(videoplaza_js_support.event.all, myListener);
videoplaza_js_support.removeEventListener(videoplaza_js_support.event.adremainingtimechange, myListener);
videoplaza_js_support.removeEventListener(videoplaza_js_support.event.advolumechange, myListener);
```

## The Event Object

**event**

The event object is the container of a triggered event. It has a type and a value. The type holds the event type triggered and the value is populated with any return value from the event. A timestamp property defines the time for when the event was triggered.

The event object is one of the parameters sent back to your custom listener function in the addEventListener and removeEventListener methods.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|type|string|AdImpression|type of event|
|value|string|string|object|
|timestamp|string|1317996174|Timestamp in milliseconds according to the EPOC standard.|

## The Context Object

**context**

The context object is the container of the data behind a triggered event. For ad events it will hold two objects; session and ad. The objects are populated with different data depending on whether an ad event or session event was triggered. When an ad event is triggered the ad object property and the session object property are populated. When a session event is triggered the session object property is populated but the ad object property is set to null .

The context object is one of the parameters sent back to your custom listener function in the addEventListener and removeEventListener methods.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|ad|object|ad object|When an ad event is triggered this object is populated as an ad object. When a session event is triggered this property is set to null.|
|session|object|session object|The session property holds a session object to describe the session for the current event. Is populated for both session events and ad events.|

## The Ad Context Object

**ad**

The ad object contains all the information about the ad in a tracked event and details on the ad that tracked it.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|id|string|A42B568B-34A9-45F9-A2C3-81054D0613FA|Ooyala Ad Products specific id.|
|creative\_URL|string|http://\[client specific URL/service\].cdn.Videoplaza.\[tv/org\]/creatives/\[creative id\].\[mp4/flv\]|The URL the Ooyala Ad player uses to fetch the file for the ad \(ad creative\).|
|custom\_id|string|AlfaBeta123|Client specific id as specified when creating the ad in Campaign manager or through the Ooyala Ad Products Platform REST API.|
|duration|number|15.0|Duration of a linear ad in seconds.|
|format|string|-   imageset
-   site
-   splash
-   video
-   interactive
-   selector
-   standard
-   takeover
-   inskin

|Format for the ad triggering the event.1.  Overlay type: imageset, site, splash, video
2.  Spot type: interactive, selector, standard, takeover
3.  Skin type: inskin

|
|insertion\_point|number|55.0|A point on the video timeline where the ad is triggered.|
|type|string|-   pre-roll
-   mid-roll
-   post-roll
-   overlay
-   skin

|The ad type for the current ad. These types may by of any linear or non-linear ad type. The only ad that is not covered is the companion banner, which is a separate object property to the ad context object.|
|campaign|object|\[object\]|Reference object to the campaign that holds the current ad.|
|companion|object|\[object\]|Companion banner that is accompanying the current ad \(usually with pre-, mid and post-roll\).|
|goal|object|\[object\]|Reference object to the goal that holds the current ad.|
|position|object|\[object\]|The position of the ad when played. The term position is discussed in the ad.position object below.|

**ad.campaign**

The campaign object includes all the data about the campaign hosting the ad triggering the event.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|id|string|2F04FC79-6A0D-47DD-A872-9ED233C93DEA|Id generated by the Ooyala Ad Products platform when campaign is created in Campaign manager.|
|custom\_id|string|AlfaBeta456|Optional Campaign id added by the client to Ooyala's backend through Campaign Manager or REST API.|

**ad.companion**

The companion contains data on any companion banner accompanying a pre-mid- or post-roll.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|id|string|470B8A38-9C35-4E39-8E73-18CACFDB8C4C|Id generated by the Ooyala Ad Products platform when companion banner is created in Campaign manager.|
|custom\_id|string|AlfaBeta789|Optional Companion id added by the client to Ooyala's backend through Campaign Manager or REST API.|

**ad.goal**

The goal object includes all the data about the goal hosting the ad triggering the event.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|id|string|BA78672A-BAC5-4710-9564-3AFACD6BD0FD|Id generated by the Ooyala Ad Products platform when goal is created in Campaign manager.|
|custom\_id|string|AlfaBeta987|Optional Goal id added by the client to Ooyala's backend through Campaign Manager or REST API.|

**ad.position**

An ad position can mean two things. For linear ads that reside within ad breaks, position refers to the position in the break \(called slot\). For non-linear ads, like overlays, appearing at a given frequency, the position refers to the frequency count. The count begins with zero, meaning the third ad has a position index of 2.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|index|number|2|For linear ads the index refers to the position in the ad slot. For non-linear ads it is always set to null.|
|size|number|3|For linear ads size refers to the number of positions in an ad slot. For non-linear ads it is always set to null.|

## The Session Context Object

**session**

A session is the wrapper of all ads served for a video clip. This object contains metadata on how the current ad session is configured.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|id|string|A42B568B-34A9-45F9-A2C3-81054D0613FA|Id generated by the Ooyala Ad Products platform when the video player requests a set of ads from the Ooyala Ad server.|
|adplayer\_settings|object|\[object\]|Basic settings around the current integration of Ooyala and client.|
|content\_metadata|object|\[object\]|Metadata on the session hosting the ads.|

**session.adplayer\_settings**

The adplayer\_settings object includes all the data about the current client integrated the Ooyala Ad Player. To identify the client the Ooyala Ad Products platform employ two IDs; vp\_id and vp\_user. vp\_id support older client integrations and vp\_user is the new way.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|vp\_id|string|126D4584-B061-41E1-9981-2E49F0C61D3D|Id generated by the Ooyala Ad Products platform when the Ooyala team creates the client account.|
|vp\_user|string|channel9999|The Ooyala team adds a specific username for the client when Ooyala set up the account.|

**session.content\_metadata**

The metadata object contains data on the session hosting the ads. The metadata contains information sent by the video player called tags. Tags are keywords describing the current video content. Clients may target campaigns against any combination of tags as well as other parameters in the Ooyala Pulse Campaign manager.

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|duration|number|21.0|The duration of the video clip playing in the video player, in seconds.|
|tags|list|sports,golf|Tags are keywords for different type of video content. The client sets the tags.|

## All Events

These events are available to the Event Listener and are a part of the Event object. The Event object uses type for an event and Value as the return value attached to that event.

**Ad events**

|Attribute|Description|Event value|
|---------|-----------|-----------|
|AdStarted|When a linear or non-linear ad is displayed AdStarted will trigger.|null|
|AdStopped|When a linear or non-linear ad has stopped playing AdStopped is triggered.|null|
|AdLinearChange|An Ad interrupts a video playing and plays a linear ad. Usually used for overlay \(non-linear\) ads that trigger pop up video ads \(linear\).|null|
|AdExpandedChange|Some ads allow the user to interact with some interactive elements of the ad. This event is triggered by a non-linear ad when the ad is hidden or expanded.|null|
|AdRemainingTimeChange|The video ad is playing or the user skips ahead to a later part of the ad.|number|
|AdVolumeChange|When the user changes the volume of the ad this event is triggered.|The AdPlayers new volume|
|AdImpression|When an ad is visible to the user the AdImpression event will trigger.|null|
|AdVideoStart|When a linear ad starts playing.|null|
|AdVideoFirstQuartile|When a linear ad reaches the first quartile of the duration it is playing. Quartiles are the common standard for measuring time spent for online video ads.|null|
|AdVideoMidpoint|When a linear ad reaches the middle of the duration it is playing AdVideoMidpoint is triggered.|null|
|AdVideoThirdQuartile|When a linear ad reaches the third quartile of the duration it is playing, AdVideoThirdQuartile is triggered.|null|
|AdVideoComplete|When a linear ad reaches the end of the duration it is playing AdVIdeoComplete is triggered.|null|
|AdClickThru|AdClickThru is triggered when a user clicks an interactive part of an ad that is configured to lead to an external destination URL.|null|
|AdUserAcceptInvitation|When a user is invited to engage interactive features of an ad and accepts this invitation AdUserAcceptInvitation is triggered.|null|
|AdUserMinimize|When the user minimizes a non-linear ad the AdUserminimize event is triggered.|null|
|AdUserClose|When a user closes an ad using a visual close button, the AdUserClose event is triggered.|null|
|AdInteraction \(from VPAID specification's appendix\)|User interacts with an interactive element of an ad.|null|
|AdLog|AdLog is triggered as part of debugging generating a specific text output for different parts of the system.|string|

**Session events**

|Attribute|Description|Event value|
|---------|-----------|-----------|
|ContentStart|The Ooyala Ad Products Platform will trigger ContentStart when the video player starts playing the video. Ususally this happens after a pre-roll break.|null|
|SlotStart|SlotStart is triggered every time the Ooyala Ad Player encounters an ad break \(a slot\).|-   pre-roll
-   mid-roll
-   post-roll

|

## Error Events

**AdErrorEvent**

Dispatched when an AdError has occurred.

```
videoplaza_js_support.addEventListener(videoplaza_js_support.errorevent.ad,
                onAdError);
```

```
function onAdError(adError){
    adError.errorCode = "100"
    adError.thirdPartySourceURL = "http://url ...."
    adError.detailedMessage = "Could not parse third party ad.[etc]"
    adError.type = "adErrorEvent"
}
```

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|errorCode|string|100|The Error Code for the error, as described in VAST 3.|
|thirdPartySourceURL|string|http://....|The first third party vast url for the ad that caused the error.|
|detailedMessage|string|Could not parse third party ad.\[etc\]|A message with details on the error.|
|type|string|adErrorEvent|Type of error.|

**SessionErrorEvent**

Dispatched when a SessionError has occurred. There are four different main categories for session errors; "Invalid Response", "Invalid Argument", "Request Failed" and "Request Timeout". A detailed message will begin with one of these categories, followed by explicit information about occurred error.

```
videoplaza_js_support.addEventListener(videoplaza_js_support.errorevent.session,
                onSessionError);
```

```
function onSessionError(sessionError){
    sessionError.detailedMessage = "Invalid Response: [etc]"
    sessionError.type = "sessionErrorEvent"         
}
```

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|detailedMessage|string|Invalid Response: \[etc\]|A message with details on the error.|
|type|string|sessionErrorEvent|Type of error.|

**TrackingErrorEvent**

Dispatched when a tracking URL fails.

```
videoplaza_js_support.addEventListener(videoplaza_js_support.errorevent.tracking,
                onTrackingError);
```

```
function onTrackingError(trackingError){
    trackingError.ad = The ad associated with the tracking.
    trackingError.trackingEvent = VAST Ticket Tracking Event
    trackingError.statusCode = 200
    trackingError.URL = "http://url...."
    trackingError.message = Message describing the cause of failure.
    trackingError.type = "trackingErrorEvent"
}
```

|Property|Type|Example|Description|
|--------|----|-------|-----------|
|ad|Object|\[Object\]|Look above at "Ad Context object" section for Ad Object details.|
|trackingEvent|string|VAST Ticket Tracking Event \(impression, and so on\)|For which event the tracking error has occured.|
|statusCode|Int|200|The response status code for the http request.|
|URL|string|http://url....|The tracking url that failed.|
|message|string|string|Message describing the cause of failure.|
|type|string|trackingErrorEvent|Type of error.|

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

