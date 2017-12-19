# Planner

## What is Forecasting?

A forecast is a prediction of future conditions based on past and present data. Pulse continually collects data about all ad requests and responses, the 'past' data, which is used for the forecasting functionality in the system. The 'present' data used in forecasting is the current state of all campaigns, goals, ads, and other settings on your account. In this context, Pulse forecasts future ad inventory based on historical user traffic, and current campaign and account settings.

## The Simulation Engine

Pulse uses a simulation based forecasting approach, as opposed to a calculation or mathematical model based approach. This means that during a forecast, the forecasting engine simulates ad delivery by fast-forwarding the same ad decisioning engine, which will later deliver the ads, through a future inventory based on historical user data. The result is more realistic and accurate than a traditional calculation or mathematical model based approach.

The simulation engine is used for:

-   forecasting inventory,
-   forecasting how much inventory is reachable for a new goal you want to run, and
-   projecting delivery for running campaigns and goals.

The first two uses are available through the Planner and are discussed in the following sections. For the last use, refer to [Campaign and Goal Progress Bar](monitoring_tools.md#campaign_goal_progress_bar). For an overview of the Pulse distribution engine, refer to [Pulse Distribution Engine](http://community.ooyala.com/t5/Adtech-Knowledge-Articles/Pulse-Distribution-Engine/ta-p/8780).

## Simulation and Engine Details

The following information must be kept in mind when looking at and creating forecasts:

-   The forecasting engine can project **up to 100 days** into the future. This means that forecast requests are limited to date ranges between tomorrow and 100 days from tomorrow. The further into the future the forecast looks, the more uncertainty exists in the results. We have determined that 100 days provides for an optimal balance between accuracy and performance for the forecasting system.
-   The forecasting engine uses a **sample of actual user traffic \(ad requests\) from the previous two weeks** when forecasting into the future.
-   **Simulations** and their results are **kept for 14 days**. Given how often both traffic patterns and account settings \(campaigns, goals, and ads\) change, results of forecasts more than a few days old tend to lose their meaning and relevance. For this reason, the length of time that results are kept is limited.

For a list of frequently asked questions, refer to [Forecasting FAQ](http://community.ooyala.com/t5/Adtech-FAQs/Forecasting-FAQ/ta-p/8751).

-   **[Planner Interface Overview](../../../oadtech/ad_serving/ug/planner_ui_overview.md)**  

-   **[Create Inventory Simulation](../../../oadtech/ad_serving/ug/planner_create_inventory_simulation.md)**  

-   **[Inventory Simulation Report](../../../oadtech/ad_serving/ug/planner_inventory_simulation_report.md)**  

-   **[Create Campaign Simulation](../../../oadtech/ad_serving/ug/planner_create_campaign_simulation.md)**  

-   **[Campaign Simulation Report](../../../oadtech/ad_serving/ug/planner_campaign_simulation_report.md)**  


**Parent topic:**[Ooyala Pulse User Guide](../../../oadtech/ad_serving/ug/introduction.md)

