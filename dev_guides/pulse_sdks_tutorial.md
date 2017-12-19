# Tutorial

This page describes in short the steps you need to perform to set up an integration using one of the Pulse SDKs. The examples given are for the Android Pulse SDK, but equivalent methods exist in the other Pulse SDKs \(HTML5, iOS and tvOS\). The steps to follow are:

1.  Initialise the Pulse SDK
2.  Implement the Pulse Session Listener
3.  Create the Pulse Session
4.  Start the Pulse Session
5.  Implement the remaining Pulse Session event methods
6.  Handle the Pulse Video Ads
    1.  Select the correct media file
    2.  Implement the ad event methods
7.  Handle the Pulse Pause Ads \(optional\)
    1.  Verify the supported resource file
    2.  Implement the pause ad event methods
8.  Implement Pulse Session Extension \(optional\)

## Initialise the Pulse SDK

During the startup of the video player application, you initialise the Pulse SDK and set up the connection to your Ooyala Pulse account. For example, in the Android Pulse SDK this is done with:

```
Pulse.setPulseHost(hostUrl, deviceContainer, persistentId);
```

where:

-   hostUrl is the URL to your Ooyala Pulse account, which can be created by taking your sub-domain and appending ".videoplaza.tv" after it. The sub-domain is found under Settings\>Account Settings\>Integration Information\>Sub-domain after logging into Ooyala Pulse.
-   deviceContainer is the identifier for a range of devices, used for targeting and reporting. In general, this parameter should be set to NULL to use Pulse's built-in device detection.
-   persistentId is the unique user identifier, like a cookie, used for frequency capping, audience targeting, and so on.

For more information about these parameters, refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md).

A code example would be:

```
Pulse.setPulseHost("http://pulse-demo.videoplaza.tv", null, null);
```

## Implement the Pulse Session Listener

To respond to the events coming from the Pulse SDK, you need to implement a listener which overrides all methods defined in the Pulse Session Listener protocol \(iOS, tvOS\) or interface \(Android, HTML5\). For example, in the Android Pulse sample integration, the listener interface is implemented in the [PulseManager.java](https://github.com/ooyala/pulse-sdk-android-2.x-sample/blob/master/app/src/main/java/com/ooyala/pulseplayer/PulseManager/PulseManager.java) class.

The methods that need to be overridden, for example, for the Android Pulse SDK can be found here: [Interface PulseSessionListener](http://pulse-sdks.ooyala.com/android_2/latest/com/ooyala/pulse/PulseSessionListener.html).

## Create the Pulse Session

When you know which video the viewer has selected in the video player application, you create the Pulse Session object, which is used to send the video player events to the Pulse SDK. For example, in the Android Pulse SDK this is done with:

```
Pulse.createSession(contentMetadata, requestSettings);
```

where:

-   contentMetadata is the object containing all meta data about the video requested by the viewer.
-   requestSettings is the object containing information about each position in the video where ads should be served.

For more information about these parameters, refer to [Ooyala Ad Products SDK Parameter Reference](integration_sdk_parameter.md).

A code example would be:

```
public class PulseManager implements PulseSessionListener {
 private PulseSession pulseSession;
 
...
 
 pulseSession = Pulse.createSession(getContentMetadata(), getRequestSettings());
 
...
 
 private ContentMetadata getContentMetadata() {
  ContentMetadata contentMetadata = new ContentMetadata(); 
  // implement the creation of the contentMetadata object
  return contentMetadata;
 }
 
 private RequestSettings getRequestSettings() {
  RequestSettings newRequestSettings = new RequestSettings();
  // implement the creation of the newRequestSettings object
  return newRequestSettings;
 }
 
...
}
```

## Start the Pulse Session

Now that you have created the Pulse Session, you start it to pass the Pulse Session Listener to the Pulse SDK, so it has the correct object to send events to. For example, in the Android Pulse SDK this is done with:

```
PulseSession.startSession(listener);
```

where the listener is the reference to the Pulse Session Listener.

A code example would be:

```
public class PulseManager implements PulseSessionListener {
 private PulseSession pulseSession;
 
...
 
 pulseSession = Pulse.createSession(getContentMetadata(), getRequestSettings());
 pulseSession.startSession(this);
 
...
 
}
```

## Implement Remaining Pulse Session Event Methods

You have implemented the listener to respond to events coming from the Pulse SDK. Now, you need to implement the remaining methods from the Pulse Session protocol \(iOS, tvOS\) or interface \(Android, HTML5\) to send information about content playback from the video player to the Pulse SDK. For example, in the Android Pulse sample integration, the session interface is also implemented in the [PulseManager.java](https://github.com/ooyala/pulse-sdk-android-2.x-sample/blob/master/app/src/main/java/com/ooyala/pulseplayer/PulseManager/PulseManager.java) class.

The methods that need to be reported, for example, for the Android Pulse SDK can be found here: [Interface PulseSession](http://pulse-sdks.ooyala.com/android_2/latest/com/ooyala/pulse/PulseSession.html).

## Handle the Pulse Video Ads

After an ad break has started, the Pulse SDK sends startAdPlayback events containing an ad and for each ad in the ad break. For example, in the Android Pulse SDK:

```
PulseSessionListener.startAdPlayback(ad, timeout);
```

**Select the correct media file**

Now, you need to select the correct media file to display from the ad. For example, in the Android Pulse sample integration:

```
@Override
public void startAdPlayback(PulseVideoAd pulseVideoAd, float timeout) {
 currentPulseVideoAd = pulseVideoAd;
 adPlaybackTimeout = (long) timeout;
 String adUri = selectAppropriateMediaFile(pulseVideoAd.getMediaFiles()).getURL().toString();

...


}
 
...
 
MediaFile selectAppropriateMediaFile(List<MediaFile> potentialMediaFiles) {
 MediaFile selected = null;
 int highestBitrate = 0;
 for (MediaFile file : potentialMediaFiles) {
  if (file.getBitRate() > highestBitrate) {
   highestBitrate = file.getBitRate();
   selected = file;
  }
 }
 return selected;
}
```

**Implement the ad event methods**

When you have the correct media file, start the ad playback and implement all methods from the Pulse Video Ad protocol \(iOS, tvOS\) or interface \(Android, HTML5\) to send information about ad playback from the video player to the Pulse SDK. For example, in the Android Pulse sample integration, the ad interface is also implemented in the [PulseManager.java](https://github.com/ooyala/pulse-sdk-android-2.x-sample/blob/master/app/src/main/java/com/ooyala/pulseplayer/PulseManager/PulseManager.java) class.

The methods that need to be reported, for example, for the Android Pulse SDK can be found here: [Interface PulseVideoAd](http://pulse-sdks.ooyala.com/android_2/latest/com/ooyala/pulse/PulseVideoAd.html).

## Handle the Pulse Pause Ads \(optional\)

Although handling pause events in the player in a way to get pause ads is optional, it is good practice to implement the following methods, so your integration is ready whenever you want to start serving pause ads from Pulse.

When the viewer pauses the video, you report contentPaused to PulseSession. If you have requested pause ads in your integration, the Pulse SDK sends showPauseAd events containing a pause ad. For example, in the Android Pulse SDK:

```
...

  PulseSession.contentPaused();

...

PulseSessionListener.showPauseAd(ad);
```

**Verify the supported resource file**

Now, you need to verify that your integration can access and display the provided ad. For example, in the Android Pulse sample integration you have to first verify if the provided pause ad type is supported by your integration, then you need to load the image from the URL:

```
@Override
public void showPauseAd(PulsePauseAd pulsePauseAd) {
  ...
  currentPulsePauseAd = pulsePauseAd;
  ...
  String pauseAdType = currentPulsePauseAd.getResourceType();

  if (pauseAdType.equals("image/jpeg")) {
    URL srcUrl = currentPulsePauseAd.getResourceUrl();
    if (srcUrl != null) {
      // Try to load the image from provided URL
      //pauseImageView is the container to show the image
      pauseImageView.loadImage(srcUrl);
    }
  }
}

...

public void loadImage(URL url) {
  new DownloadImageTask(imageView, this)
    .execute(url.toString());
}
```

**Implement the pause ad event methods**

When you have the correct source file, start displaying the ad and implement all methods from the Pulse Pause Ad protocol \(iOS, tvOS\) or interface \(Android, HTML5\) to send information about the ad from the video player to the Pulse SDK. For example, in the Android Pulse sample integration, the ad interface is also implemented in the [PulseManager.java](https://github.com/ooyala/pulse-sdk-android-2.x-sample/blob/master/app/src/main/java/com/ooyala/pulseplayer/PulseManager/PulseManager.java) class.

The methods that need to be reported, for example, for the Android Pulse SDK can be found here: [Interface PulsePauseAd](http://pulse-sdks.ooyala.com/android_2/latest/com/ooyala/pulse/PulsePauseAd.html).

## Implement Pulse Session Extension \(optional\)

If you want to request more linear ads or new pause ads, you need to extend the Pulse Session by implementing the extendSession method. In the same way when creating the session, you must pass in content metadata and request settings. The content metadata can be the same, but you must make sure that none of the settings in the content metadata interfere with requesting the desired additional ads. For example, if you added a tag called 'standard-preroll' that prevents requesting midrolls, then you must update the content metadata object without this tag if you want to request midrolls in the session extension. The request settings have to be updated with the positions where you want to show additional ads with the following limitations:

-   You cannot request insertion points that have been requested already. For example, if you have already requested post-roll ads, then you cannot request them again.
-   You can request additional mid-rolls, but only for cue points that have not been requested yet. For example, if you have already requested midrolls to show after 10 seconds and 30 seconds of video content playback, you can only request more midrolls for times that differ from 10 and 30 seconds.
-   You may request pause ads multiple times, but the selected pause ad is always the last one requested. This means that the pause ad insertion point is always overwritten with the latest result from the session extension.

The extendSession method also takes a callback function, or a PulseSessionExtensionListener in case of the Android Pulse SDK, to execute when the session extension was successful. For example, in the Android Pulse SDK:

```
pulseSession.extendSession(updatedContentMetadata, updatedRequestSettings, new PulseSessionExtensionListener() {
  @Override
  public void onComplete() {
    Log.i("Pulse Demo Player", "Session was successfully extended.");
  }
});
```

**Parent topic:**[Pulse SDKs](../../../oadtech/ad_serving/dg/pulse_sdks_intro.md)

