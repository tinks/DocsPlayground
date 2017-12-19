# Ad Overview

After you save the new ad, you see it in the Goal overview under Ads. Click on it to expand the Ad overview:

![Ad Overview](../../image/pulse_campaigns_ad_overview.png)

## Parts of the Ad Overview

|Part|Name|Description|
|----|----|-----------|
|1|Ad information|Basic information about the ad. Double-clicking the pen icon gives you the option to edit.**Note:** The field WEIGHT can only be set here. For more information, refer to [Ad Weight](#ad_weight)

|
|2|On/Off button|If you have uploaded a creative, the ad is turned on automatically. Always check if the ad is active before you launch the campaign.|
|3|Ad menu|Clicking the ad menu gives you the following options:-   **Preview ad**: this gives you the option to preview the ad clip.
-   **Live Preview ad**: this loads the ad on the default preview page, and also gives you the option to edit the URL to preview the ad on another page.
-   **Duplicate ad to goals**: use this option to duplicate the ad to other goals part of the current campaign, including the goal where the ad already belongs to. For more information, refer to [Duplicate Ad to Goals](#duplicate_ad_to_goals)
-   **Delete ad**: this cannot be undone.

|
|4|Ad performance chart|When the campaign is launched and has gathered data, you see a chart showing the amount of impressions and click-throughs for an ad during a certain time period. Hovering over the bars gives you detailed information. Hide the performance chart by clicking this field.|
|5|Performance chart menu|Click the menu to choose a time period for which you want to get performance data. You can get data from yesterday, last week, last month, or since start. The data can be presented by hour, day or week, depending on the selected period.|
|6|Export|When the campaign is launched and has gathered data, clicking the button opens a new window with a table overview of the performance chart data.|
|7|Ad metrics and settings|Short overview of some of the most important metrics and the possibility to edit the "Skippable" setting. Double-click the pen icon to edit. For more information on skip ad button settings, refer to [Ad Insertion Policies](ad_insertion_policies.md). In the COMPLETION field, click the magnifying glass icon for more details.|
|8|Description|Double-click the pen icon to enter a description of the ad, or edit an existing description.|
|9|Preview and edit options|By clicking on the tabs you can:-   **Live preview the ad**: this loads the ad on the default preview page and gives you the option to edit the URL to preview the ad on another page.
-   **Preview the ad**: this gives you the option to preview the ad clip.
-   **Edit ad**: this opens a new page where you can edit the information you previously entered.

|
|10|Asset link|Clicking on the link automatically downloads the media files.|
|11|External Tracking|If you added an external tracking pixel, you see the information here, including the event which triggers the external pixel tracker and the URL for the external pixel tracker.|

## Ad Weight

Ad weight is used to choose how often to pick a specific ad after the goal has already been picked. If there are multiple ads of the same ad format in one goal, they take an even share of the impressions by default. If one of the ads needs to run more frequently you can add a weight to that ad.

**Example**: A goal has 4 ads. One of them should claim the majority of impressions. Pulse adds a weight of 40% to that ad. The remaining ads automatically split the remaining 60% between them, which means that each ad gets 20% of the impressions.

**Note:** Weight is applied within individual ad formats only. Pre-rolls can have weight applied only against other pre-rolls. It is not possible to serve 20% post-rolls and 80% pre-rolls. To do that, you need to create separate goals and manually count the right amount of impressions for each goal.

## Duplicate Ad to Goals

**Duplicate ad to goals** is used to duplicate an ad to one or more goals within its campaign, including the goal it already belongs to. After selecting the menu option, another window opens where you can enter a new name for the ad and select the goals where you want to duplicate the ad.

![Duplicate Ad to Goals window](../../image/pulse_duplicate_ad.png)

**Note:** only goals that have not ended are displayed for selection.

The duplicated ad is turned off by default and inherits all properties from the original ad, except for:

-   **Start date** is inherited from the goal the ad is copied to.

**Parent topic:**[Create a Campaign](../../../oadtech/ad_serving/ug/create_a_campaign.md)

