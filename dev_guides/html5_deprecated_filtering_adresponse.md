# Filtering Ad Response

This tutorial demonstrates how to filter the ads you have called from the backend using the HTML5 SDK.

\[ooyala:ZsbXB0dToDwMWkAIEu5YzZD1mx0n8KKC\]



```
var standarAdsArr = []; //keep track of 'usable' ads

// ads can be of 2 types: standard_spot or inventory
function filterAds(ads) {
  ads.forEach(function(ad, index, array) {
    switch (ad.type) {
      case 'standard_spot':
        standarAdsArr.push(ad);
        break;
      case 'inventory':
        // track as inventory
        break;
      default:
        // track as error, not supported ads
        break;
    }
  });
  standarAdsFilter(standarAdsArr[0]);
}

function standarAdsFilter(ad) {
  //sort the Creative(s), it can be of two types: video ads or companion banners
  for (var i = ad.creatives.length - 1; i >= 0; i--) {
    creative = ad.creatives[i];

    if (creative.id == 'video') {
      currentAd = creative;
    }

    if (currentAd === null || currentAd.mediaFiles[0] === undefined) {
      return;
    }

    console.log(currentAd);
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 1.x\)](../../../oadtech/ad_serving/dg/html5_deprecated_phase2.md)

