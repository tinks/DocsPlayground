# Campaign

The Campaign endpoint allows you to create, update, delete, and list campaigns.

To create and update campaigns, you need to supply a body to the request with the following format:

**Note:** Only the name parameter is required. All other parameters are optional.

```
<campaignBean>
    <advertiserId>string</advertiserId>
    <agencyId>string</agencyId>
    <brandId>string</brandId>
    <budget>
        <value>number</value>
    </budget>
     <!-- <cpmHigh> (Setting this value is ignored)
        <value>number</value>
    </cpmHigh> -->
   <!-- <cpmLow> (Setting this value is ignored) 
        <value>number</value>
    </cpmLow> -->
    <customId>string</customId>
    <description>string</description>
    <enabled>boolean</enabled>    <!-- (Defaults to false) -->
    <!-- <end>2016-10-26T08:36:28</end> (Setting this value is ignored) -->
    <exclusive>boolean</exclusive>    <!-- (Defaults to false) -->
    <frontLoadFactor>0|10|20|30|40|50|60|70|80|90|100</frontLoadFactor>    <!-- (Defaults to match the global frontload setting) -->
    <goalTotal>number</goalTotal>
    <goalType>IMPRESSION|MIXED|SHARE_OF_VOICE</goalType>
    <id>string</id>    <!-- (Set only when updating a campaign) -->
    <includeInForecast>boolean</includeInForecast>    <!-- (Defaults to true) -->
    <name>string</name>    <!-- (Required) -->
    <priority>integer</priority>    <!-- (1-10; defaults to match the global priority setting) -->
    <!-- <start>2016-10-01T06:36:46+01:00</start> (Setting this value is ignored) -->
    <status>ACTIVE|RECENT|UPCOMING|ARCHIVED</status>    <!-- (The only valid value that can be set is ARCHIVED) -->
    <vastEnabled>boolean</vastEnabled>    <!-- (Defaults to false) -->
</campaignBean>
```

## Create a Campaign

|Method|POST|
|URI path|/campaign|
|Matrix params|-|
|Query params|-|
|Content type|application/xml|
|XML Body|campaignBean|
| | |
|*Returns*|campaign id|

**Example:**

*Request header:*

```
POST /api/1.0/campaign
Host: api.videoplaza.com
Content-type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
  <campaignBean>
        <advertiserId>f16dd041-a659-4f7f-bf53-b7f1fcd84bee</advertiserId>       
        <description>API test campaign.</description>
        <enabled>true</enabled>
        <exclusive>false</exclusive>
        <frontLoadFactor>20</frontLoadFactor>              
        <includeInForecast>false</includeInForecast>
        <name>API campaign</name>
        <priority>4</priority>        
        <vastEnabled>true</vastEnabled>
    </campaignBean>
```

*Success response:*

```
HTTP status:
  200 (OK)

Body:
84a19c28-­ba66-­411b-­a5bf-­49ecfce1e607
```

## Update a Campaign

|Method|PUT|
|URI path|/campaign/by\_campaign\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|XML Body|campaignBean|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
PUT /api/1.0/campaign/by_campaign_id;id=84a19c28-­ba66-­411b-­a5bf-­49ecfce1e607
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<campaignBean>
        <advertiserId>f16dd041-a659-4f7f-bf53-b7f1fcd84bee</advertiserId>
        <agencyId>3f01fedc-06fe-442e-a185-0a8e6433cd96</agency
        <brandId>0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9</brandId>
        <description>API test campaign.</description>
        <enabled>true</enabled>
        <exclusive>false</exclusive>
        <frontLoadFactor>40</frontLoadFactor>
        <id>84a19c28-­ba66-­411b-­a5bf-­49ecfce1e607</id>
        <includeInForecast>true</includeInForecast>
        <name>API Test Campaign</name>
        <priority>10</priority>        
        <vastEnabled>true</vastEnabled>
    </campaignBean>
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

## Delete a Campaign

|Method|DELETE|
|URI path|/campaign/by\_campaign\_id|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
DELETE /api/1.0/campaign/by_campaign_id;id=84a19c28-­bb66-­411b-­a5bf-­49efgfce1e607
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  204 (No Content)
```

## List All Campaigns

|Method|GET|
|URI path|/campaign|
|Matrix params|-|
|Query params|OPTIONAL1.  status:
    -   ACTIVE
    -   RECENT
    -   UPCOMING
2.  state:
    -   ARCHIVED
    -   DISABLED
    -   ENABLED

|
| | |
|*Returns*|list of campaigns|

**Example:**

*Request header:*

```
GET /api/1.0/campaign?status=upcoming&state=enabled
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  200 (OK)

Body:
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<collection>
    <campaignBean>
        <advertiserId>20020002-f299-489a-a9e1-362bfbe0c676</advertiserId>
        <enabled>true</enabled>
        <exclusive>false</exclusive>
        <frontLoadFactor>0</frontLoadFactor>
        <goalTotal>0.0</goalTotal>
        <id>c3abb649-e45f-4692-a467-083e9968af6b</id>
        <includeInForecast>true</includeInForecast>
        <name>Royco_2016_10</name>
        <priority>5</priority>
        <status>UPCOMING</status>
        <vastEnabled>true</vastEnabled>
    </campaignBean>
    <campaignBean>
        <advertiserId>664e3f55-3b89-4e2d-8635-5421716a00f7</advertiserId>
        <enabled>true</enabled>
        <exclusive>false</exclusive>
        <goalTotal>0.0</goalTotal>
        <id>f007aced-330c-4961-9da2-31527458bee5</id>
        <includeInForecast>true</includeInForecast>
        <name>Coca cola</name>
        <status>UPCOMING</status>
        <vastEnabled>true</vastEnabled>
    </campaignBean>
</collection>
```

## List Archived Campaigns

|Method|GET|
|URI path|/campaign/archived|
|Matrix params|-|
|Query params|1.  year \[0,1\] -­ number \(4 digits\)
2.  month \[0,1\] -­ number:
    -   1 \(January\)
    -   2 \(February\)
    -   3 \(March\)
    -   ...

|
| | |
|*Returns*|list of campaigns|

**Note:** Returns campaigns that were running during specified year and month. If no year or month is specified, archived campaigns for current year and/or month are returned.

**Example:**

*Request header:*

```
GET /api/1.0/campaign/archived?year=2016&month=8
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  200 (OK)

Body:
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<collection>
    <campaignBean>
        <advertiserId>f16dd041-a659-4f7f-bf53-b7f1fcd84bee</advertiserId>
        <cpmHigh>
            <value>4.9E-324</value>
        </cpmHigh>
        <cpmLow>
            <value>0.0</value>
        </cpmLow>
        <enabled>false</enabled>
        <end>2016-08-21T13:16:32+0200</end>
        <exclusive>false</exclusive>
        <goalTotal>250000.0</goalTotal>
        <goalType>IMPRESSION</goalType>
        <id>49428852-473d-4be8-a142-7abd85b7d9aa</id>
        <includeInForecast>true</includeInForecast>
        <name>IKEA_Sverige</name>
        <priority>5</priority>
        <start>2016-07-04T14:16:32+0200</start>
        <status>ARCHIVED</status>
        <vastEnabled>true</vastEnabled>
    </campaignBean>
    <campaignBean>
        <advertiserId>20020002-f299-489a-a9e1-362bfbe0c676</advertiserId>
        <agencyId>c9c72b46-4464-4ca8-aad4-6080b66f3318</agencyId>
        <brandId>d01b019f-0115-4384-a218-6b80c1bb803a</brandId>
        <cpmHigh>
            <value>4.9E-324</value>
        </cpmHigh>
        <cpmLow>
            <value>0.0</value>
        </cpmLow>
        <enabled>false</enabled>
        <end>2016-08-25T14:16:00+0200</end>
        <exclusive>false</exclusive>
        <goalTotal>74000.0</goalTotal>
        <goalType>IMPRESSION</goalType>
        <id>ce0e6dc2-feed-4711-96d2-1cb4992fd0cf</id>
        <includeInForecast>true</includeInForecast>
        <name>Royco_201607</name>
        <priority>2</priority>
        <start>2016-07-04T14:16:21+0200</start>
        <status>ARCHIVED</status>
        <vastEnabled>true</vastEnabled>
    </campaignBean>
    <campaignBean>
        <advertiserId>9692f005-7d78-4ec2-ba0c-0e6bff86c5ae</advertiserId>
        <cpmHigh>
            <value>4.9E-324</value>
        </cpmHigh>
        <cpmLow>
            <value>0.0</value>
        </cpmLow>
        <enabled>false</enabled>
        <end>2016-08-14T02:42:00+0200</end>
        <exclusive>false</exclusive>
        <goalTotal>52000.0</goalTotal>
        <goalType>IMPRESSION</goalType>
        <id>d1b89e0c-9528-4c1c-b233-ecaab0c99b82</id>
        <includeInForecast>true</includeInForecast>
        <name>Argos_storytelling_2016</name>
        <priority>3</priority>
        <start>2016-07-07T03:42:00+0200</start>
        <status>ARCHIVED</status>
        <vastEnabled>true</vastEnabled>
    </campaignBean>
</collection>
```

## List Campaign\(s\) by Id

|Method|GET|
|URI path|/campaign/by\_campaign\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of campaigns|

**Example:**

*Request header:*

```
GET /api/1.0/campaign/by_campaign_id;id=f007aced-330c-4961-9da2-31527458bee5
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  200 (OK)

Body:
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<collection>
    <campaignBean>
        <advertiserId>664e3f55-3b89-4e2d-8635-5421716a00f7</advertiserId>
        <enabled>true</enabled>
        <exclusive>false</exclusive>
        <goalTotal>0.0</goalTotal>
        <id>f007aced-330c-4961-9da2-31527458bee5</id>
        <includeInForecast>true</includeInForecast>
        <name>Coca cola</name>
        <status>UPCOMING</status>
        <vastEnabled>true</vastEnabled>
    </campaignBean>
</collection>
```

## List Notifications by Campaign Id

|Method|GET|
|URI path|/campaign/notification/by\_campaign\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|map \(key campaign id, value list of notifications\)|

**Example:**

*Request header:*

```
GET /api/1.0/campaign/notification/by_campaign_id;id=b67fd507-8e80-41f6-bdc2-3af60f058b7e
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  200 (OK)

Body:
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<map>
    <entry key="b67fd507-8e80-41f6-bdc2-3af60f058b7e">
        <notificationList>
            <notificationBeans>
                <concernedResource>
                    <id>59a0fc5f-d22b-40a2-ac72-264663c84c7e</id>
                    <type>GOAL</type>
                </concernedResource>
                <level>WARNING</level>
                <message>Running goal is missing active ads during some of its run time. (Royco_201607)</message>
                <relatedResources>
                    <id>b67fd507-8e80-41f6-bdc2-3af60f058b7e</id>
                    <type>CAMPAIGN</type>
                </relatedResources>
            </notificationBeans>
        </notificationList>
    </entry>
</map>
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

