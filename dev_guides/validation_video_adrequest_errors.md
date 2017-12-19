# Video Ad Error Handling & Tracking

## Ad Response Only Contains "inventory" ==\> Track Inventory

As mentioned in the previous section, this part of the validation process is the one with the highest failing percentage. These are some edge cases that can easily be forgotten, but really have to be handled and tracked.

![Error Handling Checklist](../../image/video_ad_error_list.png)

This tutorial explains how to test your project to ensure proper reporting of errors regarding the inventory.

\[ooyala:VmeTU4djoqHhBBmCzBuDY34UPA56ms1Z\]



Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_inventory \> click OK.

![Charles Proxy Request Check](../../image/inventory_screen.png)

## 404 When Loading the Video Ad

This tutorial explains how to test and track an ad's 404 error.

\[ooyala:VkeTU4djqC\_pNe\_dl8XTAH2qzuuDKHOG\]



**Start content playback**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_404 \> click OK.

When you start the player, does the player correct error-handle the 404 issue and start the content?

**Track error**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_404 \> click OK.

You should see one "inventory" tracking HTTP request \(aid=0 & e=0\) per each available ad break. The example below has 2 available ads per break.

![Charles Proxy Sequence Check](../../image/sequence_menu.png)

**Alternate testing method:** If you have access to the source code of the integration, you can also achieve the same results by checking your request configuration directly in the implementation to the following:

-   host: 'vp-validation.videoplaza.tv'
-   category \(s\): 'validation'
-   tag \(t\): '404'

**For information about how to track errors please refer to the developer documentation. Also, in our DIY tutorials, there are special sections dedicated to error handling and tracking.**

## Timeout when Loading the Video Ad

This tutorial demonstrates how to test a timeout error.

\[ooyala:VoeTU4djq1uj-iGNKiOHYx37wLgWCpnI\]



**Start content playback**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_timeout \> click OK.

Start the player, does the player correct error-handle the timeout issue and start the content?

**Track error**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_timeout \> click OK.

You should see one "inventory"\(error\) tracking HTTP request \(aid=0 & e=0\) per each available ad break.

**Alternate testing method:** If you have access to the source code of the integration, you can also achieve the same results by checking your request configuration directly in the implementation to the following:

-   host: 'vp-validation.videoplaza.tv'
-   category \(s\): 'validation'
-   tag \(t\): 'timeout'

## Get an Unsupported Video Ad

This tutorial shows how to test the player's handling of an unsupported video ad.

\[ooyala:VqeTU4djpeo7dzFy8AX-kuB9qG057aGy\]



**Start content playback**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_invalid \> click OK.

Start the player, does the player correct error-handle the unsupported video ad and start the content?

**Track error**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_invalid \> click OK.

You should see one "inventory" tracking HTTP request \(aid=0 & e=0\) per each available ad break.

**Alternate testing method:** If you have access to the source code of the integration, you can also achieve the same results by checking your request configuration directly in the implementation to the following:

-   host: 'vp-validation.videoplaza.tv'
-   category \(s\): 'validation'
-   tag \(t\): 'invalid'

**Parent topic:**[Step by Step Validation Process](../../../oadtech/ad_serving/dg/validation_step_by_step.md)

