# Appendix B - Creative Asset Specification

## Ad Formats - The Format Family

There are four main categories of ad formats available in Ooyala Pulse, which comprise the Format Family:

-   **Standard Formats**: include pre-rolls, mid-rolls, post-rolls, seek-rolls and overlays in different variations. These can be static or contain interactive elements. They can be booked as sponsor bumpers and with combined display elements like companion banners outside the video player. These formats are the obvious choice for long form content and are available on all devices.
-   **Premium Formats**: create an interactive and engaging experience for the viewer. **Takeover** is a traditional linear ad, which takes over the full screen when the ad is showing. **Ad Selector** allows a viewer the option to select which advert they want to watch, with a range of 2-6 different adverts to choose from. **Pause ads** start playing when the viewer pauses video content. These formats can generate a higher yield and provide a premium position for the advertiser.
-   **Format Partners**: Ooyala has partnerships with a range of best of breed format partners and ad format specialists such as **Innovid**, **InSkin** and **Brainient**. The Ooyala platform is compliant with the leading video industry standards - VAST and VPAID, ensuring we can deliver interoperability between different ad serving technologies and video players.

    **Note:** The Partner ad formats require an additional contract between the publisher and each partner.

-   **Custom Formats**: a service enabling publishers to offer and serve unique ad formats without impacting their high priority internal development projects. We can work with you to build custom formats specific to your needs.

## Spot Ads: Pre-rolls, Mid-rolls, Post-rolls and Seek-rolls

Spots can be **standard** or **interactive**. The standard format only supports clickthrough to an URL. Interactive spot ads offer more functionality adopted for the Interactive TV; a roll-­up reminder bar is displayed after the ad has ended, and video starts playing. The viewer can click on the bar to bring back either the same advertising message or a new, follow-­up message. If there are multiple interactive ads in an ad break, the user may flip between the reminder bars to engage any interactive spot ad.

| |Video file|Click through URL|3rd Party Impression tracking URL|Reminder bar|Follow up video|Companion banner support|
|--|----------|-----------------|---------------------------------|------------|---------------|------------------------|
|**Standard**|Video file\*|Yes|Yes|No|No|Yes|
|**Interactive**|Video file\*|Yes|Yes|Yes|Video file\*|Yes|

\*The video file you use should follow the recommendations in the **Video file specifications** section below.

**Reminder Bar**

The reminder bar is displayed after an interactive video ad has ended, and video starts playing. It is visible for a few seconds and then slides up in the video player header, where the user may reach it by hovering the mouse pointer. Reminder bars are currently only supported in Flash based video players.

|Flash banner|Required dimensions|Maximum weight|
|------------|-------------------|--------------|
|.swf|505x40 px|50kb|

## Video File Specifications

If the Asset Factory functionality is activated for your account, you can upload almost any video file to Pulse and we use it to generate new video assets that work on any device you wish to target. You should try uploading a high-­resolution file with no or little compression, as the quality of the generated assets depends on the quality of the file you upload.

If you are uploading each video file manually, the specifications for video files depend on which devices you want to target. Make sure these specifications meet the [IAB standards](http://www.iab.com/guidelines/digital-video-ad-format-guidelines-best-practices/).

**General Recommendations for Automated Transcoding**

|Quality|Container format|Video codec|Audio codec|Minimum bitrate|Resolution width|Resolution height|
|-------|----------------|-----------|-----------|---------------|----------------|-----------------|
|HD|MP4|H264|AAC|5000kbs|1280|720|
|SD|MP4|H264|AAC|2000kbs|1280|720|

**Note:** These are recommendations only. Ooyala supports a wide range of source file configurations.

**Requirements for Pre-transcoded Files**

|High resolution file\(for broadband connections\)

|Low resolution file\(for limited Internet connections and mobile Internet access\)

|Recommended Audio|Recommended Aspect ratio|
|---------------------------------------------------|------------------------------------------------------------------------------------|-----------------|------------------------|
|700kbs|400kbs|Encoded at volume less than or equal to -12db|Check the size of the video player, or conform to the international standards: -   **4:3** \(512 x 384 pixels, 640 x 480 pixels, 1024 x 768 pixels\)
-   **16:9** \(512 x 288 pixels, 640 x 360 pixels, 1280 x 720 pixels\)

|

## Companion Banner

-   Supply a 3rd party ad code snippet or upload a Banner file \(SWF, JPG, GIF, PNG\)
-   Clickthrough URL
-   Follow the standard display banner sizes specified by [IAB](http://www.iab.com/guidelines/iab-display-advertising-guidelines/)
-   A predefined area <DIV\> on your site to host the ad

**Note:** The companion areas you created need to be registered with your Pulse account in order to traffic ads to them. Contact you Account Manager for more information.

## Overlay

|Flash banner|Required dimensions|Maximum weight|
|------------|-------------------|--------------|
|.png .jpg .swf|400x50 pxBe sure to mask the area around the banner.

|30kb|

You may not have streaming video in the overlay.

**Options**

-   Clickthrough URL
-   Video: see "Video file specification" above
-   Splash ad \(.swf\)
-   Slide show JPEG images

## Premium Formats

**Takeover**

A takeover has the same specifications as any spot ad.

**Ad Selector**

To create an Ad Selector campaign you need to create one goal for every ad that you want the user to be able to choose from. In each goal you create one ad that has the format "Ad selector". The Ad Selector ad is composed of:

-   one thumbnail, recommended size **138x105**,
-   one video file for the ad, that meets the recommendations in the "Video file specification" above,
-   and one destination URL.

**Pause Ad**

Pause ads are non-linear banner ads that are displayed within the video area when the user presses pause or otherwise intentionally pauses the content. This way they get maximum attention by the viewer.

|Flash banner|Required dimensions|Maximum weight|
|------------|-------------------|--------------|
|.swf \(recommended\) .png .jpg .gif|Same as video player|100kb|

-   A close button always appears in the top right corner.
-   You may not have streaming video in the banner.

**Options**

-   Clickthrough URL

## Partner Ad Formats

**Inskin**

InSkin™ is an interactive ad format that wraps around video and games. The InSkin™ ad is displayed after any pre-rolls have been shown and the video content starts. The InSkin™ remains wrapped around the player throughout the duration of the clip to ensure maximum brand recognition. A second step of the InSkin™ ad is triggered when the wrap area is clicked. The second step of the ad could either take the viewer to the destination page of the advertiser, or present an in-­page advertiser mini site that loads from InSkin servers.

-   The InSkin ad creative is built by InSkin Media.
-   Client approves flat designs in PSD file along with required graphical assets.
-   Contact the publisher offering InSkin ads or Ooyala for a detailed InSkin creative specification.

More information can be found at [Inskin Media](http://www.inskinmedia.com/).

**Brainient**

Brainient mainly have two products. The first one is BrainAds, which is a personalised video retargeting platform able to serve individual ads to people who visited the advertiser's site before. The second one is BrainRolls, simply interactive pre-rolls with tons of engaging features.

-   Contact Brainient on a complete specification of the format. Ooyala serves the ad as a 3rd party ad from Brainient through the VAST standard. Please supply an appropriate VAST URL.
-   More info at: [Brainient](http://brainient.com/en/).

**Innovid**

Innovid’s flagship is the iRoll, which is essentially a pre-roll that introduces interactive elements, such as clickable areas on the ad which can take users to specific promotions, interactive presentations, other ads, and so on. Innovid also offers a range of iRoll apps, which make the iRoll fully social by utilizing: Twitter follow, YouTube sharing, coupon downloads, store locator, ticket purchase and many other features, all with the click of a button.

-   Contact Innovid on a complete specification of the format. Ooyala serves the ad as a 3rd party ad from Innovid through the VAST standard. Please supply an appropriate VAST URL.
-   More info at: [Innovid](http://www.innovid.com/#transform-your-video-experience).

**Parent topic:**[Ooyala Pulse User Guide](../../../oadtech/ad_serving/ug/introduction.md)

