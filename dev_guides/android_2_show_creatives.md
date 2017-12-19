# Show the Creatives

When you know the type of the ad, and you have delegated the handling of the ad object to the correct function, you can retrieve the actual creatives \(Creative\) from the ad and show them. The creative object contains a list of media files \(MediaFile\) with different dimensions, bit rates, MIME types and so on. Based on these properties, you need to select the media file which matches your video player best. This media file then has a URL to retrieve and show the ad.

A simple example to show linear ads for, for example, a pre-roll:

**Java**

```
/*
 * Simple example getting the linear ads for a standard spot
 */

private void playStandardSpotAd(Ad ad, VideoView videoPlayer) {

    if (ad.getCreatives().size() > 0) {
        // Get the first creative element.
        LinearCreative linearCreative = (LinearCreative) ad.getCreatives().get(0);

        // Select the media file that suits the desired bitrate. In this example the medial file with the highest bit rate is selected
		// but in a production application the best media file should be selected based on resolution/bandwidth/format considerations.
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
        } else {
            Log.i("Ad Player", "Failed to find a valid media file for ad : " + ad.getIdentifier());
        }
    }

}
 
 
MediaFile selectAppropriateMediaFile(List<MediaFile> potentialMediaFiles) {
    MediaFile selected = null;
    int highestBitrate = 0;
    for (MediaFile file : potentialMediaFiles) {
        if (file.getBitRate() > highestBitrate) {
            highestBitrate = file.getBitRate();
            selected = file;
        }
    }
    return selected;
}
 
public static boolean isValidURI(String uriStr) {
    try {
        Uri.parse(uriStr);
        return true;
    } catch (Exception e) {
        return false;
    }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

