# Integration Resources

Here you will find the resources you will need to be able to perform an Ooyala Ad Solutions integration on the iOS platform.

## Ooyala Ad Products iOS 2.x Core Framework file

The core and core debug frameworks for the iOS 2.x SDK can be found on the [Downloads](http://help.ooyala.com/downloads) page.

The Ooyala Ad Products Core Framework file gives you access to the VPAdRequester and the VPTracker.

The VPAdRequester facilitates the requesting of ads from the Ooyala Pulse video ad server and parses the ad response into well formatted native objects for easy use. The VPTracker assists in performing the appropriate tracking requests for an ad and makes sure that the capping and consistency rules that Ooyala requires are properly enforced.

Althought the provided framework is in Objective-C, you can also use it to code your own integration in Swift.

## Online Reference documentation

Reference documentation can be found here: [iOS 2.x SDK documentation](http://pulse-sdks.ooyala.com/ios_2/latest/index.html)

## Demo Integration

Two demo integrations are provided for reference, to illustrate how an integration with the Ooyala Ad Products iOS 2.x SDK could be done and are intended to be an inspiration for you when designing your own application.

The first demo integration is written in Objective-C and is located here: [pulse-sdk-ios-2.x-core-sample](https://github.com/ooyala/pulse-sdk-ios-2.x-core-sample)

The second demo integration is written in Swift and is located here: [pulse-sdk-ios-2.x-core-sample-swift](https://github.com/ooyala/pulse-sdk-ios-2.x-core-sample-swift)

**Warning:** These demos are not intended to be used in production and Ooyala does not support or fix issues that may arise from blindly copying code from these demos into your app.

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

