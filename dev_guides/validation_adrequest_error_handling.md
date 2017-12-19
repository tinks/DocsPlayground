# Ad Request Error Handling

## 404 During Ad Request to Ooyala ==\> Start Content Playback

This section and [Video Ad Error Handling & Tracking](validation_video_adrequest_errors.md) are usually the sections that cause most of the apps to fail at first. Please try to pay special attention to these in your testing procedures.

This tutorial demonstrates the user's experience when you have a 404 error during your ad request.

\[ooyala:13eDU4djr6PMFpMAtZeeUsTmfnu59jlQ\]



To fake a server 404 map all requests from Ooyala server to a 404 page. Open Charles Proxy \> Tools \> Map Remote... \> Enable Map Remote \> Add

![Charles Proxy Edit Mapping](../../image/edit_mapping_menu.png)

Select and click OK.

When you start the player, does the player correct error-handle the 404 issue and start the content?

## Timeout During Ad Request to Ooyala ==\> Start Content Playback

This tutorial demonstrates the user's experience when you have a timeout error during your ad request.

\[ooyala:0xeTU4djpKT9sAEW0gaj9fT7V6uEN0Ou\]



To fake a server slow response open Charles Proxy \> Proxy \> Throttle Settings \> Enable Throttling \> Add

![Charles Proxy Edit Host](../../image/edit_host_menu.png)

After adding the configuration above, start the video player. All requests to Ooyala will be very slow. Make sure your player timeouts and starts the content after a short, acceptable period.

## Empty Ad Response \(meaning, "nocom" flag\) ==\> Start Content Playback

This tutorial demonstrates the user's experience when you have an empty ad response error during your request.

\[ooyala:15eDU4djoDmx5rA0uXepcE15BW9Nj00r\]



Open Charles Proxy \> Tools \> Rewrite \> Enable Rewrite \> Select: vp\_host + vp\_nocom \> click OK.

When you start the player, does the player content start without displaying any ads?

**Parent topic:**[Step by Step Validation Process](../../../oadtech/ad_serving/dg/validation_step_by_step.md)

