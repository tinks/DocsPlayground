# Making Ad Requests

This tutorial explains how to make an ad request using the Android SDK.



```
package se.videoplaza;

import java.util.ArrayList;
import java.util.List;

import android.content.Intent;
import android.media.MediaPlayer;
import android.net.Uri;
import android.util.Log;
import android.view.MotionEvent;
import android.view.View;
import android.view.View.OnTouchListener;
import se.videoplaza.custom.CustomMediaController;
import se.videoplaza.custom.CustomVideoView;
import se.videoplaza.kit.adrequestor.AdRequestor;
import se.videoplaza.kit.adrequestor.ContentMetadata;
import se.videoplaza.kit.adrequestor.RequestSettings;
import se.videoplaza.kit.adrequestor.AdRequestorSettings;
import se.videoplaza.kit.model.Ad;
import se.videoplaza.kit.model.LinearCreative;
import se.videoplaza.kit.tracker.Tracker;

public class VideoplazaPlugin {

  private AdRequestor adRequestor;
  private ContentMetadata contentMetadata;
  private RequestSettings requestSettings;

  public void init(CustomVideoView player, CustomMediaController controls) {
    Log.d("VideoplazaPlugin", "init VideoplazaPlugin");

    configVideoplaza();
  }

  /*
  * Init Android SDK
  */
  private void configVideoplaza() {
    Log.d("VideoplazaPlugin", "config");

    // init ad request module
    adRequestor = new AdRequestor("vp-validation.videoplaza.tv");

    // config ad settings
    contentMetadata = new ContentMetadata();
    contentMetadata.setCategory("validation");
    contentMetadata.addTag("standard");

    requestSettings = new RequestSettings();
    requestSettings.addInsertionPointType(RequestSettings.INSERTION_POINT_TYPE_ON_BEFORE_CONTENT); //preroll
    requestSettings.setHeight(270);
    requestSettings.setWidth(480);
    requestSettings.setMaxBitRate(700);

    adRequestor.requestAds(contentMetadata, requestSettings, new AdRequestor.AdRequestListener() {
      @Override
      public void onComplete(List ads) {
        Log.i("VideoplazaPlugin", ads.get(0).getId());
      }
    });
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

