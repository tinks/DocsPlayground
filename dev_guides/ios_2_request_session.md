# Request the Session

When a user selects a video for playback, you gather all information from the selected video and request the session from Pulse. This session object contains indirectly all ads and times to show these ads for the requested video. The information gathered from the video relates to:

-   **Content meta data**: contains information from the video that has a direct impact on which ads to pick, based on video category, video form, flags, tags, and so on.
-   **Request settings**: contains information about the quality and size of the ads that will be served, and also where \(insertion point\) and when \(insertion time\) the ads are served.

For more information about content meta data and request settings, refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md#)

**Objective-C**

```
/*
 * Request a session.
 */


-(void) requestAllAdSlotsForContent {

    // In the ContentMetadata object you set the tags, flags, shares, and so on, that are appropriate
    // for your video content.

    VPContentMetadata *contentMetadata = [VPContentMetadata new];
    contentMetadata.category = @"validation";
    contentMetadata.contentForm = VPContentFormShortForm;
    contentMetadata.identifier = @"";
    contentMetadata.contentPartner = @"";
    contentMetadata.duration = 600;
    contentMetadata.tags = @[@"standard"];
    contentMetadata.flags = @[];
    
    // In the RequestSettings object you set information about your video player, bitrate and desired
    // insertion points, for example, VPInsertionPointTypeOnBeforeContent (preroll).

    VPRequestSettings * requestSettings = [VPRequestSettings new]
    requestSettings.height = 300;
    requestSettings.width = 400;
    requestSettings.maxBitrate = 0;
    requestSettings.insertionPointFilter = VPInsertionPointTypeAll;

    // Make the request to the Ooyala Pulse ad server.
    // The success block is executed when the request was successful, otherwise the fail block is executed.
    // If the request succeeds, a VPSession object is available.
    // If the request fails, the error will be an NSError object with an error message explaining the failure.

    [self.adRequester requestSessionWithMetadata:contentMetadata requestSettings:requestSettings
                                         success:^(VPSession *adSession) {
                                             _adSession = adSession;
                                         }
                                            fail:^(NSError *error) {
                                                NSLog(@"Failed Retrieving Ad Session %@", error);
                                            }
     ];
}
```

**Swift**

```
private func contentMetadata() -> VPContentMetadata {
	let returnValue = VPContentMetadata()
	returnValue.tags = ["standard"]
	returnValue.category = "validation"
	returnValue.contentForm = .Short
	returnValue.identifier = ""
	
	return returnValue
}
private func requestSettings() -> VPRequestSettings {
	let requestSettings = VPRequestSettings()
	requestSettings.height = 300
	requestSettings.width = 400
	requestSettings.maxBitRate = 0
	requestSettings.insertionPointFilter = .All
	return requestSettings
}

func initializeAdService(completion:()-> Void) {
	self.adRequester.requestSessionWithMetadata(contentMetadata(), requestSettings: requestSettings(), success: { adSession in
		self.adSession = adSession
		completion()
		}) { error in
			print("Failed Retrieving Ad Session ", error)
	}
}
```

The session should be requested the moment you know which content the user wants to view.

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

