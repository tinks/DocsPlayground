# Tracking

This tutorial shows how to correctly implement ad tracking using the Android SDK.

\[ooyala:1obXR0dTrHMgdVR\_R3V\_lGV\_k4sR13N1\]



```
// #1 only track "impression" and "start" if the video ad actually starts
videoplayer.setMediaStateListener(new CustomVideoView.PlayPauseListener() {

  @Override
  public void onPlay() {
    Log.i("DemoPlayer", "Player PLAY AD");

    tracker.track(ad, Tracker.AD_TRACKING_EVENT_IMPRESSION);
    tracker.track(linearCreative, Tracker.CREATIVE_TRACKING_EVENT_START);

    videoplayer.setMediaStateListener(null);
  }
});

// #2 if the ad object returns a video file that is not supported, then track error
videoplayer.setOnErrorListener(new MediaPlayer.OnErrorListener() {
  @Override
  public boolean onError(MediaPlayer mp, int what, int extra) {
    Log.i("DemoPlayer", "Cant play the Ad - Player ERROR: " + what);

    switch (what) {
      case MediaPlayer.MEDIA_ERROR_UNKNOWN:
        tracker.reportError(linearCreative, Tracker.CREATIVE_ERROR_INVALID_ASSET);
        break;
      case MediaPlayer.MEDIA_ERROR_SERVER_DIED:
        tracker.reportError(linearCreative, Tracker.CREATIVE_ERROR_INVALID_ASSET_URI);
        break;
      default:
        tracker.reportError(linearCreative, Tracker.CREATIVE_ERROR_INVALID_ASSET);
        break;
    }

    //start the player
    playContent();

    return true;
  }
});

// #3 when ad completes playback, track completed
videoplayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener(){

  @Override
  public void onCompletion(MediaPlayer arg0) {
    Log.i("DemoPlayer", "Player COMPLETED");

    tracker.track(linearCreative, Tracker.CREATIVE_TRACKING_EVENT_COMPLETE);
  }
});
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

