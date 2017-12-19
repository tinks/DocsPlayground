# Display

## Display More Than One Ad in the Same Slot \(For Example, 2 Pre-rolls\)

![Display Section of the Template](../../image/display_template.png)

This tutorial explains how to test your ad capabilities; specifically, it demonstrates how to test if you can show multiple ads in the same slot.

\[ooyala:NidzU4djrIFaHTaX\_a50-9BSujwcPevn\]



Open Charles Proxy then Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_standard \> click OK. Should look something like this:

![Charles Proxy tool](../../image/modifying_requests.png)

The subdomain in vp\_host ‘Locations' has to match the subdomain used by your requests.

Now when you start the player, can you see 2 pre-roll ads?

## Display Ads From Third Party Ad Server \(VAST Wrapper\)

This tutorial shows how to display ads from a third-party ad server.

\[ooyala:NkdzU4djp\_JCTH-dvQFLxmxALlAgQTeA\]



Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_3rd\_party \> click OK.

![Rewrite Settings Window](../../image/rewriting_settings_window.png)

In the highlighted region, make sure you change vp-validation account to the name of your account.

When you start the player, can you see a 3rd-party ad?

## Display VPAID Ads from Third Party Ad Server

This tutorial shows how to display VPAID ads from a third party server.

\[ooyala:NmdzU4djo\_M4TQYtPJNwHqhahwKp28m8\]



**Parent topic:**[Step by Step Validation Process](../../../oadtech/ad_serving/dg/validation_step_by_step.md)

