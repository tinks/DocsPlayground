# Handling Passbacks

If an ad cannot be played, because an error occurred, it is sometimes still possible to show ads if 3rd party \(passback\) ad sources are available. To request a passback ad, you will need to have access to the ad requester, the type of error that occurred and the ad or creative object.

Building further on the example, which passes the correct media file to the player:

**Java**

```
/*
* Simple example getting the linear ads for a standard spot, and
* dealing with certain errors and handling the passback 
*/

public void playStandardSpotAd(Ad ad, final VideoView videoPlayer) {

        if (ad.getCreatives().size() > 0) {
            // Get the first creative element.
            LinearCreative linearCreative = (LinearCreative) ad.getCreatives().get(0);

            Uri mediaUrl = getMediaUrlFromLinearCreative(linearCreative);

            // If URI is valid, replace the player source with the ad URI and start the video
            if(mediaUrl != null){
                videoPlayer.setVideoURI(mediaUrl);
                videoPlayer.start();
            } else {
                if(ad.hasPassback()){
                    this.adRequester.requestPassback(ad, new AdRequester.AdListener() {
                        @Override
                        public void onSuccess(Ad ad) {
                            playStandardSpotAd(ad, videoPlayer);
                        }

                        @Override
                        public void onFailure(com.ooyala.adtech.Error error) {
                            Log.i("Demo Player", "Failed to request passback ad");
                        }
                    });
                } else {
                    Log.i("Demo Player", "Failed to find a valid media file for ad with id : "+ ad.getIdentifier());
                }
            }

        }
    }


    public Uri getMediaUrlFromLinearCreative(LinearCreative linearCreative) {
        Uri mediaUrl = null;
        MediaFile mediaFile = selectAppropriateMediaFile(linearCreative.getMediaFiles());

        if (mediaFile != null) {
            final String adUriString = mediaFile.getURL().toString();
            // If URI is valid, replace the player source with the ad URI and start the video
            if (isValidURI(adUriString)) {
                videoPlayer.setVideoURI(Uri.parse(adUriString));
                videoPlayer.start();
            }
            // If URI is not valid, start the content
            else {
                Log.i("Ad Player", "Failed to parse the provided Uri");
            }
        }
        return mediaUrl;
    }


    public static boolean isValidURI(String uriStr) {
        try {
            Uri.parse(uriStr);
            return true;
        } catch (Exception e) {
            return false;
        }
    }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

