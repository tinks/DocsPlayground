# Setting Up and Configuring the AdCallModule

\[ooyala:hobXZ0dTpqK0lOpvk2Kxji\_LL1h5rTQu\]



Instantiate the AdCallModule using Lazy instantiation. The adCallModule takes a settings object where you can set the device container for the app and the persistent identifier for the individual user.

Refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md)for more details on the AdCallModule and its settings.

```
@synthesize adCallModule = _adCallModule;

/*
* Lazy instantiation of the VPAdCallModule. 
*/
-(VPAdCallModule *) adCallModule {
  if(!_adCallModule){
    VPAdCallModuleSettings * adCallModuleSetting = [[VPAdCallModuleSettings alloc]init];

    // adCallModuleSetting
    .deviceContainer = @"";
    // adCallModuleSetting
    .persistentIdentifier = @"";
    
    NSURL * vpHost = [NSURL URLWithString:@"http://vp-validation.videoplaza.tv"];
    
    _adCallModule = [[VPAdCallModule alloc]initWithHost:vpHost andSettings:adCallModuleSetting];
  }
  return _adCallModule;
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

