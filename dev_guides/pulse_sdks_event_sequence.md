# Event Sequence Scenarios

An integration with a Pulse SDK is event driven, which means that the logical flow of the application only continues if the correct events are sent from the application to the Pulse SDK, and all events sent from the Pulse SDK are handled correctly. This page provides scenarios of event sequences \(without errors\) for:

-   the basics for ad serving in a video player application:
    -   how to start an ad session
    -   how to handle pre-, mid- and postrolls
    -   how to end an ad session
-   handling pause ads
-   extending an ad session

## Start the Ad Session and Handle Prerolls \(and Midrolls\)

The following image shows an example of the events sent between the video player application and the Pulse SDK, when a viewer selects a video for playback.

![Start Ad Session and Handle Prerolls](../../image/dg_pulse_sdk_scenario_start_ad_session.png)

For each new video started, a new session is requested by the application. Before video content playback starts, the Pulse SDK checks if prerolls are available in the session and initiates an ad break if this is the case. When the prerolls have been shown, the video content playback starts and the video player application sends updates about playback progress. Based on this progress, the Pulse SDK checks when and if midrolls should be shown. The process of showing midrolls follows the same pattern as prerolls.

The following table explains in more detail what happens at and between the video player application and the Pulse SDK:

|\#|App|Pulse SDK|
|--|---|---------|
|1|Sets up the Pulse host URL and optionally a log listener.||
|2|Requests a session from the Pulse SDK and sends **startSession** as soon as the user initiates video content playback.||
|3||Verifies if pre-rolls must be served before the content is started. If this is the case, the Pulse SDK sends the **startAdBreak** event to tell the player to stop any content playback.|
|4||Sends the **startAdPlayback** event which contains the ad and waits for the **adStarted** event.|
|5|Selects correct media file to display from the received ad and sends **adStarted** after the ad has started playing successfully.

If no appropriate media file is found or another error occurred, sends the **adFailed** event.

||
|6||If **adStarted** is received, an impression is tracked. In all other cases, an error is tracked and the process continues from step 11.|
|7|Sends **adPositionChanged** every 250ms.||
|8||Tracks quartiles and ad progress based on **adPositionChanged** events.|
|9|Sends **adFinished** when the ad has finished playback.||
|10||Tracks ad completion.|
|11||Verifies if more ads should be displayed. If that is the case, then the procedure starts again from step 4. If no more ads should be displayed, then the process goes to the next step.|
|12||Sends **startContentPlayback** event.|
|13|Starts content playback and sends **contentStarted** event.

In case an error occurs with content playback, the app stops the session with the **stopSession** event .

||
|14|Sends **contentPositionChanged** every 250ms.||
|15||Follows **contentPositionChanged** and based on the information verifies if mid-rolls should be shown. If it is time to show mid-rolls, the Pulse SDK sends the **startAdBreak** event again and steps 4 through 14 are repeated.|

## Handle Content Finished and Postrolls

The following image shows an example of events sent between the video player application and the Pulse SDK, when video content playback has finished and postrolls are available.

![Handle Content Finished and Postrolls](../../image/dg_pulse_sdk_scenario_postrolls.png)

The following table explains in more detail what happens at and between the video player application and the Pulse SDK:

|\#|App|Pulse SDK|
|--|---|---------|
|1|Sends **contentFinished** when content playback has finished.||
|2| |Verifies if postrolls should be shown. If that is the case, the Pulse SDK sends the **startAdBreak** event again and the same process is followed as for pre- and midrolls.

Otherwise, the process goes to the next step.

|
|3||Sends **sessionEnded** event.|

## Handle Pause Ads

The following image shows an example of events sent between the video player application and the Pulse SDK, when the viewer pauses and resumes the video content playback in case pause ads are available.

![Handle Pause Ads](../../image/dg_pulse_sdk_scenario_pause_ad.png)

The following table explains in more detail what happens at and between the video player application and the Pulse SDK:

|\#|App|Pulse SDK|
|--|---|---------|
|1|During content playback, if viewer pauses the content, sends the **contentPaused** event.||
|2||Verifies if pause ads should be displayed. If this is the case, the Pulse SDK sends **showPauseAd** which contains the pause ad and waits for either **adDisplayed** or **contentStarted**.|
|3|Verifies if the provided resource from the received ad can be displayed and sends **adDisplayed** after the ad has been displayed successfully.

If no supported resource is found or could not access the resource, sends the **adFailed** event.

||
|4|In the case viewer closed the displayed ad, sends the **adClosed** event.||
|5||Tracks pause ad displayed, and ad closed in case it was closed by the viewer.|
|6|Starts content playback and sends **contentStarted** event when viewer resumes the content playback.||
|7||Requests a new pause ad.|

## Request Session Extension

When providing live streams to your viewers, you can still request ad sessions in the same way you would for fixed length content and you can request more ads to be inserted when you need them. This mechanism uses session extension to request additional ads, with the following limitations:

-   You cannot request insertion points that have been requested already. For example, if you have already requested post-roll ads, then you cannot request them again.
-   You can request additional mid-rolls, but only for cue points that have not been requested yet. For example, if you have already requested midrolls to show after 10 seconds and 30 seconds of video content playback, you can only request more midrolls for times that differ from 10 and 30 seconds.
-   You may request pause ads multiple times, but the selected pause ad is always the last one requested. This means that the pause ad insertion point is always overwritten with the latest result from the session extension.

**Note:** If you leave out specific ad positions \(pre-, mid- and/or postrolls\) in the initial request for an ad session, you automatically get ads for all linear positions. This means that you would not be able to request, for example, postrolls in a session extension.

The following image shows an example of events sent between the video player application and the Pulse SDK, when the publisher initiates ad insertion:

![Request Session Extension](../../image/dg_pulse_sdk_scenario_session_extension.png)

The following table explains in more detail what happens at and between the video player application and the Pulse SDK:

|\#|App|Pulse SDK|
|--|---|---------|
|1|Sends the **extendSession** event containing the specifications of the extension, after the publisher's request comes in. Optionally, the **extendSession** event may contain a callback function, which is called in case the session was successfully extended.||
|2||Verifies the session extension specification, and creates additional ad requests in case of valid specifications.

In case the extension was not successful, the process ends here.

|
|3||When the session is successfully extended, calls the callback function if available.|
|4|Executes the callback function, if session extension was successful and callback function is available.||

**Parent topic:**[Pulse SDKs](../../../oadtech/ad_serving/dg/pulse_sdks_intro.md)

