# What is VAST?

VAST \([Video Ad Serving Template](http://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast)\) is the industry standard for communicating video ads from ad server to ad server and from ad server to video player. VAST is developed and maintained by the IAB \([Interactive Advertising Bureau](http://www.iab.net)\) which is comprised of more than 500 ad serving companies, including all the major ad serving actors like Ooyala, Doubleclick, Freewheel, and Liverail.

VAST is an XML based format that describes one or more ads, their media files, links to track on certain events, which page to open when someone clicks on the ad, and more. The version of VAST most commonly used today is VAST version 2.0.1. VAST 3 was introduces in mid 2012 and added extra optional functionality on top of the VAST 2 specification.

## VAST and Ooyala

The Ooyala ad server uses its native protocol VPTP3 with its more advanced platforms. The VPTP3 Protocol is based off of the VAST 3 specification but is extended to allow for Ooyala specific functionality not included in VAST. Ooyala also offers the standard ad formats through the VAST protocol which supports VAST 2 and portions of the VAST 3 specification.

An example of an Ooyala VAST request would look like this: `http://vp-validation.videoplaza.tv/proxy/distributor/v2?tt=p&rt=vast_2.0&s=validation&t=standard`

## VAST and the Ooyala Ad Products Mobile SDKs

The Ooyala Ad Products mobile SDKs use the VAST protocol internally but developers using the SDKs do not need to understand the VAST standard. When the SDKs receive a VAST ticket, they parse and package the ads into native objects for easy use by the developers. Even nested 3rd party VAST ad wrappers are requested and parsed by the SDKs into native objects making the support for 3rd party ads transparent.

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

