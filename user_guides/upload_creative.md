# Upload Creative

This section covers the second part of adding a new ad. It applies to specific ad formats. For more information on uploading ad assets, refer to [Uploading Ad Assets Manually or Automatically](uploading_ad_assets.md) and make sure to check [Appendix B - Creative Asset Specification](appendix_b.md).

There are two types of ads you can use for your goals in Pulse. Either ads uploaded directly in Pulse, or 3rd party ads coming from an external provider. Examples of 3rd party ad sources include ad networks, another ad server, or SSP services like Pulse and Pulse SSP.

## Standard Spot Ad

![Upload Standard Spot Ad page](../../image/pulse_campaigns_add_standard_spot_ad.png)

1.  If you have one source file, choose one of the following options and go to step 3, otherwise continue to the next step:
    1.  Select from asset factory.
    2.  Upload file: all other assets you need, for all devices, services and bandwidths you want to support, are automatically generated.
    3.  Fetch from URL.
2.  Upload pre-transcoded files manually:
    1.  Click on **upload pre-transcoded video files**.
    2.  Supply file assets specified for each row in the **Expected files** table. Standard spot ads require one high‐resolution file and one low‐resolution file for each device. Upload the file or fetch it from URL.
3.  **Destination URL** \(optional\): add a URL triggered when the ad is clicked.
4.  **External Tracking** \(optional\): if you have a 3rd party tracking service to track your ad impressions, you can enter the URL for that service here. For more information on external tracking, refer to [Global Tracking](settings.md#global_tracking).
5.  Click **SAVE**.

## Overlay

The Overlay comes in standard and interactive format. The standard overlay only supports click through to a destination URL, where the interactive overlay supports a wider selection of click events as described below.

![Upload Overlay page](../../image/pulse_campaigns_add_overlay_ad.png)

1.  **Banner file**: the overlay requires one image file that appears as an overlay banner in the video. The supported file formats are SWF, PNG and JPG.
2.  **Link text** \(optional\): insert the clickable text that provides a link to the destination page.
3.  **Video** \(optional\): trigger a video just like a standard spot ad. Upload the video file to be used.
4.  **Imageset** \(optional\): launch a mini slideshow of uploaded JPEG images in the video player, for the user to browse.
5.  **Splash** \(optional\): show graphical banner covering the video player.
6.  **Destination URL**: add a URL to be triggered when the ad is clicked.
7.  **External Tracking** \(optional\): if you have a 3rd party tracking service to track your ad impressions, you can enter the URL for that service here. For more information on external tracking, refer to [Global Tracking](settings.md#global_tracking).
8.  Click **SAVE**.

**Note:** You can control the behaviour of your overlay ads using the insertion policy settings for your categories. For more information, refer to [Ad Insertion Policies](ad_insertion_policies.md).

## Companion Banner

![Upload Companion Banner page](../../image/pulse_campaigns_add_companion_banner_ad.png)

1.  **Zone**: choose a zone for your companion banner. Pulse helps you to register a number of locations on your site where companion banners should be shown.
2.  **Banner file**:
    1.  **Flash**: upload a file in SWF format. Make sure it has the same width and height as the zone on your website.
    2.  **Image**: upload a file in JPG, GIF or PNG format. Make sure it has the same width and height as the zone on your website.
3.  **Code template**: modify the ad template code or leave it as it is. The template is the code that is injected into your website's zone and it triggers the companion banner ad. Dynamic data, like the actual image file or click through URL is indicated with curly brackets. If you are pulling the ad from a **3rd party**, configure a 3rd party ad tag.
4.  **Destination URL**: add a URL to be triggered when the ad is clicked.
5.  **External Tracking** \(optional\): if you have a 3rd party tracking service to track your ad impressions, you can enter the URL for that service here. For more information on external tracking, refer to [Global Tracking](settings.md#global_tracking).
6.  Click **SAVE**.

## 3rd Party Ad

![Upload 3rd Party Ad page](../../image/pulse_campaigns_add_3rd_party_ad.png)

1.  Click the **Add new ad button** and select the desired standard spot ad from the ad format list.
2.  Click on the **3rd Party Ad** tab.
3.  **3rd party Ad URL \(VAST\)**: add a URL to a VAST ad served by an external system. Pulse supports the VAST industry standard for serving video ads. The URL leads to an XML response that contains all information about which video files to play and what tracking is available.

    **Note:** Ensure that the 3rd party URL that you book is VAST compatible in order to work well in all Ooyala integrations.

4.  **Use strict VPAID mode** \(optional\): enabled by default. VPAID is a complementary standard to the VAST standard, which describes the additional behaviour of the ad. The strict mode of VPAID is a stability feature, which means that, even if it contains errors, the VPAID ad cannot break the other ads playing in the break.
5.  **Display countdown** \(optional\): select this box if you want the countdown text visible on the 3rd party ad. Disabled by default to avoid the risk of VPAID ads having their own countdown covering the standard Ooyala countdown that is always shown on ads.
6.  **Estimated ad duration** \(optional\): if you are using time based breaks, you have to estimate the duration of the 3rd party ad. If the ad does not have an estimated duration, or exceeds the time based break duration, it will not get selected. Check the box and enter the estimated duration of the ad in seconds.

    **Note:** Contact your Account Manager to use time based breaks. This feature needs to be enabled in the backoffice.

7.  **External Tracking** \(optional\): if you have a 3rd party tracking service to track your ad impressions, you can enter the URL for that service here. For more information on external tracking, refer to [Global Tracking](settings.md#global_tracking).
8.  Click **SAVE**.

Read more on VAST in [Appendix A - Introduction to VAST](appendix_a.md).

**Parent topic:**[Create a Campaign](../../../oadtech/ad_serving/ug/create_a_campaign.md)

