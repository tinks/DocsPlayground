# Setting Up and Configuring the AdRequester

To show adverts before, during or after playing video content, the application needs to initiate an ad requester object. This object needs at least the host URL of the client's Pulse account, which can be found in the account settings in the Pulse manager. The ad requester object can also be initiated with the optional deviceContainer and persistentId parameters. For more information about these parameters, refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md#).

**Java**

```
/* 
* Instantiation of the AdRequester. 
*/

public AdRequester AdRequesterInitializer(){
    if(adRequester == null){    
        try {
            final URL pulseHost = new URL("http://se-showroom.videoplaza-staging.tv");
            String deviceContainer  = "";
            String persistentIdentifier = "";

            adRequester = new AdRequester(pulseHost,deviceContainer,persistentIdentifier);
        }catch (MalformedURLException e){
            e.printStackTrace();
        }
    }
    return adRequester;
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

