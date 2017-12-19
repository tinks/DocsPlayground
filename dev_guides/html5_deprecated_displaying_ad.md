# Displaying Video Ads

This tutorial demonstrates how to display ads using the HTML5 SDK.



```
var originalSrc = myPlayer.currentSrc;

myPlayer.addEventListener('play', onPlay);
myPlayer.addEventListener('ended', onEnded);

// #1 when the user click play, we should interrupt the playback and make a new ad request
function onPlay(){
  myPlayer.removeEventListener('play', onPlay);
  myPlayer.addEventListener('play', onAdPlay);
  myPlayer.addEventListener('error', onError);

  myPlayer.pause();
  adCallModule.requestAds(contentMetadata, requestSettings, onSuccess, onFail);
}

// #2 get ads from backend and replace the <video> src with ad 
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

    myPlayer.src = currentAd.mediaFiles[0].uri;

    myPlayer.addEventListener('loadstart', function playerPlay() {
      this.removeEventListener('loadstart', playerPlay);
      myPlayer.play();
    }, false);
  }
}

// #3a when the ad start playing track impression and ad started
function onAdPlay() {
  myPlayer.removeEventListener('play', onAdPlay);
  //track impression and ad started
}

// #3b if ad fail to play track error
function onError() {
  myPlayer.removeEventListener('error', onError);
  //track error
}

// #4 when ad complete playing start the original content. Notice that you may have more than 1 
// ad to display, for example, 2 pre-rolls.
function onEnded() {
  myPlayer.removeEventListener('ended', onEnded);
  myPlayer.src = originalSrc;

  myPlayer.addEventListener('loadstart', function playerPlay() {
    this.removeEventListener('loadstart', playerPlay);
    myPlayer.play();
  }, false);
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(HTML5 1.x\)](../../../oadtech/ad_serving/dg/html5_deprecated_phase2.md)

