# JW6 Integration Customization

## Tags

To be able to target the ads to different keywords in Ooyala Pulse Campaign Manager, the ad player must be informed about these keywords. It can be done in two ways, either separate from each other or combined together:

1.  "vpTags" flashvar: `vpTags: "tag1,tag2,tag3,tag4"`
2.  XML Config file:

    ```
    <plugins>http://cdn.videoplaza.tv/resources/flash/jw6/latest/vp_plugin.swf
    </plugins> <vp_plugin.vphost>http://vp-validation.videoplaza.tv</vp_plugin.vphost>
    <vp_plugin.vpcategory>validation</vp_plugin.vpcategory>
    <vp_plugin.vptags>standard</vp_plugin.vptags>
    <vp_plugin.cuePoints>10,15</vp_plugin.cuePoints>
    ```


Tags added to the "vpTags" flashvar will act as global tags for this player/session and should only be used for static keywords or players without playlists.

Tags added to an item in the playlist xml will act as local tags for that particular item.

For example, setting "mysite.com,sport" in the vpTags flashvar and "football,finals" on playlist item \#1, will let Ooyala Pulse know that this content has the tags: mysite.com, sport, football, and finals.

## Mid-roll breaks

Mid-roll breaks are defined by either adding cue points to the media file's metadata, or by specifying them in as flashvars. For example, to trigger mid-roll breaks at seconds 30, 60 and 120 seconds: `cuePoints: '30,60,120'`.

## Additional Configuration Parameters

Consult the [Flashvars](integration_flashvars_configuration_variables.md) article for additional configuration parameters.

## Using other JW Player plugins

Please be advised that the use of other plugins in combination with the Ooyala plugin is made at your own risk. We do not test our plugin against other JW Player plugins, so there is always a chance that things like visual elements or events listeners could interfere with the user experience.

Always test your player and plugins before putting them into production, and don't hesitate to contact us if you are unsure whether a given combination of plugins will work correctly or not.

## Example customization

```
<script type="text/javascript">
        jwplayer("mediaplayer").setup({
        primary: 'flash',
        height: 270,
        width: 480,
        controlbar: 'over',
        file: "http://cdn.videoplaza.tv/resources/media/more_like_trees_640x360.mp4",
        image: 'http://demo.videoplaza.com/plugins/resources/jw/moreLikeTrees.jpg',
        plugins:{
        'http://cdn.videoplaza.tv/resources/flash/jw6/latest/vp_plugin.swf':
        {
          vphost: 'http://vp-validation.videoplaza.tv',
          cuepoints: '10,20',
          vptags: 'standard',
          vpcategory: 'validation'
        }
      }
    });
</script>
```

**Parent topic:**[JW6 Flash Plugin](../../../oadtech/ad_serving/dg/plugin_jw6_flash.md)

