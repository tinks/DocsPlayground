# Flowplayer Flash Plugin

How to integrate Ooyala Pulse ad delivery with the Flowplayer version 3.2.6 - 3.2.\* using the Flowplayer Flash plugin.

It assumes that you have Flowplayer up and running on your site, as well as an Ooyala Pulse account and a unique ID.

**Note:** If you are using an earlier version of the Flowplayer \(<=3.2.5\), please contact your Ooyala Technical Account Manager.

**Note:** Flowplayer does not currently support timeout or 404 not found error handling of plugins.

1.  Modifty your player configuration to include the plugin, and to include "tags" keywords and Ooyala "flags" on the items:

    ```
    flowplayer("player", "flowplayer-3.2.16.swf", {
        playlist: [{
        url: "http://url1.flv",
        tags: ["tag1", "tag2"] 
        },{
        url: "http://url2.flv",
        tags: ["tag1", "tag3"]
        }],
        plugins: {
        videoplaza: { 
        url: 'http://cdn.videoplaza.tv/resources/flash/flowplayer-3.2.6/latest/vp_plugin.swf',
        vpHost:'http://se-showroom.videoplaza.tv',
        vpCategory: ["category1"]
        }
        }
        });
    ```

    Important: If you are using Flowplayer 3.2.17 or Flowplayer 3.2.18, you need to host the plugin on the same domain as the Flowplayer swf-file. In that case you are responsible for having the latest version on your CDN.

2.  Set the "vpHost" flashvar to your unique Ooyala sub domain. Try it out with this test ID first, which will always serve ads:`http://se-showroom.videoplaza.tv` You should now be getting ads from your Ooyala Pulse account.

For more information on customization, see:

-   **[Flowplayer Integration Customization](../../../oadtech/ad_serving/dg/plugin_flowplayer_customization.md)**  


**Parent topic:**[Plugins](../../../oadtech/ad_serving/dg/plugin_adtech_introduction.md)

