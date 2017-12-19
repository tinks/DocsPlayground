# Create New Custom Report

1.  Open Insight from the menu \(![Insight Icon](../../image/pulse_insight_icon.png)\).
2.  Click on the **New custom report** button.

    The **New report** page opens in the **Select Data** tab:

    ![Select Data tab](../../image/pulse_insight_new_custom_report_select_data.png)

3.  Fill in the following fields:

    1.  **Filters**: filters can be combined in order to narrow down the report. Click **Add filter** to create different combinations.

        |Filter|Value|
        |------|-----|
        |Campaign|Campaign name|
        |Advertiser|Advertiser name|
        |Brand|Brand name|
        |Agency|Agency name|
        |Content partner|Content partner name|
        |Format type|Ad format type \(for example: pre-roll, mid-roll or post-roll\)|
        |Category|Category node|
        |Time period|Custom range: enter the desired time periodor

Choose one of the available options from the pop up window

|

    2.  **Dimensions**: dimensions can be combined in order to create different breakdowns of data. Click **Add dimension** to create different combinations.

        |Dimension|Option|
        |---------|------|
        |Time period|Choose one of the available options from the pop up window|
        |Device group| |
        |Category| |
        |Content partner| |
        |Ad| |
        |Format type| |
        |Campaign| |
        |Goal| |
        |Tag|Select tags: enter tag name and click Save. Repeat until all desired tags are added.|
        |Geography|CountryCountry & region

|

    3.  **Metrics**: from the list of **common**, **interactive** and **other** metrics, select the ones that you want to include in your report. For metric explanation, refer to [Glossary](glossary_pulse.md).
    4.  **Layout preview**: shows the actual structure of the report. However, this IS NOT actual data from your report. Select or deselect the **Include totals** and **Include subtotals** box to change the layout of your report. As you add and remove filters, dimensions and metrics, you should notice the layout changing.
    **Note:** The **Report size bar** in the bottom left corner indicates how much work is required to store and read the report. It varies between small, medium, large and exceeded. If you exceed the allowed report size, you cannot save or pull the report. These limitations are set to ensure that big report queries do not slow down the system. Change the filters, dimensions and metrics in order to reach an acceptable report size.

    ![Report size small](../../image/pulse_insight_report_size_small.png)

    ![Report size medium](../../image/pulse_insight_report_size_medium.png)

    ![Report size large](../../image/pulse_insight_report_size_large.png)

    ![Report size exceeded](../../image/pulse_insight_report_size_exceeded.png)

    **Note:****Info messages** may show up when combining some filters, dimensions and metric, which means you have to make changes to your report in order to save it as a template or pull it. Below is a table with a list of possible info messages and their explanations:

    |Info message|Description|
    |------------|-----------|
    |Incomplete data for selected <X\>. For example: ![Info incomplete data](../../image/pulse_insight_info_incomplete_data_.png)|Insight provides data from a certain period. If data is not available for a certain period, you see this message, but you can still pull the report.|
    |Multiple <X\> dimensions is not supported. For example:![Info multiple date dimensions](../../image/pulse_insight_info_multiple_date_dimensio.png)|You see this when trying to use multiple dimensions that are not supported together. Such reports cannot be produced.|
    |Multiple <X\> filters is not supported. For example:![Info multiple date filters](../../image/pulse_insight_info_mulitple_date_filter.png)|You see this when trying to use multiple filters that are not supported together. Such reports cannot be produced.|
    |Cannot combine <X\> metric\(s\) with <Y\> filter\(s\) and dimension\(s\). For example:![Info cannot combine](../../image/pulse_insight_info_cannot_combine.png)|You see this when trying to pull a report with metrics that cannot be combined with selected dimension\(s\) or filter\(s\).|
    |![Info save report as template](../../image/pulse_insight_info_save_as_template.png)|You see this because Insight is not currently aggregating data for the selected dimensions, filters and metrics. You have to save the template in order to start aggregating the requested data.|
    |![Info invalid report definition](../../image/pulse_insight_info_invalid_report_definition.png)|You see this in two cases:    -   when you open the new report window, because you have not filled in any information yet
    -   when you have selected some invalid combination of filters, dimensions and/or metrics, which Insight has not described in a more specific info message
|
    |![Info Kubrick Reporting Service error](../../image/pulse_insight_info_kubrick_error.png)|An error message shown when something has gone wrong in Insight's backend.|

4.  Click **Next**.

    The **Header and summary tab** opens:

    ![Header and Summary tab](../../image/pulse_insight_new_custom_report_header_and_summary.png)

5.  Fill in the following fields:
    1.  **Header**: add a custom title to your report.
    2.  **Header fileds**: select the fields you want visible in the header part of your report.
    3.  **Key metrics**: select the metrics you want visible in the header part of your report.
    4.  **Header preview**: check to ensure that you highlighted the most important information.
6.  Click **Next**.

    The **Preview** tab opens:

    ![Preview tab](../../image/pulse_insight_new_custom_report_preview.png)

    Use the Preview tab to ensure that the report layout matches your expectations.

7.  Click **Save as template** or **Pull report now**:
    -   If the new report can be based on an existing template, it is possible to pull it immediately from the report builder by clicking the **Pull report now** button. Otherwise, the button is greyed out.

    -   If the "Pull report now" button is greyed out, you first need to click the **Save as template** button, after which the report appears in the report library and immediately starts collecting data.


**Parent topic:**[Insight](../../../oadtech/ad_serving/ug/insight.md)

