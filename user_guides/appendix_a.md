# Appendix A - Introduction to VAST

VAST \(Video Ad Serving Template\) is an XML standard ad container developed by the IAB.

A VAST compliant video player facilitates for publishers to plug in 3rd party ads from VAST compliant video ad networks and other ad sources.

```
<?xml version="1.0" encoding="UTF-8"?> 
<VideoAdServingTemplate xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="vast.xsd">

 ... 
 
</VideoAdServingTemplate>
```

VAST supports linear video ads \(such as pre-rolls\), non-linear video ads \(such as overlays\) and companion ads as defined in the IAB Digital Video Ad Format Guideline \(although the more common case is to use linear video ads\). It is also important to note that VAST does not specify the positioning or timing of the ads within a video player; it is left to the video player itself to determine this since the player is the entity that understands the context in which the ads appear.

Using Pulse, you can either use third party VAST ads in your campaigns, or you can do the opposite and broadcast your own ads as VAST ads to be played in a third party VAST compliant video player. Broadcasting VAST ads from Pulse currently works for standard pre-roll, mid-roll, and post-roll.

**Parent topic:**[Ooyala Pulse User Guide](../../../oadtech/ad_serving/ug/introduction.md)

