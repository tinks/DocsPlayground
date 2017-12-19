# Making Ad Requests

This tutorial shows how to make an ad request of the backend and get an ad response using the HTML5 SDK.

\[ooyala:FqbXB0dTrXx2dZSn-KjLxc780ySQV3iA\]



```
var adCallModule = new videoplaza.core.AdCallModule("http://vp-validation.videoplaza.tv"),
    contentMetadata = {
      category : 'validation',
      tags     : ['standard'],
    },
    requestSettings = {
      height : myPlayer.height,
      width : myPlayer.width,
      insertionPointType : 'onBeforeContent', //prerolls
      maxBitRate : 800
    };

//make new ad request
adCallModule.requestAds(contentMetadata, requestSettings, onSuccess, onFail);

// get ads array 0~N
function onSuccess(ads){
  console.log(ads);
}

function onFail(erroMsg) {
  console.log(erroMsg);
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 1.x\)](../../../oadtech/ad_serving/dg/html5_deprecated_phase2.md)

