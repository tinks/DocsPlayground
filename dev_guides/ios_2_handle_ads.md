# Delegating Ad Types

When you have the correct insertion point, you can retrieve the ads from it and serve them. In order to do this, you first retrieve the array of slots \(VPSlot\), and then from these slots you retrieve the array of ads \(VPAd\). In general, an insertion point will only have one slot.

When you have the ads in the slots, there are two aspects to check:

-   **Readiness**: is the ad ready to be shown. In case the ad comes directly from Pulse, then it is always ready, but for 3rd party ads we use lazy loading by default. Lazy loading, which means the ad is not preloaded, is used for 3rd party ads, because the provider of the ad may track it as an impression the moment it is loaded
-   **Type**: the type of the ad will determine how and where it should be shown. For example, an overlay ad is shown while the video is still playing, whereas a mid-roll will interrupt video playback and cover the full size of the player.

    **Note:** there may also be companion ads located within the ad \(VPAd.companions\), which are shown alongside any video and should not overlay the player in any way.


## Example: Dealing with Ad Types

This simple example shows you how you might forward the different ad types to be handled by different functions.

**Objective-C**

```
/* After finding the correct insertion point
 * delegate the handling of the different ad types to the appropriate function
 */

- (void) delegateAd:(VPAd *)ad onPlayer:(VideoPlayer *)player {
    if (!ad.isReady) {
        // load the ad if it is not ready yet
        // this requires access to the ad requester object
        [self.adRequester requestThirdPartyWithContainer:ad
                                                 success:^(VPAd *updatedAd) {
                                                     [self delegateAd:updatedAd onPlayer:player];
                                                 }  fail:^(NSError *error) {
                                                     NSLog(@"Failed to retrieve the requested ad %@", error);
                                                 }
         ];
    } else {
        switch (ad.type) {
            case VPAdTypeStandardSpot:
                [self showStandardSpotAd:ad onPlayer:player];
                break;
            case VPAdTypeStandardOverlay:
                [self showStandardOverlayAd:ad];
                break;
            case VPAdTypeVideoOverlay:
                [self showVideoOverlayAd:ad];
                break;
            case VPAdTypeImagesetOverlay:
                [self showImagesetOverlayAd:ad];
                break; 
            default:
                // Report that the ad type was not supported by this application
                [self.tracker reportError:VPTrackingErrorAdTypeNotSupported withTrackable:ad];
                break;
        }
}
```

**Swift**

```
func delegate(ad: VPAd, onPlayer player: VideoPlayer) {
	if ad.isReady == false {
		adRequester.requestThirdParty(container: ad, sucess: { ad in 
			self.delegate(ad, onPlayer: player)
		}, fail: { error in 
			print(@"Failed to retrieve the requested ad %@", error)
		})
	} else {
		switch ad.type {
			case .StandardSpot: showStandardSpotAd(ad, onPlayer: player)
			case .StandardOverlay: showStandardOverlayAd(ad, onPlayer: player)
			case .VideoOverlay: showStandardVideoOverlayAd(ad, onPlayer: player)
			case .ImageSetOverlay: showImageSetOverlayAd(ad, onPlayer: player)
			case default: tracker.reportError(.AdTypeNotSupported, trackable: ad)
		}
	}
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

