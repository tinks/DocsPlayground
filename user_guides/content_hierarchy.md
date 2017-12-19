# Content Hierarchy

When you open the Account from the menu \(![Account icon](../../image/pulse_account_icon.png)\), you see the following interface:

![Content Hierarchy Overview](../../image/pulse_account_content_hierarchy_tab_overview.png)

The Account Overview opens in the Content Hierarchy tab by default.

## Parts of the Content Hierarchy Tab

|Part|Name|Description|
|----|----|-----------|
|1|Select period|Select the time period for which you want to get a detailed report.|
|2|Filter tabs|Click here to switch between Content Hierarchy and Content Partners.|
|3|Current Path|By default, it shows the root node of your account. See "Change Path" below for more information.|
|4|Insertion policy icon|Clicking the icon opens the **Insertion policies** page. You can click on it whether it is visible or greyed out: -   The icon is visible if there is a defined insertion policy
-   The icon is greyed out if there is no defined insertion policy

For more information, refer to [Ad Insertion Policies](ad_insertion_policies.md).

|
|5|Change Path|Click here to select any node in your account. This opens the Select Path page and presents you with the structure of your account. Changing paths allows you to get detailed reporting on the chosen node and its configured subcategories, as well as adding a new category under a different node.|
|6|Content hierarchy structure|Overview of the top node and its underlying subcategories. This helps you to mirror the content structure you have defined for your video content.|
|7|On/Off button|Enable or disable ad serving for a category. Enabled by default.|
|8|Menu|Menu options. For more information, see below.|
|9|Add Category|Click here to add a new category. For more information, refer to [Add Category](add_category.md#).|

## Menu Options

Clicking the menu opens a pop up window:

![Content category menu](../../image/pulse_account_content_category_menu.png)

-   **Select as Report Path**: clicking here to select that node as the report path so you can get detailed reporting on that node and its subcategories, and add a new category under that node.
-   **Export VAST URL**: copy a request URL from ads targeted against the current category. Add the ad request URL to your VAST compliant video player. When this URL is requested, Pulse returns campaigns that are targeted against this category.

    **Note:** If a campaign that is targeted against this category has other targeting rules, for example tag targeting rules, these are not automatically picked as the VAST URL does not contain these tags. In that case, the tags must be added to the exported VAST URL.

-   **Performance report:** this opens a new page where you can:
    1.  View a **Full report** for the chosen category consisting of:
        -   Category Overview
        -   Distributed Campaigns
        -   Distribution by Day \(performance chart and table view\)
    2.  View a **Summary report** consisting of:
        -   Category Overview
        -   Distributed Campaigns
    3.  **Download**both the full report and the summary report as PDF or Excel.
-   **Delivery by Day or Subcategory \(Excel\)**: clicking here downloads the desired report as Excel spreadsheet.
-   **Ad Insertion Policy Settings**: clicking here opens the **Insertion policies** page, the same as when you click the insertion policies icon. For more information, refer to [Ad Insertion Policies](ad_insertion_policies.md).
-   **External Report Access**: click here to create a new external invitation and share your report. For more information, refer to [Share a Report](insight_share_a_report.md#).
-   **Delete**: this cannot be undone. When you delete a subcategory, its name and data are removed from the Pulse user interface. However, this does not affect the data in Insight reports because the category name is still visible but marked as "deleted".

    **Note:** You cannot delete the root node of your account or the "Unassigned" category.


-   **[Ad Insertion Policies](../../../oadtech/ad_serving/ug/ad_insertion_policies.md)**  

-   **[Add Category](../../../oadtech/ad_serving/ug/add_category.md)**  

-   **[Category Overview](../../../oadtech/ad_serving/ug/category_overview.md)**  

-   **[Category Aliases](../../../oadtech/ad_serving/ug/category_aliases.md)**  


**Parent topic:**[Account](../../../oadtech/ad_serving/ug/account.md)

