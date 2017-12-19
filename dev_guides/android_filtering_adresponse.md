# Filtering Ad Response

This tutorial shows how to filter the ad response from the backend.



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

        adsList = ads;
        checkNumOfAvailableAds();
      }
    });
  }

  private void checkNumOfAvailableAds() {
    Log.i("VideoplazaPlugin", "Number of Ads to play: " + adsList.size());

    // if there is no ads in the list, start the content
    if (adsList.isEmpty()) {
      playContent();
    }
    // if there is ads to display, we check if the ad is a supported ad type
    else {
      filterAds();
    }
  }

  private void filterAds() {
    Ad ad = adsList.get(0); 

    if (ad.getType().equals(Ad.AD_TYPE_SPOT_STANDARD)) {
      playAd(ad);
      return;
    }
    else if (ad.getType() == Ad.AD_TYPE_INVENTORY) {
      //track impression
    }
    else {
      //track error
      playContent();
    }

    // remove the current ad from the list, and check next ad
    adsList.remove(0);
    checkNumOfAvailableAds();
  }

  private void playContent() {
    Log.i("VideoplazaPlugin", "play content");
  }

  private void playAd(final Ad ad) {
    Log.i("VideoplazaPlugin", "play ad");
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

