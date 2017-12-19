# Tracking

This is related to the tracking seen in the ad type category of the validation document \(Preroll/MidrollPostroll/\). If you are looking for the article on error tracking, please check [Video Ad Error Handling & Tracking](validation_video_adrequest_errors.md).

**Impression \(e=0\)**

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> click OK.

When **each** pre-roll ad start you should see a HTTP "tracker" request like below.

![Impression Tracker](../../image/impression_http_tracker.png)

**NOTICE: PARAM E=0 AND PARAM AID!=0 \(NOT EQUAL TO 0\).**

## Click-through \(e=20\)

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> click OK.

When you click on the pre-roll ad you should see a HTTP "tracker" request like below.

![Click Tracker](../../image/click_http_tracker.png)

## Quartiles \(e=14, e=15, e=16, e=17, e=18\)

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> click OK.

You should see all HTTP "tracker" requests \(e=14, e=15, e=16, e=17, e=18\) like below.

![Quartile Tracker](../../image/quartile_http_tracker.png)

## External Pixel Tracking \[none, one, several\]

Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> click OK.

You should see 3 test external pixel tracker events like below. If you can see only 1 test external pixel tracker add a comment "one".

![External Pixel Tracking](../../image/pixel_tracker.png)

**Parent topic:**[Validation Importance and Process](../../../oadtech/ad_serving/dg/validation_importance_process.md)

