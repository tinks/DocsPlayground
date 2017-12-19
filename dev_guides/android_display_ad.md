# Displaying Video Ads

This tutorial shows how to correctly display ads.

\[ooyala:w5bXR0dTpEYATBSiQGiyg3HH9D5\_eDOA\]



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
import se.videoplaza.kit.model.Ad;
import se.videoplaza.kit.model.LinearCreative;
import se.videoplaza.kit.tracker.Tracker;


/*
* Ad player encapsulates all code that implements SDK.
*/

public class VideoplazaPlugin {

  private CustomVideoView videoplayer;
  private CustomMediaController controlBar;
  private AdRequestor adRequestor;
  private ContentMetadata contentMetadata;
  private RequestSettings requestSettings;
  private Uri videoContentURI;
  private List adsList = new ArrayList();
  private LinearCreative linearCreative; 

  public void init(CustomVideoView player, CustomMediaController controls) {
    Log.d("VideoplazaPlugin", "init VideoplazaPlugin");

    videoplayer = player;
    controlBar = controls;

    /*
    * Store a reference to the original video content, this should be done
    * as we will replace the player video source with the ad, then after the
    * ad has finish playing we ad the video source back.
    */
    videoContentURI = player.getVideoURI();

    configPlayer();

    configVideoplaza();
  }


  /*
  * #1 config metadata
  */
  private void configVideoplaza() {
    Log.d("VideoplazaPlugin", "config");

    contentMetadata = new ContentMetadata();

    adRequestor = new AdRequestor("vp-validation.videoplaza.tv");
    contentMetadata.setCategory("validation");
    contentMetadata.addTag("standard");
  }

  /*
  * #2 config player
  */
  private void configPlayer() {

    videoplayer.setOnPreparedListener(new MediaPlayer.OnPreparedListener() {
      @Override
      public void onPrepared(MediaPlayer mediaPlayer) {
        Log.i("DemoPlayer", "Player READY");

        controlBar.show();
      }
    });

    videoplayer.setMediaStateListener(new CustomVideoView.PlayPauseListener() {
      /*
      * #3 When the user click play we need to interrupt the video player and make an ad request
      */
      @Override
      public void onPlay() {
        Log.i("DemoPlayer", "Player PLAY");

        requestSettings = new RequestSettings();
        requestSettings.addInsertionPointType(RequestSettings.INSERTION_POINT_TYPE_ON_BEFORE_CONTENT);
        requestSettings.setHeight(270);
        requestSettings.setWidth(480);
        requestSettings.setMaxBitRate(700);

        newAdRequest(requestSettings);

        videoplayer.setMediaStateListener(null);
      }

      @Override
      public void onPause() {
        Log.i("DemoPlayer", "Player PAUSE");
      }
    });

    videoplayer.setOnCompletionListener(new MediaPlayer.OnCompletionListener(){
      /*
      * When the first ad is complete you should check if there is no more ads to be shown,
      * when all ads have been displayed the player replace the ad URI with the original
      * video content "videoContentURI" and start the playback.
      */
      @Override
      public void onCompletion(MediaPlayer arg0) {
        Log.i("DemoPlayer", "Player COMPLETED");
        
        // After this ad is displayed, remove from the list of "available" ads
        adsList.remove(0);

        // check if there is more preroll ads in the list
        checkNumOfAvailableAds();
      }
    });
  }

  /*
  * #4 make a new HTTP request to backend
  */
  private void newAdRequest(RequestSettings requestSettings) {
    Log.i("DemoPlayer", "NEW AD REQUEST");

    // first thing, we stop the player playing the content
    videoplayer.stopPlayback();

    adRequestor.requestAds(contentMetadata, requestSettings, new AdRequestor.AdRequestListener() {
      @Override
      public void onComplete(List ads) {
        adsList = ads;
        checkNumOfAvailableAds();
      }
    });
  }

  /*
  * #5 check how many ads you get back from Ooyala Pulse
  */
  private void checkNumOfAvailableAds() {
    Log.i("DemoPlayer", "Number of Ads to play: " + adsList.size());

    // if there is no ads in the list, start the content
    if (adsList.isEmpty()) {
      playContent();
    }
    // if there is ads to display, we check if the ad is a supported ad type
    else {
      filterAds();
    }
  }

  /*
  * #6 filter ads
  */
  private void filterAds() {

    Ad ad = adsList.get(0);

    // if it is a supported ad type, we play it
    if (ad.getType().equals(Ad.AD_TYPE_SPOT_STANDARD)) { 
      playAd(ad);
      return;
    }
    // if it is a inventory type, track as "inventory" and check for more ads in the list
    else if (ad.getType() == Ad.AD_TYPE_INVENTORY) {
      //track inventory
    }
    // if it is a unknown ad type, track as "error" and check for more ads in the list
    else {
      Log.i("DemoPlayer", "Ad Type not supported");
    }

    // remove the current ad from the list, and check next ad
    adsList.remove(0);
    checkNumOfAvailableAds();
  }

  /*
  * #7 Play the first ad in the list
  */
  private void playAd(final Ad ad) {
    Log.i("DemoPlayer", "CAMPAIGN ID: " + adsList.get(0).getCampaignId());

    // 1. get the first creative element
    linearCreative = (LinearCreative) ad.getCreatives().get(0);

    // 2. get the URI to the creative
    String adUriString = linearCreative.getMediaFiles().get(0).getUri();

    // 3. If URI is valid, replace the player source with the ad URI and start the video
    if (isValidURI(adUriString)) {
      videoplayer.setVideoURI(Uri.parse(adUriString));
      videoplayer.start();
    }
    // 3.1. If URI is not valid, start the content
    else {
      Log.i("DemoPlayer", "AD URI ERROR: Fail to parse Ad URI string");
      //start the player
      playContent();
      return;
    }
  }

  /*
  * #8 play the original content
  */
  private void playContent() {
    Log.i("DemoPlayer", "Start Video Content: " + videoContentURI);

    //clear previous error listener from the Ad content
    videoplayer.setOnErrorListener(null);

    // set new error listener for the Video content
    videoplayer.setOnErrorListener(new MediaPlayer.OnErrorListener() {
      @Override
      public boolean onError(MediaPlayer mp, int what, int extra) {
        Log.i("DemoPlayer", "Cant play the content - Player ERROR: " + what);
        return true;
      }
    });

    videoplayer.setOnPreparedListener(new MediaPlayer.OnPreparedListener() {
      @Override
      public void onPrepared(MediaPlayer mediaPlayer) {
        mediaPlayer.start();
      }
    });

    videoplayer.setVideoURI(videoContentURI);

    videoplayer.setOnCompletionListener(null);
    videoplayer.setOnTouchListener(null);
    controlBar.show();
  }

  /*
  * Check if the Ad URI is valid or not
  */
  public boolean isValidURI(String uriStr) {
    try {
      Uri.parse(uriStr);
      return true;
    }
    catch (Exception e) {
      return false;
    }
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 1.x\)](../../../oadtech/ad_serving/dg/android_phase2.md)

