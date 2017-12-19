# Settings

You can personalize your ad delivery, video player experience and Pulse user interface by configuring the different settings when you open Settings from the menu \(![Settings icon](../../image/pulse_settings_icon.png)\).

## Account Settings

The account settings allow you to configure user interface settings for your entire account, visible for all Pulse users, and language settings for your video players ads.

**Locale Settings**

|Setting|Description|
|-------|-----------|
|Player Language|Set the language to be used in the video player, that is the countdown text for video ads and all other messaging.|
|Currency|Set which currency you will use for working with campaign budgets. This currency is also visible in reports.|
|Account Time Zone|Set the time zone for your reporting.|

**Campaign Manager Settings**

|Setting|Description|
|-------|-----------|
|Archive old campaigns|Select the time period for a recently ended campaign to be automatically moved to the "Archive" tab. The default setting is 14 days.|
|Default page size|Select the number of rows that are visible in tables on pages including Campaigns, Archive and Clients. The default setting is 10.|

**Live Preview Settings**

|Setting|Description|
|-------|-----------|
|Enable Live Preview|By selecting "live preview", all ads will have a "live preview" option next to the "preview" option in Pulse. This function is disabled by default.|
|Default Preview URL|When using live preview, you see an ad on your own site. This setting allows you to set a default URL for your preferred video player. You still get the option to enter other video player URLs upon using the live preview function.|

**3rd party Ad-serving**

|Setting|Description|
|-------|-----------|
|Enable passback|Check the box to enable passbacks from 3rd party ad sources to maximize your fill rate. This function is disabled by default.|
|Allow max number of passback ad sources|Select the maximum number of passbacks \(1 to 9\). This refers to the maximum number of passback candidates in the passback chain and defines how many ad sources get offered the chance to "be on standby" for a position. The default setting is 2.|

Passbacks have two additional settings built in, related to timeouts, to offer the best user experience. These settings allow configuration of maximum allowed response time. To change these settings and make sure passbacks are enabled, please contact your account manager.

**Intergration Information**

|Setting|Description|
|-------|-----------|
|Sub-domain|The sub-domain is a username that connects your video player to your Pulse account. This information is a reference for you when talking to the Ooyala Ad Solutions Integrations Team.|
|Account ID|The Account ID is the ID for your account to be used when integrating a third party system with Pulse. This information is a reference for you when talking to the Ooyala Ad Solutions Integrations Team.|
|FTP Account|The address and login details to an FTP account connected to your Pulse account. If you want to upload a creative that has a large file size \(<500 mb\), we recommend using FTP for upload. Click **Show/Hide FTP password** to see/hide your password.|

**Note:** Do not forget to click the **Save Account Settings** button in the bottom when you have finished configuring your Account Settings.

## Campaign Settings

**Default Campaign Delivery Settings**

|Setting|Description|
|-------|-----------|
|Default Campaign Priority and Delivery Mode|Set the default values on priority and frontload for any new campaigns you create. By default, this is set to priority 5 and 30% frontload.|
|Automatic Optimisation|Enable eCPM optimisation to allow campaigns with a higher eCPM value to be selected before campaigns with a lower eCPM. This only works with campaigns within the same priority level. The eCPM of a goal is based on the configured budget for the goal divided by the total number of impressions in that goal, that is budget per impression. Goals that have a set budget get selected before goals with no configured budget.|
|VAST Setting For New Campaigns|Set the campaigns to be delivered through VAST by default.|

**Global Targeting Rules**

You can set default values for targeting for all campaigns, which may later be overridden by a specific campaign or goal. A common use case for defining global targeting is to divert traffic away from some content – like children's shows or specific audiences like in‐house staff. For more information, refer to [Targeting Rules](targeting_rules.md).

**Note:** Do not forget to click the **Save Campaign Settings** button in the bottom when you have finished configuring your Campaign Settings.

## Targeting Templates

Targeting templates help those who use the same targeting rules often. This simplifies work and makes targeting management more effective. With this feature, you only have to create the targeting once, and then apply it to your campaigns or goals.

**Note:** This feature needs to be enabled in the backoffice. Contact your Account Manager to set the desired number of targeting templates.

**Create a Targeting Template**

1.  Click the **New template** button located in the bottom. A new page opens up:

    ![Targeting Templates creation page](../../image/pulse_settings_targeting_templates_creation_page.png)

2.  On the left, enter a name for your template. You can double-click the pen icon to edit the name.
3.  Configure the desired targeting rules as explained in [Add Targeting Rules](add_targeting_rules.md).
4.  Click **SAVE**.

Now, you can:

-   **Link your targeting template** to a campaign or goal. This means that the campaign or goal inherits all the rules from the template. If you edit the targeting template, the changes AFFECT all campaigns/goals linked to it. This is useful because you no longer have to go through many campaigns with the same targeting just to change one small detail.
-   **Import rules from a targeting template** to a campaign or goal. This means that the rules from the template are copied to the campaign or goal. If you edit the template, the changes DO NOT AFFECT the campaign/goal targeting. Importing rules can be useful when you want to use the rules from a template but still add some extra information manually.

## Inventory Forecast

You may hardcode your Inventory Forecast \(weekly impressions\) and override the Pulse forecasting module. Please use this with care and consult your Account Manager before, as setting a low amount of impressions makes all campaigns compete for space and might finish ahead of schedule.

**Note:** Do not forget to click the **Save Inventory Settings** button in the bottom when you have finished configuring your Inventory Settings.

## Personal Settings

Customise your personal experience of the Pulse user interface. Enter or change your name, surname and email.

**Date and Time Format Settings**

|Setting|Description|
|-------|-----------|
|Region|Select the region to define time format settings in reports and the user interface. You get a preview of the changes after saving the settings.|

**Note:** Do not forget to click the **Save Settings** button in the bottom when you have finished configuring your Personal Settings.

## Global Tracking

Set up global external pixel trackers which work for all campaigns and ads:

1.  Click **Add External Pixel Tracker**.
2.  Select the event which triggers the external pixel tracker.
3.  Enter the URL for the external pixel tracker. The URLs may contain macros, which are described on the [Ooyala Pulse Macros](http://community.ooyala.com/t5/Ad-Products-Knowledge-Articles/Ooyala-Pulse-Macros/ta-p/7041) page.
4.  Click **Save External Tracking Settings** when you are done entering all the external pixel trackers.

**Note:** All added global tracking pixels work retroactively, which means that tracking is applied to all ads that were already active before the tracker was added.

**Note:** Duplicate tracking pixels, where the tracking event and URL are exactly the same, do not result in duplicate tracking. This is also true if the same tracker is defined on an individual ad and on the global level.

**Parent topic:**[Ooyala Pulse User Guide](../../../oadtech/ad_serving/ug/introduction.md)

