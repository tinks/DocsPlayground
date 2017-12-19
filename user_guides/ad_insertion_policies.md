# Ad Insertion Policies

You can configure a unique ad insertion policy on any category of your content from within Pulse to control the ad serving down to individual content level. The policy states what ad formats can run on this content category, how many linear ads should appear in breaks, how long the duration of the break should be, at what frequency non‐linear ads should appear and if the ads should have a skip button or not. The settings for a category are inherited to all subcategories, but you can choose to override these settings on any sub-level. The ad insertion policies are flexible and can also be applied to devices and content play length. If you want to boost or limit the ad serving on specific devices you can customise that. You can have individual ad insertion policies for long and short video, making it easy to optimise ad load for long or short form to take into account user behaviour around the content type.

When you click on the insertion policy icon, or choose "Ad Insertion Policy Settings" from the desired category's menu, the following page opens up:

![Insertion policies page](../../image/pulse_account_insertion_policies.png)

## Parts of the Insertion Policies Page

|Part|Name|Description|
|----|----|-----------|
|1|Override parent policies|The settings for a category are inherited to all subcategories, but you can choose to override these settings on any sub‐level by activating this button. You have to activate the button to be able to configure the insertion policy, otherwise all the settings are greyed out.|
|2|Device containers|By default, the Insertion policies page opens up for all devices/services. Choose a device container from the list to configure ad insertion policies for a specific device container you want to target. **Note:** Insertion policies are not inherited across devices.

|
|3|Short/long form policies|Enable if you want to use different insertion policies for short and long form content.|
|4|Format specific settings|Settings options for different formats. For more information, see below.|
|5|Save Insertion Policies|Click the button to save your Insertion policies configuration.|

**Spot settings**

-   **Enable or disable** interactive and/or standard spot ad formats.
-   **Time-based Frequency Cap**: select the minimum number of minutes that have to pass before any linear ad can be shown to a viewer again. You can select from a time range of zero to 10 minutes, or set it to 20, 30, 40, 50 or 60 minutes.

    **Note:** Sponsor goals are also affected by this cap.

-   **Skip Ad Button**: select whether to show the skip ad button **always**, **after first unique view** or **never**.

    -   Selecting **always**gives you the option to set the amount of seconds, or the percentage of the ad, after which the skip button appears.
    -   Selecting **after first unique view** gives you the option to reset view count after a certain time period. You can choose to reset on a scale from 1-48 hours.
    **Note:** Campaigns, goals and ads inherit the insertion policy settings. You can override these settings on campaign, goal or ad level. For more information, see below.

-   **Enable or disable mid-roll, post-roll and pre-roll ads.** When enabled, you get two options:
    1.  Configure **position based breaks** by choosing the maximum number of ad positions for each ad format per ad break.
    2.  Configure **time based breaks** by selecting to limit break duration, and entering the maximum amount of seconds you want the ad break to last. For time based breaks, both maximum duration and maximum number of ad positions have to be specified. The ad break ends when it reaches the specified duration, or when all its slots are filled, whichever happens first.

        The limitations of using time based breaks are:

        -   It guarantees that ad breaks are not longer than the time you set, but it does not guarantee the complete duration limit is filled with ads.
        -   Ads that are too long \(exceed the defined duration limit of the break\) are not eligible for time based breaks and will not get selected.
        -   The forecasting engine does not take time based breaks into account. It always assumes that the maximum number of impressions is available, even though fewer ads might be shown in time based breaks. This limitation affects campaign and inventory forecasts, and the projected delivery of running campaigns and goals.
        -   You have to **specify the estimated duration of 3rd party ads** to make them eligible for time based breaks. If the ad exceeds the duration limit of the break, it will not get selected.
        **Note:** This feature needs to be enabled in the backoffice. Contact your Account Manager if you want to use time based breaks.

-   **Ad Selector Ads**: choose the maximum number of ads on a scale from 2-6. Enter the amount of seconds after which playback begins automatically.

**Skin Settings**: enable or disable the Skin functionality.

**Pause ad Settings**: enable or disable Pause ad functionality.

**In-Stream Overlay settings**

-   **Enable or disable** the delivery of overlay ads.
-   **First insertion**: the time when the first overlay impression appears. Choose on a scale from 1-60 seconds. The default setting is 20 seconds.
-   **Display for**: the amount of time the overlay is visible before hiding automatically. Choose on a scale from 5-30 seconds. The default setting is 15 seconds.
-   **New overlay every**: the number of minutes that need to pass before a new overlay impression appears. Choose on a scale between 1-10 minutes. The default setting is 4 minutes.

## Override Skip Ad Button Settings

There are some occasions when an advertiser does not want their ad to be skippable, so you need to override the insertion policy settings by changing the "skippable" settings on the campaign, goal or ad level. Find the option as shown below:

**Campaign overview**

![Campaign Skippable Setting](../../image/pulse_override_skippable_campaign_overview.png)

**Goal overview**

![Goal Skippable Setting](../../image/pulse_overview_skippable_goal_overview.png)

**Ad overview**

![Ad Skippable Setting](../../image/pulse_override_skippable_ad_overview.png)

Double-click the pen icon. A pop up window opens up:

![Skip ad settings pop up](../../image/pulse_override_skip_ad_settings_page.png)

Select **Override parent settings** and configure the settings as you want. The skippable column displays a different value based on the settings you enabled:

|Value|Description|
|-----|-----------|
|Inherits|Inherits settings from parent.|
|Yes|Overrides parent settings and is set to either:-   always be skippable, or
-   skippable after first unique view.

|
|No|Overrides parent settings and is set to never be skippable.|

**Note:** If you edit the settings for a campaign, all the goals and ads in that campaign inherit the campaign settings unless you have edited the settings for the individual goals or ads. The same is true for ads within a goal.

**Parent topic:**[Content Hierarchy](../../../oadtech/ad_serving/ug/content_hierarchy.md)

