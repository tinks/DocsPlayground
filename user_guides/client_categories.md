# Client Categories

From the Client Categories tab you can:

1.  add a new client category,
2.  associate clients,
3.  and enable clash protection.

All three options are connected and described in this section.

## Add New Client Categories

1.  Open the Clients tab from the menu \(![Clients icon](../../image/pulse_clients_icon.png)\).
2.  From the Clients Overview, click on the Client Categories tab.
3.  Click on **Add new client category**. A new page opens up:

    ![Client Category creation page](../../image/pulse_clients_client_category_creation_page.png)

4.  Fill in the following information:
    1.  **Client Category Name**: enter a name for the client category
    2.  **Client Category Description** \(optional\): add a description of the client category for your own internal reference. Enter any notes you may have for yourself or your colleagues
    3.  **Client Category Custom ID** \(optional\): add an identifier of your choosing that helps you recognise this item. The Client Category Custom ID can be passed in third party VAST tags to help ensure that clash protection works when using third party ad sources. For more information, refer to [Ooyala Pulse Macros](http://community.ooyala.com/t5/Ad-Products-Knowledge-Articles/Ooyala-Pulse-Macros/ta-p/7041).

        **Note:** Use up to 100 characters which may include alphanumericals and the following special characters: - \_ . \(dash, underscore, dot\).

        **Note:** In order for third party ad clash protection to work, the third party ad source has to support the feature.

5.  Click **SAVE**.

## Associate Clients

After adding a new client category, click on it from the client category list to expand the tab:

![Client category expanded](../../image/pulse_clients_associate_clients.png)

1.  Click the **Associate clients** button. The **Select Clients** page opens up.
2.  Click on the folder icon ![Folder icon](../../image/pulse_clients_associate_clients_folder_icon.png)next to Advertiser or Brand to trigger the dropdown.
3.  Check the box next to advertisers or brands you wish to select:

    ![Select Clients page](../../image/pulse_clients_select_to_associate.png)

    **Note:** It is important to name both the advertiser or brand and their competitors within the same client category.

4.  Click **Select**.

**Note:** To delete a membership, click on the menu next to the desired membership.

## Enable Clash Protection

After associating clients, you get the option to enable clash protection. This prevents advertisers or brands from clashing with each other during an ad break. When clash protection is enabled for a client, ads from that client are not shown together with ads from other clients in the same client category, which means they are completely exclusive during the entire content duration or during an ad break, depending on the setting.

**Note:** Clash protection is not taken into account when doing goal forecasting.

1.  In the **Clash Protection** field, double-click the pen icon next to the desired membership: ![Clash Protection column](../../image/pulse_clients_clash_protection.png)

    **Edit clash protection** pop up window opens up. The default setting is **None**, which means clash protection is disabled.

2.  To enable clash protection, choose between:
    -   **Break**: ads in this category are never displayed in the same break.
    -   **Session**: ads in this category are never displayed in the same session. A session refers to the duration of content.
3.  Click **SAVE**.

**Example**:

![Clash Protection example](../../image/pulse_clients_example_clash_protection.png)

**Result**:

-   The brands Mazda and BMW do not appear in the same ad break as Volvo.
-   The brands Volvo and BMW do not appear in the same ad break as Mazda.
-   The brands Mazda and Volvo do not appear in the same session as BMW.

**Note:** Rules are applied depending on which clients's ad gets picked first.

**Parent topic:**[Clients](../../../oadtech/ad_serving/ug/clients.md)

