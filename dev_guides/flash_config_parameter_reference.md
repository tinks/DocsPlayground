# Flash SDK Configuration and Parameter Reference

## VideoplazaLoader Configuration

Required configuration parameters for the Flash Ad Player.

## vpHost

When the ad requesting module is initialised, the vpHost for the Ooyala Pulse account must be provided. This is used to identify the Ooyala Pulse account to request ads from. The vpHost is derived from the "sub-domain" found in the Ooyala Pulse UI and is formated like this: `http://[sub-domain].videoplaza.tv`

Previously known as vpDomain or vpid.

## Ooyala Ad Player Configuration

Optional configuration parameters to customise the Flash Ad Player.

-   flashVars : Object
-   language : String
-   adPlayerSkin : DisplayObject
-   allowDomains : Array
-   width : Number
-   height : Number
-   x : Number
-   y : Number
-   timeObject : Object
-   proceedAutomaticallyOnNewClip : Boolean

## Content Item Metadata \(ItemInfo\)

Content specific metadata values define the specific video content's rules, targeting options and metadata.

|category|The category is a string that is used to associate content with a category that has been defined for the client's account in the Ooyala Pulse UI. This value of the category can be the Ooyala Pulse native ID of the category found in the Ooyala Pulse UI or a human readable "alias" that has been associated with the category in the Ooyala Pulse UI. Categories are used for reporting and targeting purposes in Ooyala Pulse UI. It is also possible to apply individual ad policies to each category, controlling how many and what type of ads are returned. **Note:** A content session can only request ads from one category at the same time.

Previously known as shares.

|
|contentPartner|The content partner is used to add an additional reporting dimension to the ads that are displayed. The content partner value can use the Ooyala Pulse native ID of the content partner found in the Ooyala Pulse UI or a human readable "alias" that has been associated with the content partner in the Ooyala Pulse UI. Previously known as shares.

|
|contentForm|A piece of video content can be defined as either long form or short form content. Long form content can be entire episode of a program, a full feature movie or just a piece of content that is more than 10 minutes long. It is up to the client to define where the line goes between short and long form. In Ooyala Pulse UI it is possible to configure individual ad policies for long and short form adding an additional ad policy dimension to a category.|
|contentId|Content id is used for forwarding the id of the main content to 3rd party trackers. This value is not used or tracked by Ooyala Pulse but can be added to request urls for 3rd party ad requests or additional tracking url via a macro in the Ooyala Pulse UI.|
|duration|This is the total duration of the main content in seconds.|
|cuepoints|A cue point represents a point in time on the content time line. Cue points are required when `insertionPointTypes` contains `InsertionPointType.ON_CUE_POINT`**Note:** The cuePoints array should contain objects with name and time properties. Linear ads like standard spots will be inserted at cue points name : `"vpLinear"`, Nonlinear ads like overlays will start at cue points name : `"vpNonlinear"`

Example:

```
RequestSettings.cuePoints = [{name:"vpLinear", time:65}, {name:"vpLinear", time:320}, {name:"vpNonlinear", time:120}];
```

|
|tags|Tags are freeform keywords that can be used for targeting and reporting purposes. Although the tags keywords are able to handle UTF-8 characters, we recommend to refrain from using special characters like quotes \(`‘` and `"`\) ampersand \(`&`\) comma \(`,`\) semi-colon \(`;`\).|
|flags \(com.videoplaza.api.utils.VpFlag\)|The flags are used to apply special rules and condition to an ad request. For example, some piece of premium content has been sponsored and no pre-rolls should be displayed. Adding the flag "noprerolls" will prevent pre-rolls from being returned but mid-rolls and post-rolls will be available as normal. Supported flags are:

-   `nocom`: No ads are returned at all
-   `noprerolls`: No pre-rolls are returned
-   `nomidrolls`: No mid-rolls are returned
-   `nopostrolls`: No post-rolls are returned
-   `nooverlays`: No overlays are returned

|

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

