# Goal Overview

After you save the new goal, you see it in the Campaign overview under Campaign goals. It has a red warning sign saying "Goals without configured ads" because no ads have been added yet. Click on it to expand the Goal overview:

![Goal overview](../../image/pulse_campaigns_goal_overview.png)

## Parts of the Goal Overview

|Part|Name|Description|
|----|----|-----------|
|1|Goal information|Basic information about the goal. Double-clicking the pen icon gives you the option to edit. Read more about goal status and goal progress bar in [Monitoring Tools](monitoring_tools.md).**Note:** The field SEQUENCE can only ne set here. Read more about "Goal Sequencing" below.

|
|2|Goal menu|Clicking the goal menu gives you two options:1.  **Duplicate goal**:
    -   The goal has the same attribute values, like start and end date, as the original.
    -   It contains the same ads as the original, and the ads are automatically inactivated to prevent the goal from running immediately.
    -   The name of the duplicate goal is set as <original goal name\> - Copy, but can be changed before actually duplicating the goal.
2.  **Delete goal**: this cannot be undone.

|
|3|Goal performance chart|When the campaign is launched and has gathered data, you see a chart showing the amount of impressions and click-throughs for all formats together, or for a specific format, during a certain time period. Hovering over the bars gives you detailed information. Hide the performance chart by clicking this field.|
|4|Performance chart menu|Click the menu to choose a time period for which you want to get performance data. You can get data from yesterday, last week, last month, or since start. The data can be presented by hour, day or week, depending on the selected period.|
|5|Export|When the campaign is launched and has gathered data, clicking the button opens a new window with a table overview of the goal performance chart data.|
|6|Goal metrics|Short overview of some of the most important metrics. In the COMPLETION field, click the magnifying glass icon for more details.|
|7|Goal settings|Overview of some of the goal settings. Double-click the pen icon to edit. Some of the settings can only be set here:-   **Prio**: if not edited, it inherits the campaign setting. Setting the priority at goal level overrides any global or campaign priority setting. Pulse makes sure all goals with priority 1 are delivering according to schedule first. Then it focuses on priority 2 goals, then priority 3, and so on.

**Note:** The decision engine always makes sure a Share of Voice goal is delivering according to schedule, before an impression goal has a chance of getting selected, no matter which priority you set for the two goals.

-   **Frontload**: if not edited, it inherits the campaign setting. Frontload is not applicable to Share of Voice goals, goals with unlimited impressions, goals without end dates or sponsor goals \(and therefore is not visible as an option for these goal types\). For more information on frontload, refer to [Glossary](glossary_pulse.md).
-   **Custom goal ID**: add an identifier of your choosing that helps you recognise this item.

|
|8|Description|Double-click the pen icon to enter a description of the goal, or edit an existing description.|
|9|Goal targeting|Expand the "Add targeting rules" tab. Configure targeting rules as explained in [Add Targeting Rules](add_targeting_rules.md).|
|10|Add new ad|Click the button to add an ad to the current goal. For more information, refer to [Add New Ad](add_new_ad.md).|

## Goal Sequencing

Use goal sequencing when a campaign has a storyline, with two or more different ads that should be shown to a viewer in a specific order. This feature ensures that a specific ad is served in sequence after another one. Goals with lower sequence numbers serve ads before goals with higher sequence numbers. When a viewer sees an ad in a sequence, only the next ad is eligible after that, or the first one if the sequence is finished. This only works for goals within the same campaign.

**Sequencing scope** is set on campaign level, and offers two options:

-   **Session**: sequences reset for every new session. Use this option to limit goal sequencing to a session.
-   **Campaign lifetime**: sequences are active for the full campaign lifetime. Use this option for storytelling over a longer period of time.

**Example:**

Goal A \(pre-roll\), Goal B \(mid-roll\), Goal C \(mid-roll\) and Goal D \(post-roll\) within a single campaign should be displayed in sequence. Set the sequence number for each goal as follows:

-   Goal A = 1
-   Goal B = 2
-   Goal C = 3
-   Goal D = 4

**Result:**

-   In the pre-roll break, goal A is the only goal of these four that qualifies and is selected. Since goal A is first in the sequence, it can always qualify.
-   In the first mid-roll break, B qualifies because A has been shown to the user already, but C does not qualify because B has not been displayed yet.
-   In the second mid-roll break, C qualifies because B has already been displayed and cannot qualify for the same position again.
-   In the post-roll break, goal D qualifies because C has been displayed.

**Note:** If two goals have the same sequence value, a temporary split in the sequence is created and only one of the goals is picked for that position.

**Parent topic:**[Create a Campaign](../../../oadtech/ad_serving/ug/create_a_campaign.md)

