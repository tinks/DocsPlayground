# Create Inventory Simulation

Inventory simulations allow you to check how much inventory is forecast to be available for a specific target and time period, how much of that inventory is already forecast to be filled, and the fill-rate.

1.  On the Planner tab, click the **Inventory Simulation** button.

    The Inventory Simulation creation page opens.

    ![Planner Inventory Simulation creation page](../../image/pulse_planner_inventory_simulation_creation_page.png)

2.  Fill in the following fields:
    1.  **Simulation Name**: enter a meaningful name for the inventory simulation. This name is displayed in the list of simulations and in the simulation report.
    2.  **Start date**: the start of the simulation. This has to be a date in the future, which means that you can only create the simulation starting from the day after the current day.
    3.  **End date**: the end of the simulation. You can only enter a date up to 100 days from the current date, because the forecast becomes meaningless otherwise.
    4.  **Manual traffic estimate for simulation period** \(optional\): indicate the multiplier which should be applied to the average traffic sample taken from the traffic recorded in the previous two weeks. The default value is 100%. Any integer value between 1 and 500 may be filled in.

        Examples of use:

        A popular TV show starts a new season during the period for which you would like to run a simulation. From previous experience, you expect the traffic to your entire site to increase by 10% due to the TV show. In this case, you could enter 110% for the manual traffic estimate.

        In another case, you want to simulate inventory for children's shows during the summer holiday months. Again, from experience, you know that traffic for the whole site drops by about 30% during these months that you are simulating. For this simulation, you could enter 70% for the manual traffic estimate.

    5.  **Targeting template and Targeting** \(optional\): select targets through a targeting template, which was set up in the Settings tab, and/or through individually selecting content categories, tags and geotargets.
    6.  **Override global targeting** \(optional\): simulations use the global targeting settings by default. You may override global targeting for each targeting type. Select the check box corresponding to the targeting you want to override, available on each targeting type tab.
    7.  **Devices and services**: select all devices you want to target. If you want to target all device categories, click **All device containers**.
3.  When you are done configuring the inventory simulation, click **RUN SIMULATION**.

    You are returned to the Planner page, where you can see the progress of your simulation. The time it takes to run the simulation relates to the date range of your simulation.

    ![Creating Inventory Simulation Report](../../image/pulse_planner_create_inventory_simulation_report.png)


**Parent topic:**[Planner](../../../oadtech/ad_serving/ug/planner_introduction_forecasting.md)

