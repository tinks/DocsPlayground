# Pre-rolls, Mid-rolls, Post-rolls and Other Ad Types

This tutorial explains how to use the ad template when testing your ads in a player.

\[ooyala:h0dTU4djrnyU5MJwti3DcpV8Ch8F41CS\]



![Preroll Checklist](../../image/preroll_template.png)

## This Ad Format has been Implemented in the Client Player

Has this specific ad format \(pre, mid or post-roll\) been implemented and can it be tested?

## The Ad is Visible During Playback

Are you able to see pre-roll ads? If there are no ads current available you can use the validation account below.

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> press OK.

## Click-Through is Working \(Open a New Browser Window\)

When the pre-roll starts, click on the ad. Does it open a new browser window or webview? If there are no ads currently available you can use the validation account below.

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> press OK.

## Ad Request URI

Paste the "distributor" HTTP request URI, example: http://xx-clientName.videoplaza.tv/proxy/distributor/v2?rt=vast\_2.0&t=standard&s=validation&tt=p

A script will run and the params field will be filled for you. Make sure that all the required \(indicated by the red dot\) fields are populated. If they are not, you might have an integration problem. Refer to the Parameters appendix in case of issues or for having more info.

![Parameter Checklist](../../image/params_list.png)

**Parent topic:**[Step by Step Validation Process](../../../oadtech/ad_serving/dg/validation_step_by_step.md)

