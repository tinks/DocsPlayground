# Ad Targeting

In order for your Ad Operations department to find the integration useful, they need to be able to target ads against or away from certain content. This is done by the tag targeting. Tags are keywords that describe the current content, be it which site it is displayed on, in which player is displaying the video, or a description of the actual video item.

In Brightcove, there are three different ways to pass these tags:

1.  Player level inside Brightcove account.![Player Level Tag Passing](../../image/tag_passing.png)
2.  Player/embed level in embed code:

    ```
    <param name="additionalAdTargetingParams" value='vphost=http://vp-validation.videoplaza.tv&vptags=standard&vpcategory=validation' />
    ```

3.  Video level inside Brightcove account. These tags will always follow videos wherever they are displayed. ![Video Level Tag Passing](../../image/video_tag_passing.png)

**Parent topic:**[\(Deprecated\) Brightcove SMART Plugin \(Flash+HTML5\)](../../../oadtech/ad_serving/dg/plugin_bc_smart_flash_html5_deprecated.md)

