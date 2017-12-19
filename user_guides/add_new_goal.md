# Add New Goal

1.  Open Campaigns from the menu \(![Campaign Icon](../../image/pulse_campaigns_icon.png)\).
2.  From the Campaigns Overview, click on the campaign you want to add a goal to.
3.  Click the **Add new goal** button located in the bottom of the Campaign overview.

    A new page opens up:

    ![Goal Creation Page](../../image/pulse_campaigns_goal_creation_page.png)

4.  Fill in the following fields:
    1.  **Goal name**: enter the name of the goal.
    2.  **Goal mode**:
        -   Normal goal \(default setting\): populate a number of ad positions in an ad break.
        -   Sponsor goal: used for extra sponsor messages and guarantee a prime position directly after ad breaks in pre-rolls and mid-rolls, and before post-roll ad breaks, meaning they are delivered closest to content. Therefore, the option "Ad position" is greyed out.

            **Note:** Sponsor goal mode does not have an impression goal, so the below options "Delivery goal type" and "Delivery goal" are greyed out and set by default to 100% Share of Voice.

    3.  **Ad position**: select the desired ad position that ads from this goal are allowed to run within an ad break. Use this option to deliver ads close to content.
        -   Any position \(default setting\)
        -   First position only
        -   Last position only
        -   First or last position
        -   Break exclusive: means that an ad of the goal, if selected, is the only ad within the ad break. Read more about break exclusivity in [Glossary](glossary_pulse.md).
    4.  **Start date**: the start date of the goal. Uncheck the "Full day" box if you want to enter a precise start time \(hours and minutes\) of the goal.
    5.  **End date**: the end date of the goal. Uncheck the "Full day" box if you want to enter a precise end time \(hours and minutes\) of the goal. You may run the campaign without an end date ensuring it can deliver ads when other goals have met their delivery quota.
    6.  **Delivery goal type and Delivery goal**

        |Delivery goal type|Description|Delivery goal|
        |------------------|-----------|-------------|
        |Impressions|Need to secure a fixed number of impressions for the entire time period.|Enter the desired goal in number of impressions. The goal is completed when this number is reached. The default setting is 0.|
        |Share of Voice \(%\)|Take a percentage of all the possible impressions. Share of Voice goals are for this reason more aggressive in distribution and always take their share in the advertising slots before any other goal.|Enter the desired goal as Share of Voice percentage \(%\). The goal is completed when it reaches its end date. The default setting is 100%.|
        |Unlimited impressions|Goals without a defined impression target, which are ideal for lower revenue filler campaigns. They take up any remaining inventory.|None.|
        |25%, 50%, 75% or 100% Ad completion|Need to secure a fixed number of 25%, 50%, 75% or 100% ad completions. The ad completion feature measures for how long the ad played or if it was played to completion.|Enter the desired goal in number of completions. The goal is completed when this number is reached.The default setting is 0. When you click on the field, a pop up window appears on the right, showing impression estimates. Use impression cap to limit the amount of impressions delivered for the ad completion campaign in order to prevent inventory waste if the goal is not met. The cap is filled in automatically based on the delivery goal and the average completion rates for the last three weeks. Uncheck the box if you do not want to set an impression cap, or enter a number.|
        |Click throughs|Need to secure a fixed number of click throughs.|Enter the desired goal in number of click throughs. The goal is completed when this number is reached.The default setting is 0. When you click on the field, a pop up window appears on the right, showing impression estimates. Use impression cap to limit the amount of impressions delivered for the click through campaign in order to prevent inventory waste if the goal is not met. The cap is filled in automatically based on the delivery goal and the average CTR \(Click Through Rate\) for the last three weeks. Uncheck the box if you do not want to set an impression cap, or enter a number.|

    7.  **Pricing** \(optional\): specify the type of pricing and the corresponding value, which signifies the value of this goal against the entire campaign budget. The default setting is "No pricing". Goal pricing shows how each campaign goal is performing financially in Pulse and through reports. Each campaign also has a calculated effective cost per thousand impressions \(eCPM\). You can prioritise campaigns that have a higher eCPM value by enabling the "eCPM Campaign Optimisation" option. For more information, refer to [Campaign Settings](settings.md#campaign_settings). Goal budgets are not mandatory, but if skipped, you are not able to use the revenue reporting and automatic campaign prioritisation on eCPM. If you edit the pricing later in Goal overview, the new pricing is only taken into account in revenue reports for impressions delivered after the change.

        **Note:** Campaign priority prevails over eCPM campaign prioritisation.

5.  Click **SAVE**.

**Parent topic:**[Create a Campaign](../../../oadtech/ad_serving/ug/create_a_campaign.md)

