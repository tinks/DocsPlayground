The Ooyala Pulse Integration framework for iOS allows you to display ads served from [Ooyala Pulse](http://www.ooyala.com/products/video-advertising) along with your video content in the Ooyala Player for iOS. This is not the same text as before, which one to choose.

The OOPulseManager class provides the support for displaying Ooyala Pulse ads to your [OOOoyalaPlayer](http://apidocs.ooyala.com/ios_mobilesdk/class_o_o_ooyala_player.html).

## Prerequisites

- The [Ooyala Player](http://support.ooyala.com/resources/mobile-and-client-sdks) framework for iOS (aka the Ooyala Mobile SDK for iOS)
- The [Ooyala Pulse](http://support.ooyala.com/resources/mobile-and-client-sdks) framework for iOS, version 2.2.x

## Getting Started

1. Import the Ooyala Pulse Integration framework:
```
@import <OoyalaPulseIntegration/OoyalaPulseIntegration.h>
```

2. Create an OOPulseManager object and associate it with your OOOoyalaPlayer:
```
self.manager = [[OOPulseManager alloc] initWithPlayer:self.player];
self.manager.delegate = self;
```

3. Implement the OOPulseManagerDelegate method `pulseManager:createSessionForVideo:withPulseHost:contentMetadata:requestSettings:` in your delegate. Initial values for all parameters in this method are automatically taken from settings in your Backlot account, but if needed, you may modify the host location of your Ooyala Pulse account, persistent ID, content metadata, request settings and so on, before creating the session. For more information about these parameters, refer to [Ooyala Ad Products SDK Parameter Reference](http://support.ooyala.com/developers/ad-documentation/oadtech/ad_serving/dg/integration_sdk_parameter.html).
```
- (id<OOPulseSession>)pulseManager:(OOPulseManager *)manager
             createSessionForVideo:(OOVideo *)video
                     withPulseHost:(NSString *)pulseHost
                   contentMetadata:(VPContentMetadata *)contentMetadata
                   requestSettings:(VPRequestSettings *)requestSettings
{
  // Set the correct pulse host and options
  [OOPulse setPulseHost:pulsehost
        deviceContainer:nil
           persistentId:nil];

  // Here we assume a landscape orientation for video playback
  requestSettings.width = (NSInteger)MAX(self.view.frame.size.width, self.view.frame.size.height);
  requestSettings.height = (NSInteger)MIN(self.view.frame.size.width, self.view.frame.size.height);

  // Implement a way of determining the max
  // bitrate of ads to request.
  requestSettings.maxBitRate = [BandwidthChecker maxBitRate];

  return [OOPulse sessionWithContentMetadata:contentMetadata
                             requestSettings:requestSettings];
}
```

## Sample Application

The sample integration is coded in OBJ-C and is found [here](https://github.com/ooyala/ios-sample-apps/tree/stable/PulseSampleApp)

## Changelog

### Version 4.13.0 - 10 April, 2016

This is the first release of the Ooyala Pulse Integration framework.

<br><hr>
