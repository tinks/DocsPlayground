# Companion Banner

The companion banner is visible during playback.

**Note:** This test is only required if the client is using companion banners.

Are you able to see companion banners during the ad playback? If there is no companion banners current available you can use the validation account.

1.  Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> click OK.
2.  Create or rename your companion banner <div\> id to "companionMpu" like below
3.  Start the player, when the pre-roll starts you should see the companion banner image

```
<!DOCTYPE html>
<html>
<head>
</head>
<body>
    <!-- Your player code here -->

    <div id='companionMpu' style='width:300px, height:250px'>companion banner</div>
</body>
```

**Click-through is working \(open a new browser window\)**

**Note:** This test is only required if the client is using companion banners.

If you click on the companion banner it opens a new browser window/webView?

## Companion Banner Tracking

**Impression \(e=90\)**

**Note:** This test is only required if the client is using companion banners.

When the companion banner appears in the screen, can you see a HTTP "tracker" request like below?

![Charles Proxy Tracker](../../image/event_code90.png)

**Click-through \(e=92\)**

**Note:** This test is only required if the client is using companion banners.

If you click on the companion banner can you see a HTTP "tracker" request like below?

![Charles Proxy Tracker](../../image/event_code92.png)

**Parent topic:**[Validation Importance and Process](../../../oadtech/ad_serving/dg/validation_importance_process.md)

