# Ooyala Pulse Audience Management

## Background

This document details a typical data integration with Ooyala Pulse Audience Management, which allows Pulse users to target 3rd party data directly through the Pulse platform. Please contact your Account Manager at Ooyala if you want to start using Ooyala Pulse Audience Management.

## Limitations

-   Max 100 segments types per integration - Each integration is allowed up to 100 segment types \(for example, "gender, "age", ...\)
-   Max 15 segment values per type - Each segment type can contain 15 different values \(for example, "male", "female" or "21-30 years old", "31-40 years old", ...\)
-   Max 3 integrations per account - Each account is allowed max 3 integrations per default.

## Milestones/Artifacts

-   Intro meeting with client and data vendor
-   Segment identification document - List of segments and how they are to be identified to be defined between vendor and Ooyala with client's consent. CSV or Excel format.
-   Segment setup in Ooyala Pulse - PS to upload segment identification document to Pulse and enable a `<vendor name>` targeting entity for client's account.
-   Test of segment transfer - vendor/client to set up test page where Ooyala can validate that unique user gets properly tagged according to the segment identification document. Example: campaign targeting "gender:male" only reaches users belonging to that segment.
-   Test campaign
-   Launch

## Segment Identification Document

The segment identification document is a CSV file identifying each unique targeting segment, allowing Ooyala Pulse to match the information coming from the data provider with targeting segments displayed to the ad ops user.

## CSV Row Format

Index, value, Category, Subcategory, Key Label, Value Label, Parameter Name, Parameter Value

-   Index is an integer between 0-99 identifying the segmentation key \(internal to Ooyala Ad Products\)
-   Value is an integer between 1-15 identifying the value \(internal to Ooyala Ad Solutions\)
-   Category, Subcategory and Key Label are labels of the segmentation key
-   Value Label is the label of the value
-   Parameter Name and Parameter Value are used to parse incoming requests

## Example

`"0","1","Intent","Finance","Move to flat","Intent to move","x","0"`

`"0","2","Intent","Finance","Move to flat","Affine","x","1"`

`"1","1","Demographics","Demographics","Gender","Female","g","u123"`

`"1","2","Demographics","Demographics","Gender","Male","g","u124"`

`"2","1","Demographics","Demographics","Age","21-30","a","1"`

`"2","2","Demographics","Demographics","Age","31-40","a","2"`

`"2","3","Demographics","Demographics","Age","41-50","a","3"`

`"2","4","Demographics","Demographics","Age","51-60","a","4"`

## Async Pixel Protocol

**Adding data**

Segments are transferred individually or in group according to the following protocol: `{Base URL}?{dataproviderid}={URL encoded, ampersand separated string of parameter names and values}`

|Data provider|My data platform|
|Data provider id|dmpMyData|
|Segments|”Gender:Female”,”Age:21-30”|
|String without URL encoding|g=u123;a=1|
|String with URL encoding|g%3Du123%3Ba%3D1|
|Base URL|http://myaccount.videoplaza.tv/proxy/pixel/v2?|
|Async pixel URL|http://myaccount.videoplaza.tv/proxy/pixel/v2?dmpMyData= g%3Du123%3Ba%3D1|

**Removing data**

Remove all data for a user by calling:

`{Base URL}?{dataproviderid}=DELETE`

## Ooyala Pulse UI

Target Audience segments using the new entity in the targeting rules box: ![Targeting Rules](../../image/pulse_campaign_targeting.png)

Start typing in order to select audience segments: ![Select the Audience Segments](../../image/pulse_audience_targeting_rules.png)

**User opt-out**

Users that have manually opted out from data targeting from our ad serving network will not be targeted even if they would technically match an audience segment.

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

