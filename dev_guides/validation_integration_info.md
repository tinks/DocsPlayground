# Integration Info

## SDK Version and PID tutorial

This tutorial provides information on how to find which version of the SDK is used in the integration, and how to find the PID for the frequency capping cookie of the integration.

\[ooyala:MwY2wydzpw4vV7gEJ4joTVm3Wy2mimdn\]



## Integration Resources

If you are looking for the latest versions of our SDKs, you can find them on their respective pages:

-   [Flash SDK](flash_integration_resources.md#)
-   [HTML5 2.x SDK](html5_2_integration_resources.md#)
-   [Android 2.x SDK](android_2_integration_resources.md)
-   [iOS 2.x SDK](ios_2_integration_resources.md)
-   [HTML5 SDK \(Deprecated\)](html5_deprecated_integration_resources.md#)
-   [Android SDK](android_integration_resources.md#)
-   [iOS SDK](ios_integration_resources.md#)

## The frequency capping cookie "pid=" is present in the requests header

Open Charles Proxy and start the player \> select the "distributor" HTTP request \> Request \> Headers

![Charles Proxy PID validation](../../image/val_integration_info.png)

Is the pid present in the cookie header? If you reload the player a couple times and check each request cookie, has the pid the same value?

**Note:** the pid should be permanent \(always the same id string\) for all "distributor" HTTP requests.

**Parent topic:**[Step by Step Validation Process](../../../oadtech/ad_serving/dg/validation_step_by_step.md)

