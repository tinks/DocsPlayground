# Handling Passbacks

If an ad cannot be played, because an error occurred, it is sometimes still possible to show ads if 3rd party \(passback\) ad sources are available. To request a passback ad, you will need to have access to the ad requester, the type of error that occurred and the ad or creative object.

Building further on the example, which passes the correct media file to the player:

**Objective-C**

```
/*
* Simple example getting the linear ads for a standard spot, and
* dealing with certain errors and handling the passback 
*/

- (void) showStandardSpotAd:(VPAd *) ad onPlayer:(VideoPlayer *) player {
    if (ad.creatives.count > 0) {    
        // there will only ever be one creative for standard spot ads
        VPLinearCreative *spotAdCreative = (VPLinearCreative*)ad.creatives[0];
        NSURL *mediaUrl = [self getMediaUrlFromLinearCreative:spotAdCreative onPlayer:player];
        // potentially set up other parts of the ad, like a clickthrough URL
        if (mediaUrl) {
            [player playAd:mediaUrl];
        } else {
            // if no valid media file was found, then
            // request a passback ad to replace this one, if it is available
            if (ad.hasPassback) {
                // you need access to the ad requester object here
                [self.adRequester requestPassbackWithAdOrCreative:ad
                                                            error:VPTrackingErrorCreativeNoSupportedMediaFileFound
                                                          success:^(VPAd *updatedAd) {
                                                                  [self showStandardSpotAd:updatedAd onPlayer:player];
                                                          }
                                                             fail:^(NSError *error) {
                                                                  NSLog(@"Failed to request passback ad. %@", error);
                                                             }
                ];
            } else {
                // if no valid media file was found, and no passbacks are available
                // log an error
                NSLog(@"Failed to find a valid media file for ad %@", ad);
            }
        }
    } 
}

- (NSURL *) getMediaUrlFromLinearCreative:(VPLinearCreative *) creative onPlayer:(VideoPlayer *) player {
    NSURL *mediaUrl = nil;
    if (creative.mediaFiles.count > 0) {
        //code to get the correct media file
        //based on video player dimensions, required bitrate and MIME type
        mediaUrl = mediaFile.URL;
    }
    return mediaUrl;
}
```

**Swift**

```
func showStandardSpotAd(ad: VPAd, player: VideoPlayer) {
	if let firstCreative = ad.creatives().first where firstCreative is VPLinearCreative {
		if let mediaFile = getMediaUrlFromLinearCreative(firstCreative as! VPLinearCreative) {
			player.playAd(mediaFile)
		} else {
			if ad.hasPassback {
				adRequester.requestPassbackWithAdOrCreative(ad, error: .CreativeNoSupportedMediaFileFound, 
                                success: { updatedAd in
					self.showStandardSpotAd(updatedAd, player: player)
				    }, fail: { error in
					print("Failed to request passback ad ", error)
				    }
                            )
			}
		}
	}	
}
func getMediaUrlFromLinearCreative(creative: VPLinearCreative) -> NSURL? {
	return creative.mediaFiles.first?.URL 
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

