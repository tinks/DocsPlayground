# \(Deprecated\) Brightcove Perform Plugin \(HTML5\)

How to integrate Ooyala Pulse ad delivery with the Brightcove player using the Brightcove Perform plugin.

In order to enhance the advertising capabilities of the plugin, Ooyala Ad Products offers a Flash extension, capable of displaying VPAID ads, premium formats and companion banners in environments that support Flash. Prerequisites for this guide are:

-   The Brigthtcove player is up and running on your site, and is in HTML5 mode.
-   You have a Ooyala Pulse account and a unique ID.
-   You have to add an optional parameter named 'flashEnabled': true to your default configuration.

## Setup Option 1 - Embedded Player

1.  Start by configuring your Brightcove player with your desired parameters.
2.  Add the plugin to the page.
3.  On page load, initialize the plugin and send the configuration.

```
<!--embeds the brightcove player-->
    <video width='640px' height='480px'
        data-account="3110396001"
        data-player="63ab8dc0-c43c-4d45-b5cd-d81457e37917"
        data-embed="default"
        data-video-id=""
        class="video-js" id="player" controls></video>
    <script src="//players.brightcove.net/3110396001/63ab8dc0-c43c-4d45-b5cd-d81457e37917_default/index.min.js"></script>
    
    
    <script src="http://cdn.videoplaza.tv/resources/html5/bc_perform/vp_plugin.js"></script>
    
    <script type="text/javascript">
        var vpConfig = {
        vpHost: 'http://vp-validation.videoplaza.tv',
        vpCategory: 'validation',
        tags: ['standard'],
        flags: ['optional', 'array'],
        cuepoints: [10, 30],
        optional: {
        flashEnabled: true
        },
        vpContentForm: 'shortForm'
        };
        videojs('player').vpbc(vpConfig);
    </script>
```

## Setup Option 2 - Player in iframe

1.  Add the plugin to the new Brightcove Video Cloud Studio \(studio.brightcove.com\).
2.  Add the plugin name - 'vpbc'.
3.  Add the plugin options in json format.

    ```
    {
    "vpHost": "http://vp-validation.videoplaza.tv",
    "cuepoints": [
    10,
    20
    ],
    "vpcontentform": "short_form",
    "vpcategory": "validation",
    "tags": [
    "standard"
    ],
    "optional": {
    "flashEnabled": true
    }
    }
    ```

4.  Copy the iframe url generated in Video Cloud and add it to the page where you want the video and advertising to be displayed.

**Note:** Due to iframe security limitations, when using the Brightcove Player in an iframe, Takeover and Companion Banner ads are not supported.

## Adding Metadata and Video Level

In addition to the configuration object that can be passed to the embedded/iframe player, you can pass video-specific metadata in the Brightcove Video Cloud console:

![Adding Metadata](../../image/adding_metadata.png)

The metadata will be available in the mediainfo object \(player.mediainfo\) that is generated after a video is loaded programatically.

**Parent topic:**[Archive](../../../oadtech/ad_serving/dg/ad_serving_toolkit_archive.md)

