# Monitoring Tools

The Campaigns Overview lists all campaigns and their current performance with real time data. There are three ways Pulse delivers campaign monitoring capabilities:

## Campaign Notifications

To help you address issues in campaigns, Pulse supplies notifications for items that need your attention. At the top of the Campaigns Overview tab is a part called Campaign Notifications. The title gives a summary of the amount of notifications for both errors and warnings. Expand the list to read each notification and click a row to access an item that needs attention.

When you click a notification, a filter is created to show only the relevant campaign in the list of campaigns. For example:

![Campaign Notifications](../../image/pulse_campaign_notifications.png)

## Campaign and Goal Status Icons

Like the icons in the Campaign Notifications, each campaign and goal in the campaigns list has a status icon. For example:

![Campaign Status Icons](../../image/pulse_campaign_status_icons.png)

The following icons are available:

|Icon|Name|Description|
|----|----|-----------|
|![Campaign Status OK](../../image/pulse_planner_status_ok.png)|OK|The campaign or goal is ok.|
|![Campaign Status Failed](../../image/pulse_planner_status_failed.png)|Error|An error is present for the campaign or goal. If you hover over the status icon, a window listing the errors appears.|
|![Campaign Status Warning](../../image/pulse_status_warning.png)|Warning|A warning is present for the campaign or goal. If you hover over the status icon, a window listing the warnings appears.|
|![Campaign Status In Progress](../../image/pulse_planner_status_in_progress.png)|In progress|A known status cannot be shown yet for the campaign or goal. The system is working to find out what the status is and displays the status when known.|

## Campaign and Goal Progress Bar

The projected delivery of a campaign or goal is embedded into the progress bar, and can be used to take proactive measures when campaigns or goals are not forecast to reach their target. The projected delivery is continuously refreshed through a background simulation on the whole account, forecasting up to 100 days into the future.

![Campaign Progress Bars](../../image/pulse_campaign_progress_bars.png)

**Note:** All Active campaigns and goals, meaning their lifetime falls within the next 100 days, are taken into account in the background simulation, whether or not they have been turned on. You also get projected delivery for campaigns that have been turned off. For example:

![Progress Bar for a turned off Campaign](../../image/pulse_campaign_progress_bar_inactive.png)

**Progress Indicators**

The different colours and indicators are explained below:

|Image|Name|Description|
|-----|----|-----------|
|![Progress Bar Green](../../image/pulse_campaign_progress_bar_green.png)|Green|The campaign or goal is expected to deliver more than 99% of its target.|
|![Progress Bar Red](../../image/pulse_campaign_progress_bar_red.png)|Red|The campaign or goal is not expected to deliver more than the currently indicated percentage, or expected to deliver less than 90% of its target.|
|![Progress Bar Amber](../../image/pulse_campaign_progress_bar_amber.png)|Amber|The campaign or goal is expected to deliver more than the currently indicated percentage, but not expected to reach 99%. The shaded area is the projected delivery percentage.|
|![Progress Bar Arrow](../../image/pulse_campaign_progress_bar_arrow.png)|Lifetime indicator|The lifetime indicator shows you where you are in the lifetime between the start and end date of the campaign or goal. This indicator is only available for:-   Share of Voice goals and campaigns with an end date.
-   Goals with unlimited number of impressions and an end date.

|

If you hover over a progress bar, a tooltip appears with more information about the projected delivery. For example:

![Progress Bar Tooltip](../../image/pulse_campaign_progress_bar_tooltip.png)

A progress indicator is not available for:

-   Goals without an end date.
-   Goals without ads or all its ads are turned off.
-   Goals with an end date more than 100 days into the future.
-   Campaigns containing any of the above types of goals.

**Parent topic:**[Monitoring Campaigns](../../../oadtech/ad_serving/ug/monitoring_campaigns.md)

