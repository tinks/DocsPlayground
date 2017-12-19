# Show the Creatives

When you know the type of the ad, and you have delegated the handling of the ad object to the correct function, you can retrieve the actual creatives \(VPCreative\) from the ad and show them. The creative object contains an array of media files \(VPMediaFile\) with different dimensions, bit rates, MIME types and so on. Based on these properties, you need to select the media file which matches your video player best. This media file then has a URL to retrieve and show the ad.

A simple example to show linear ads for, for example, a pre-roll:

**Objective-C**

```
/*
 * Simple example getting the linear ads for a standard spot
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
            // if no valid media file was found, then log an error
            NSLog(@"Failed to find a valid media file for ad %@", ad);
        }
    }
}

- (NSURL *) getMediaUrlFromLinearCreative:(VPLinearCreative *) creative onPlayer:(VideoPlayer *) player {
    NSURL *mediaUrl = nil;
    if (creative.mediaFiles.count > 0) {
        //code to get the correct media file
        //based on video player dimensions and required bitrate
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
		}
	}	
}
func getMediaUrlFromLinearCreative(creative: VPLinearCreative) -> NSURL? {
	return creative.mediaFiles.first?.URL 
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

