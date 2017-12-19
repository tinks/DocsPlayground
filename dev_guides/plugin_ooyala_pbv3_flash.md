# Ooyala Flash Plugin for Ooyala Player V3

How to integrate Ooyala Pulse ad delivery with Ooyala Player V3 using the Ooyala Pulse Flash plugin.

In your Ooyala Backlot account, you need to have the Videoplaza ad source enabled.

Enable Ooyala Flash OPF \(Open Platform Framework\) Module.

1.  Set up your Ooyala Backlot Account.
    1.  In Ooyala Backlot, select the top-level MONETIZE tab.
    2.  Add a new Ad Set and select:
        -   **Ad Source:** Videoplaza
        -   **vpDomain:** http://\{client-id\}.videoplaza.tv
        -   **Player level mid-roll ad breaks:** comma separated values in seconds \(no spaces\)
        -   **Player level tags:** comma separated list \(no spaces\)
        -   **Player level Ooyala flags:** for example, noprerolls \(not required\)
        -   **Player level shares:** Ooyala Pulse Category and/or Content Partner alias
        -   **Short form content max. length:** single value in seconds
    3.  In the top-level MANAGE tab, select the content item you would like to monetize.
    4.  Select the content-level Monetize tab and select Ad Set: \{name of your Ooyala ad set\}.
    5.  Select the content-level Embed tab and export your embed code.
2.  Set up your Ooyala video player.
    1.  Add any additional Ooyala Ad Products plugin configurations, which should be set when the content is loaded, to your Ooyala player embed code:

        ```
        <script>
          OO.ready(function() {
            OO.Player.create('ooyalaplayer', 'xxxxxxxxxxxx', {
              autoplay : false,
              width : 567,
              height : 320,
              // ******* START Ad Products PLUGIN CONFIG *********
              'videoplaza-ads-manager' : {
                vphost: 'http://{client-id}.videoplaza.tv',
                vptags: 'keyword1,keyword2',
                vpcategory: 'news',
                cuepoints : '30'
              }
              // ****** END Ad Products PLUGIN CONFIG **********
            });
          });
        </script>
        ```


**Parent topic:**[Plugins](../../../oadtech/ad_serving/dg/plugin_adtech_introduction.md)

