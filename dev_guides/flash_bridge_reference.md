# Flash Bridge Reference

The Ad Products bridge \(com.videoplaza.bridge\) will act as the glue between your video player and the Ooyala Flash Ad Player. It is responsible for locating and loading the correct version of the Flash Ad Player from Ooyala's servers, along with any required scripts, skins, fonts, and so on. The purpose of the bridge class is to make proper API calls to the Flash Ad Player based on the states and events sent from your video player.

## com.videoplaza.bridge.core.VideoplazaLoader

Extends com.videoplaza.api.utils.VideoplazaLoader.

This method attempts to initialise the Flash Ad Player using the supplied configuration object.

Success and failure callback methods are defined.

## com.videoplaza.bridge.core.VpAdPlayer

Extends com.videoplaza.api.VpAdPlayerWrapper.

Translates and communicates events from the video player to the Flash Ad Player.

## com.videoplaza.bridge.core.TimeReference

The Flash Ad Player will call this method every time it needs the video position.

This method should return the video player's current position.

## com.videoplaza.bridge.events.PlayerState

Definition of Player State constants required by the interface.

-   PREPLAY
-   PLAYING
-   PAUSED
-   BUFFERING
-   BUFFER\_COMPLETE
-   CLIP\_COMPLET
-   VOLUME\_CHANGE
-   RESIZE

## com.videoplaza.bridge.utils.IVideoplazaPlugin

|videoplazaLoadedFail|Flash Ad Player fails to load. Returns an error message.

|
|videoplazaLoadedSuccess|Flash Ad Player loads successfully. Returns the Ooyala Flash Ad Player object.

|
|setNewItem|Set a new media file configuration and make an ad request.|
|onAdModuleCreated|Every time a new ad module is created it will fire this method. This can be used to add further customisations and event listeners to the ad modules.

|
|Getters & Setters|Various getters and setters for the interface.-   fullscreen
-   x, y
-   width, height
-   volume
-   video position
-   video state: play, pause
-   video controls: enabled, disabled

|

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

