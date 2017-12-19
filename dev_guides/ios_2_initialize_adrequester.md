# Setting Up and Configuring the VPAdRequester

To show adverts before, during or after playing video content, the application needs to initiate an ad requester object. This object needs at least the host URL of the client's Pulse account, which can be found in the account settings in the Pulse manager. The ad requester object can also be initiated with the optional deviceContainer and persistentId parameters. For more information about these parameters, refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md#).

**Objective-C**

```
/* 
* Lazy instantiation of the VPAdRequester. 
*/ 

-(VPAdRequester *) adRequester
{
    if(!_adRequester){
        NSString *const vpHost = @"http://vp-validation.videoplaza.tv";
         // adRequester settings
        NSString *const deviceContainer = @"";
        NSString *const persistentIdentifier = @"";

         _adRequester = [[VPAdRequester alloc]adRequesterWithHost:vpHost
                                                  deviceContainer:deviceContainer
                                                     persistentId:persistentIdentifier];
    }
    return _adRequester;
}
```

**Swift**

```
lazy var adRequester: VPAdRequester {
	return VPAdRequester(host: Constants.vpHost, deviceContainer: nil, persistentId: nil)
}()
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

