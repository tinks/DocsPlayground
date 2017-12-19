# Timing

This tutorial explains the importance of ad timing and how the ad behavior works.

\[ooyala:h2dTU4djrjHhI8IuAm2EmjEsWphRpTCQ\]

![Timing](../../image/timing.png)

**Ad HTTP request takes place after the play button is clicked?**

A new "distributor" request should only happen when:

-   New pre-roll ad: the user click the play button or the player auto-start
-   New mid-roll ad: on cuepoint, at the exact time the ad should appear. Pre-fetching mid-roll ad requests should not be implemented as they might result in inflated stats - Ooyala Pulse tracking the ad requests, without the users necessarily getting to the point in video where the ads are played.
-   New post-roll ad: on video content completed. Pre-fetching post-roll ad requests should not be implemented for the same reason as mid-rolls.

Open Charles Proxy and start the player. You should see only the "distributor" HTTP request when the player starts, on cuepoint or on completed.

![Resulting "distributor" Request](../../image/filter_distributor.png)

**Subsequent ad requests should be made "just-in-time" \(meaning, for mid-rolls and post-rolls\)**

Does the mid-roll and post-roll "distributor" request happen only at the correct time? Ad requests are not being pre-fetched, on page load or playlist load. This conditions is required only if applies in your use-case \(the blue dot indicates this\).

**Parent topic:**[Step by Step Validation Process](../../../oadtech/ad_serving/dg/validation_step_by_step.md)

