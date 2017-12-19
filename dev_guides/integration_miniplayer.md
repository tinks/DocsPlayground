# Miniplayer Integration Guide

## Introduction

The Miniplayer is a lightweight integration of Ooyala's Flash Ad Player for environments that want to load pre-rolls before any type of content, such as gaming sites or image galleries.

The Miniplayer is configurable using Javascript, and it will load the Ooyala Flash Ad Player inside a lightweight video player, thus eliminating the time and bandwidth required to load an traditional video player, such as Flowplayer or Brightcove. After playing the pre-roll ad break, the Miniplayer will unload itself, thus allowing the main content to be shown.

This approach is particularly useful if each content item is a unique Flash instance with no common underlying Flash platform or framework.

## Configuration

**Flash Plugin URL**

`var miniplayerURL="http://cdn.videoplaza.tv/resources/flash/miniplayer/latest/miniplayer.swf"`

**Configuration String**

A string of key/value pairs separated by the "&" symbol. Any relevant flashvar can be added here:

-   vpHost
-   vpTags
-   vpCategory
-   vpContentPartner
-   vpContentId
-   [showCountdownText, and so on.](integration_flashvars_configuration_variables.md)

`var queryString = "vpHost=http://{subdomain}.videoplaza.tv&vpTags=tag1,tag2&vpCategory=myContentCategory&vpFlags=nomidrolls,nopostrolls,nooverlays,noskins";`

**Ad complete event**

When the pre-roll ad break is complete \(or if the Ad Player fails to load\), the following Javascript event will be triggered.

`vpMiniPlayer.prerollDone()`

## Example

In the example below, the pre-rollDone\(\) function calls the Javascript function "close\_div\_promotion", which simply closes the div containing the Ooyala Miniplayer, and revealing the publisher content hidden behind it. However, the show/hide behavior can be implemented however is best suited to your site.

[Miniplayer example](http://demo.videoplaza.com/vp-miniplayer-Ptb5SC4G/)

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

