# Use Category or Content Partner IDs Created in Ooyala Pulse

## How to enable in Flowplayer:

```
plugins: { 
    videoplaza: { 
        url: 'http://se-showroom.cdn.videoplaza.tv/resources/flash/flowplayer-3.2.6/latest/vp_plugin.swf',
        vpDomain:'http://se-showroom.videoplaza.tv',
        vpCategory: '<ID or alias>',
        vpContentPartner: '<ID or alias>'    
    },
}
```

## In JW 5.x:

flashvar vpCategory=<ID\>&vpContentPartner=<ID\>

## In Brightcove:

Either by object param value:

```
<param name="vpCategory" value="<ID>"/>
<param name="vpContentPartner" value="<ID>"/>
```

Or by setting in Brightcove player's player-level key/value pairs configuration:

`...;vpCategory=<ID>;vpContentPartner=<ID>...`

## In OSMF players:

flashvar vpCategory=<ID\>&vpContentPartner=<ID\>

## In custom players:

```
...
itemInfo.duration = ...
itemInfo.tags = ...
itemInfo.category = '<ID>';
itemInfo.contentPartner = '<ID>';
...
adPlayer.setNewItem(itemInfo);
...
```

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

