# Validation Tools

## Charles Proxy

Charles Proxy is not mandatory, some tests can be performed using the browser console or firebug. We recommend it though, as Charles Proxy has some good tools to help mapping and throttling the app's HTTP requests. You can download a free trial version of Charles Proxy. Open Charles Proxy \> View \> Sequence, then add a filter distributor|tracker. Click on the Settings button and enable "Filter uses regex".

**Configure Charles to use Ooyala's testing account and scenarios**

You can use Ooyala Testing Account, where some predefined test scenarios are already set up, by modifying the application code or rewriting the HTTP request params sent from the integration to Ooyala backend. Using HTTP rewrites is a much faster way to test the application as you don't need to modify the code, compile, and deploy. This step is not required, but highly recommended as it will speed up the testing.

1.  Download the xml file [adproducts\_charles\_rewrite.xml](https://ooyala.box.com/shared/static/35d0g8i9lyx0f6eyy8qwpcaggzgbna2z.xml) to your computer
2.  Start Charles Proxy and click Proxy \> Tools \> Rewrite...
3.  Select Enable Rewrite, and In the Set menu click Import
4.  Import into Charles Proxy the file "adproducts\_charles\_rewrite.xml"
5.  Now in your Sets menu you should have something similar to the image below ![Sets Menu](../../image/sets_menu.png)
6.  Select vp\_host and double-click the Host rule. Modify xx-clientName with the client Ooyala Pulse Account Identifier.

**Parent topic:**[Validation Importance and Process](../../../oadtech/ad_serving/dg/validation_importance_process.md)

