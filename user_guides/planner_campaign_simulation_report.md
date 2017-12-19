# Campaign Simulation Report

The campaign simulation report gives insight into the possible campaign delivery, showing the total values as well as a daily breakdown graph, and all competing campaigns.

![Campaign Simulation Report](../../image/pulse_planner_campaign_simulation_report.png)

## Report parts

|Part|Name|Description|
|----|----|-----------|
|1|Campaign simulation report parameters|Show or hide the parameters for the simulation.|
|2|Campaign simulation report numbers|View the totals of the campaign delivery metrics for the report. These metrics are:-   **Average daily delivery**: Average daily delivery required to reach the campaign goal.

**Note:** This is only shown as a reference point if you specify a delivery goal amount. This is not how the campaign is forecast to deliver day by day.

-   **Unused inventory**: Reachable inventory for the simulation, not forecast to be used by existing campaigns.
-   **Accessible inventory**: Theoretical maximum accessible inventory the campaign can reach. However, parts of this inventory is forecast to be used by other campaigns.
-   **Campaign delivery**: Total possible campaign delivery, which is a number up to the delivery goal set during the simulation creation, indicating how much of the delivery goal is forecast to be delivered.

**Note:** While there may be enough inventory over the whole time period to deliver the campaign, it might still not be a good idea to book it if the daily breakdown shows there is no unused inventory on a specific day.


|
|3|Competing goals|The competing goals table gives an indication of which higher priority goals are taking up the inventory that the campaign goal in question could have used. The “competing imp.” column shows how many impressions the competing goal “took” from the forecast campaign goal. If you need to free up more inventory, you can click on the campaigns in question and target its goals elsewhere. Keep in mind that:1.  the effect of the changes can take up to 20 minutes to go through, depending on the status of the background job,
2.  the freed competing inventory from higher priority goals may be taken up by other goals with higher priority, and
3.  same or lower priority goals are not yet shown.

|

**Parent topic:**[Planner](../../../oadtech/ad_serving/ug/planner_introduction_forecasting.md)

