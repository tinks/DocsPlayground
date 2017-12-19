# Tracking

This tutorial explains how to track ad events using the HTML5 SDK.



```
function onAdPlay() {
  myPlayer.removeEventListener('play', onAdPlay);

  //track impression and ad started
  tracker.track(standarAdsArr[0], videoplaza.core.Tracker.trackingEvents.ad.impression);
  tracker.track(currentAd, videoplaza.core.Tracker.trackingEvents.creative.start);
}

function onError() {
  myPlayer.removeEventListener('error', onError);
  //track error
  tracker.reportError(currentAd, videoplaza.core.Tracker.errorEvents.creative.invalidCreative);
}

function onEnded() {
  myPlayer.removeEventListener('ended', onEnded);
  myPlayer.src = originalSrc;

  myPlayer.addEventListener('loadstart', function playerPlay() {
    this.removeEventListener('loadstart', playerPlay);
    myPlayer.play();
  }, false);

  //track completed
  tracker.track(currentAd, videoplaza.core.Tracker.trackingEvents.creative.complete);
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 1.x\)](../../../oadtech/ad_serving/dg/html5_deprecated_phase2.md)

