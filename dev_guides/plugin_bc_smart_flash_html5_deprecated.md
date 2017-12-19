# \(Deprecated\) Brightcove SMART Plugin \(Flash+HTML5\)

How to integrate Ooyala Pulse ad delivery with the Brightcove SMART player using the Brightcove SMART plugin.

-   Before proceeding, we strongly recommend that you read in full the Brightcove article [Delivering Advertising with HTML5](http://support.brightcove.com/en/video-cloud/docs/delivering-advertising-html5).
-   You have a Brightcove account with a player up and running on your site.
-   You have an Ooyala Pulse account and a unique ID.

1.  Enable HTML5 advertising.
    1.  Go to Brightcove Videocloud \> Account Settings \> HTML5 Advertising.![Enable HTML5](../../image/enable_html5.jpg)
2.  Setup the Flash plugin and configuration.
    1.  Select Advertising Tab \> Select a player and click Edit.
    2.  Select "Videoplaza Ad Player" from the Ad Source drop-down menu.
    3.  Add the plugin config as Player-Level Key/Value Pairs separated by ";".

        For example: vpHost=http://\{your-unique-subdomain\}.videoplaza.tv;

        ![Setup Flash Plugin](../../image/setup_vp_flash_plugin.png)

3.  Enable HTML5 Delivery.
    1.  Select Publishing Tab \> Select the same player and click Settings \> Select Global Settings.
    2.  Enable all Web Settings.![Enable the Web Settings](../../image/highlight_enabling.png)
4.  Setup Ooyala HTML5 Plugin.

    1.  Select Publishing Tab \> Select the same player and click Settings \> Select Plug-ins Settings.
    2.  Add the URL to the Ooyala HTML5 SMART plugin \(make sure it ends with "`?blocking=true`"\).`http://cdn.videoplaza.tv/resources/html5/brightcove/latest/vp_plugin.js?blocking=true`
    3.  Save Changes.![Save the Changes](../../image/save_changes.png)
    **Note:** It may take up to 10 minutes before Brightcove's CDN propagates all changes.


For more information on customizing your ad player, targeting your ads, adding cue points and Java support see:

-   **[Customizing the AdPlayer](../../../oadtech/ad_serving/dg/plugin_bc_smart_customizing_adplayer_deprecated.md)**  

-   **[Ad Targeting](../../../oadtech/ad_serving/dg/plugin_bc_smart_targeting_deprecated.md)**  

-   **[Add Cue Points](../../../oadtech/ad_serving/dg/plugin_bc_smart_add_cuepoint_deprecated.md)**  

-   **[JavaScript Support](../../../oadtech/ad_serving/dg/plugin_bc_smart_java_support_deprecated.md)**  


**Parent topic:**[Archive](../../../oadtech/ad_serving/dg/ad_serving_toolkit_archive.md)

