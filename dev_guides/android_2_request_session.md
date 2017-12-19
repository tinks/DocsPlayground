# Request the Session

When a user selects a video for playback, you gather all information from the selected video and request the session from Pulse. This session object contains indirectly all ads and times to show these ads for the requested video. The information gathered from the video relates to:

-   **Content meta data**: contains information from the video that has a direct impact on which ads to pick, based on video category, video form, flags, tags, and so on.
-   **Request settings**: contains information about the quality and size of the ads that will be served, and also where \(insertion point\) and when \(insertion time\) the ads are served.

For more information about content meta data and request settings, refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md#)

**Java**

```
/*
 * Request a session.
 */

public void  setUpAndRequestAdSession(){

    // In the ContentMetadata object you set the tags, flags, shares, and so on, that are appropriate
    // for your video content.
    ContentMetadata contentMetadata = new ContentMetadata();
    contentMetadata.setCategory("validation");
    contentMetadata.setContentForm(ContentMetadata.ContentForm.SHORT);
    contentMetadata.setIdentifier("");
    contentMetadata.setContentPartner("");
    contentMetadata.setDuration(600);
    contentMetadata.setTags(Arrays.asList("standard"));
    contentMetadata.setFlags(Arrays.asList(""));


    // In the RequestSettings object you set information about your video player, bitrate and desired
    // insertion points.

    RequestSettings requestSettings = new RequestSettings();
    requestSettings.setHeight(300);
    requestSettings.setWidth(400);
    requestSettings.setMaxBitRate(800);

    //Set the ad break position. In this example there are two ad breaks, one at 10 and one at 30 second.
    final List<Float> adBreakPositions = Arrays.asList(10f, 30f);
    requestSettings.setLinearPlaybackPositions(adBreakPositions);

    // Indicate the type of insertion point
    // Preroll ==> INSERTION_POINT_TYPE_ON_BEFORE_CONTENT
    // Midroll ==> INSERTION_POINT_TYPE_PLAYBACK_POSITION
    // Postroll ==> INSERTION_POINT_TYPE_ON_CONTENT_END

    List<RequestSettings.InsertionPointType> insertionPointTypeList = new ArrayList<>();
    insertionPointTypeList.add(RequestSettings.InsertionPointType.ON_BEFORE_CONTENT);
    insertionPointTypeList.add(RequestSettings.InsertionPointType.PLAYBACK_POSITION);
    insertionPointTypeList.add(RequestSettings.InsertionPointType.ON_CONTENT_END);

    requestSettings.setInsertionPointFilter(insertionPointTypeList);


    // Make the request to the Ooyala Pulse ad server.
    // The success block is executed when the request was successful, otherwise the fail block is executed.
    // If the request succeeds, a Session object is available.
    // If the request fails, the error will be an Error object with an error message explaining the failure.

    try {
        URL  pulseHost = new URL("vp-validation.videoplaza.tv");

        AdRequester adRequester = new AdRequester(pulseHost);

        adRequester.requestSession(contentMetadata, requestSettings, new AdRequester.SessionListener() {
            @Override
            public void onSuccess(Session session) {
                this.session = session;
            }

            @Override
            public void onFailure(com.ooyala.adtech.Error error) {
                Log.d("Demo Player", "Failed Retrieving Ad Session");
            }
        });
    } catch (MalformedURLException e) {
        e.printStackTrace();
    }

}
```

The session should be requested the moment you know which content the user wants to view.

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

