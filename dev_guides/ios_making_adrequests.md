# Making Ad Requests

This tutorial shows how to use the adCallModule to make ad requests.



```
/*
* Make an ad call.
*/
-(void) makeAdCallForSlot:(NSString *) slot{

     // In the ContentMetadata object you set the tags, flags, shares and etc that are appropriate for your video content.
    VPContentMetadata *contentMetadata =
    [VPContentMetadata contentMetadataWithTags: [NSArray arrayWithObjects:@ "standard", nil]
                                         flags:[NSArray arrayWithObjects:@ "", nil]
                                   contentForm:VPContentFormShortForm
                                      category:@ "validation"
                                      duration: 600
                             contentIdentifier:@ ""];

     // In the RequestSettings object you set information about your videoplayer, bitrate and insertionpoint, for example, onBeforeContent (preroll).
    VPRequestSettings * requestSettings =
    [VPRequestSettings requestSettingsWithHeight: 300
                                           width: 400
                                      maxBitrate: 0
                              insertionPointType:slot];

     // Make the request to the Ooyala Pulse ad server.
    // The completion block get executed once the request is done.
    // If the request succeeds, ads will contain an array of VPAd objects and error will be nil.
    // If the request fails, ads will be an empty NSArray and error will be an NSError object with an error message explaining why if failed.
    [self.adCallModule requestAdsWithContentMetadata:contentMetadata
                                     requestSettings:requestSettings
                                     completionBlock:^(NSArray *ads, NSError *error){
                                          if(error){
                                             NSLog(@ "error: %@", error);
                                             [self playContent];
                                         } else{
                                             NSLog(@ "got %d ads.", [ads count]);
                                             [self playAds:ads];
                                         }
                                     }];

}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

