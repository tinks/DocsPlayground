# Delegating Ad Types

When you have the correct insertion point, you can retrieve the ads from it and serve them. In order to do this, you first retrieve the array of slots \(VPSlot\), and then from these slots you retrieve the list of ads \(Ad\). In general, an insertion point will only have one slot.

When you have the ads in the slots, there are two aspects to check:

-   **Readiness**: is the ad ready to be shown. In case the ad comes directly from Pulse, then it is always ready, but for 3rd party ads we use lazy loading by default. Lazy loading, which means the ad is not preloaded, is used for 3rd party ads, because the provider of the ad may track it as an impression the moment it is loaded
-   **Type**: the type of the ad will determine how and where it should be shown. For example, an overlay ad is shown while the video is still playing, whereas a mid-roll will interrupt video playback and cover the full size of the player.

## Example: Dealing with Ad Types

This simple example shows you how you might forward the different ad types to be handled by different functions.

**Java**

```
/* After finding the correct insertion point
 * delegate the handling of the different ad types to the appropriate function
 */

public void HandleAdType(Ad ad, final VideoView videoPlayer) {

    if (!ad.isReady()) {
        adRequester.requestThirdParty(ad, new AdRequester.AdListener() {
            @Override
            public void onSuccess(Ad ad) {
                HandleAdType(ad, videoPlayer);
            }

            @Override
            public void onFailure(com.ooyala.adtech.Error error) {
                Log.i("Demo Player", "Failed to retrieve the requested ad");
            }
        });

    } else {
        switch (ad.getType()) {
            case STANDARD_SPOT:
                playStandardSpotAd(ad, videoPlayer);
                break;
            case INVENTORY:
                tracker.reportError(TrackingError.AD_NO_AD, ad);
                break;
            default:
                tracker.reportError(TrackingError.AD_TYPE_NOT_SUPPORTED, ad);
                break;

        }
    }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

