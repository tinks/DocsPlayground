# Flashvars Supported by the Ad Plugins

|Name|Description|Example|
|----|-----------|-------|
|vpDomain / vpHost|Overrides the account ID.|Flashvar example:

```
vpDomain="http://xx-comapanyName.videoplaza.tv";
```

|
|vpTags|Keywords describing content, separate by commas.|Flashvar example:

```
vpTags="football,World Cup";
```

|
|vpFlags|Pre-defined flags|Flashvar example:

```
vpFlags="nocom"; //no commercials
```

|
|vpShares \[DEPRECATED\]|Replaced by vpCategory and vpContentPartner.| |
|vpCategory|UUID or alias of Category share|Flashvar example:

```
vpCategory="sports_mobile";
```

|
|vpContentPartner|UUID or alias of Content Partner share|Flashvar example:

```
vpContentPartner="MyPartnerName";
```

|
|vpContentForm|Informs the ad player if the video content is type short\_form or long\_form.|Flashvar example:

```
vpContentForm="short_form";
```

|
|adPlayerName|Lets you target a specific plugin version.|Flashvar example:

```
adPlayerName="as3_vp_player_2.0.0";
```

|
|closeButtonTimeout \[DEPRECATED\]|Only for Spots and Interactive Spots. Number of seconds before the close button shows up.| |
|fontURL|Overrides the font file URL.|Flashvar example:

```
fontURL="http://this.url/font.swf";
```

|
|language|Overrides the language used in the plugin.

Supported language tags in Flash:

-   de\_DE \(German\)
-   dk\_DK \(Danish\)
-   en\_UK \(UK English\)
-   en\_US \(US English\)
-   fr\_FR \(French\)
-   no\_NO \(Norweigan\)
-   es\_ES \(Spanish\)
-   sv\_SE \(Swedish\)
-   fi\_FI \(Finnish\)
-   tr\_TR \(Turkish\)
-   pl\_PL \(Polish\)
-   it\_IT \(Italian\)
-   nl\_NL \(Dutch\)
-   pt\_PT \(Portuguese\)
-   th\_TH \(Thai. NOTE: Requires custom font file!\)

|Flashvar example:

```
language="de_DE";
```

|
|showCountdownText|Set to false to hide the countdown text in Spots and Interactive Spots.|Flashvar example:

```
showCountDownText=false;
```

|
|skinURL|Overrides the skin file URL.|Example:

```
skinURL="http://this.url/skin.swf";
```

|
|vpCloseButtonOverride \[DEPRECATED\]|Overrides the behavior of the close button \(skip button in the Ooyala Ad Player and ms/mandatory strategy in the ticket\) for a specific ad format.| |
|vpEnvironmentURL|Overrides the environment URL. It is normaly downloaded from the same destination as the Bootloader.|Flashvar example:

```
vpEnvironmentURL="http://this.url/environment.xml";
```

|
|vpHideSpotCurtainOnPause|If "false", the curtain will show up when pausing the video.|Flashvar example:

```
vpHideSpotCurtainOnPause=false;
```

|
|vpHideCloseButtonIfAdIsLessThan|Always hides the close button for spot ads that have a duration shorter than this value.|Flashvar example:

```
vpHideCloseButtonIfAdIsLessThan=5;
```

|
|vpSpotAutoCloseAfterStep2|-   false \(default\) - The ad is not closed automatically on step 2 \(when the user has started the ad by clicking its curtain\).
-   true - The ad is closed automatically on step 2.

|Flashvar example:

```
vpSpotAutoCloseAfterStep2=true
```

|
|vpSelectorSpotTimeout|Override the selector spot countdown time \(in number of seconds\).|Flashvar example:

```
vpSelectorSpotTimeout=13;
```

|
|vpSelectorSpotPositions|Tells the distributor to limit the number of selector ads it returns \(2-6\).|Flashvar example:

```
vpSelectorSpotPositions=4;
```

|
|vpSpotClickThruMode|-   0 \(default\) - Standard mode, strongly recommended.
-   1 - Ad pauses and continues when user comes back, automatically closes when finished. Controls are not visible. Is not muted.
-   2 - on click, ad pauses, when user comes back ad is still paused and play button displayed, user must click to continue.

|Flashvar example:

```
vpSpotClickThruMode=2;
```

|
|vpUseMultiTriggerableCuePoints \[DEPRECATED\]|If set to "true" spots can be triggered multiple times \(they will be triggered each time the player hits that mark, impressions will also be tracked each time\).| |
|vpPrerollSlotSize|Pre-roll slot size|Flashvar example:

```
vpPrerollSlotSize=2;
```

|
|vpMidrollSlotSize|Mid-roll slot size|Flashvar example:

```
vpMidrollSlotSize=2;
```

|
|vpPostrollSlotSize|Post-roll slot size|Flashvar example:

```
vpPostrollSlotSize=2;
```

|
|vpNumberOfOverlays|Overlay Positions - number of overlays in the session|Flashvar example:

```
vpNumberOfOverlays=5;
```

|

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

