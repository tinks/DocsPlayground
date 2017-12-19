# Post-roll Shown Incorrectly

**Make sure that you are telling the ad player that the item has ended before taking any other actions.**

This is done by calling

```
adPlayer.setPlayerState(PlayerState.CLIP_COMPLETE);
```

The adPlayer will then display any post-rolls, and when the ad session is completely ended, it will dispatch

```
VpEvent.AD_PLAYER_COMPLETE
```

after which your player is free to move on to show a splash screen or move on to the next item.

## The pre-roll plays but the content does not start playing in the HTML5 ad player

When implementing our HTML5 ad player plugin there are a few important things to remember.

Upon loading the plugin our adplayer immediately looks for a video tag and stores the current video source url for later. If the video tag or its source hasn't been initialized upon loading the plugin, it will store an empty string. This means that when the video player is started it will replace the current source url with the source for an ad and when the ad has completed it sets the source back to the stored source url. If this stored source url is empty nothing will be played.

A few key points to remember are:

-   The video tag must have an ID so our plugin can access it.
-   The video's source has to be set before our plugin is loaded.
-   Our plugin has to be loaded immediately and not dynamically later on.
-   The script tag that loads our plugin must be in the body, after the video tag.

For more detail information go to the [HTML5](html5_2_diy_toolkit.md#) integration page.

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

