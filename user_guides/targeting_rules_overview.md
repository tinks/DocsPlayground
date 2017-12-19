# Targeting Rules Overview

When expanding the Add Targeting Rules tab, you see these parts, with slight differences, depending on the level:

![Add Targeting Rules tab](../../image/pulse_targeting_rules_overview.png)

## Parts of the Add Targeting Rules Tab

|Part|Name|Description|
|----|----|-----------|
|1|Targeting rules icons|Each targeting rule has a corresponding icon. Useful tips:-   These icons are visible even before expanding the Add Targeting Rules tab. Clicking directly on the desired targeting rule icon expands the whole tab as well as the specific targeting rule.
-   When you add a targeting rule, there will be a red dot next to the icon, allowing you to see which targeting rules have been added even before expanding the tab.

|
|2|Targeting template options|These options are available on campaign and goal level, but NOT on global level. When you create a targeting template, you can either link your template to a campaign or goal, or import rules from the template to a campaign or goal. For more information, refer to [Targeting Templates](settings.md#targeting_templates).|
|3|Targeting rules|You see the same set of targeting rules on global, campaign and goal level. For more information on how to set targeting rules, refer to [Add Targeting Rules](add_targeting_rules.md).|
|4|Override targeting rules|This enables you to have specific targeting rules that only apply to certain goals/campaigns that would otherwise be covered by a campaign/global targeting rule. For more information, see below.|
|5|Audience targeting|This targeting rule is not enabled by default. In order to use this functionality, you first need a data integration added to your account. Contact you Account Manager if you want to use this option. For more information, refer to [Appendix C - Pulse Audience Management \(PAM\)](appendix_c.md).|

## Targeting Rules

|Targeting rule|Description|
|--------------|-----------|
|Content Targeting|Target your video content to a specific content category from your Account.**Example**: Your video player passes information about the current video to Pulse, for example: 'The cooking show - episode 14'. You have a hierarchy of different categories that reflect this information in your Account. One of the categories is called 'The cooking show', which allows you to target your campaign to all episodes of that show.

|
|Tag Targeting|Target your video content across categories based on keywords in use from any video player or partner integration. Use it for targeting all content related to a topic, for example, 'cooking'. Tag targeting also allows you to target on content partners, such as videos by Disney or any other partner, which are useful for passing advertising with syndicated content.|
|Geotargeting|Target your video content to countries, regions, cities and/or metro areas. Metro area targeting includes Designated Market Areas in the United States of America \(US DMA regions\).**Note:** Metro area targeting is not enabled by default. Please contact your Account Manager if you want to use this feature.

|
|Frequency capping|Limit the number of times the same user sees a specific ad. You can use combinations of capping settings to create rules such as 'five times per day, but max twice per hour'. **Note:** For frequency capping to work, your Ooyala integration needs to be able to differentiate unique users either by cookies or by some other mean.

|
|Time of Day/Day of Week Targeting|Target a campaign or a goal to run only at a specific time period.|
|IP Targeting|Target one or many IP addresses to limit the audience. It is also used for targeting ads away from certain IP addresses, for example, when internal staff are watching videos and do not need to see ads.|
|Browser/OS Targetin|Target a campaign or goal against or away from a web browser in combination with an operating system.|

## Override Targeting Rules

Targeting rules are hierarchically inherited from global, to campaign and then to goal level. This needs to be taken into account when overriding a rule. This means:

-   If you have a targeting rule on global level, and you want to change it for a campaign, you need to override that rule on campaign level by checking the **Override Global Targeting Rule** box. That campaign now applies its own targeting rules, and not the global ones. All goals in that campaign inherit the campaign targeting rules.
-   If you have a targeting rule on global level, and you want to change it for a goal, you need to **Override Campaign Targeting Rule** on goal level. You also need to **Override Global Targeting Rule** on campaign level, otherwise the campaign inherits global targeting rules and applies them to all the goals in the campaign.

**Parent topic:**[Targeting Rules](../../../oadtech/ad_serving/ug/targeting_rules.md)

