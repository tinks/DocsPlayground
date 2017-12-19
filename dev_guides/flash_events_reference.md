# Flash Events and PlayerState Reference

## Ooyala Flash Ad Player \(Plugin\) Event Flow

![Event Flow Diagram](../../image/plugin_event_flow.png)

## Ooyala Flash Ad Player Events

|Name|Description|Action|
|----|-----------|------|
|VpEventType.AD\_PLAYER\_READY|Triggered when the ad player has fetched ads and is ready to start|Call adPlayer.start\(\)to start the session|
|VpEventType.AD\_PLAYER\_COMPLETE|Triggered when the ad player has played the last ad for the session and has ended or been closed by the user|Move on to a new content item and start from the beginning|
|VpEventType.AD\_PLAYER\_VOLUME\_CHANGE|Triggered when the ad player volume changes. Required for syncing the ad player volume with the player volume|Update player volume to match ad player volume|
|VpCommandEventType.DISABLE\_CONTROLS|Triggered when the ad player tells you to disable user controls \(for example, when it is displaying a linear ad and the user should not be able to control the main content\)|Disable controls|
|VpCommandEventType.ENABLE\_CONTROLS|Triggered when the ad player tells you to enable controls again|Enable controls|
|VpCommandEventType.START|Triggered when the ad player is done playing pre-content linear ads|Start your main content|
|VpCommandEventType.PAUSE|Triggered when the ad player tells you to pause the content \(for example, when a linear ad is displayed\)|Pause the main content|
|VpCommandEventType.PLAY|Triggered when the ad player tells you to resume/play your content|Resume main content|

## Ooyala Flash Ad Player States

The PlayerState static constants should be used to inform the Flash Ad Player about the current state of the client video player.

-   PREPLAY: video player is in an initial preplay state
-   PLAYING: video player is playing
-   PAUSED: video player is paused
-   BUFFERING: main video content is buffering
-   BUFFER\_COMPLETE: main video content buffering is complete
-   CLIP\_COMPLETE: main video content playback is complete

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

