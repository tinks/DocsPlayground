# Goal

The Goal endpoint allows you to create, update, delete, and list campaign goals.

To create or update a goal, you need to supply a body to the request with the following format:

**Note:** All parameters are optional unless explicitly stated.

```
<goalBean>
    <budget>
        <value>number</value>   
    </budget>
    <campaignId>string</campaignId>    <!-- Required -->
    <!-- <cpm> (Setting this value is ignored)
        <value>number</value>
    </cpm> -->
    <customId>string</customId>
    <description>string</description>
    <end>2016-09-29T03:49:45</end>
    <formatType>PREROLL|MIDROLL|POSTROLL|OVERLAY|COMPANION_BANNER|INSKIN|SPLASH|SEEKROLL|PAUSE_AD</formatType>    <!-- Defaults to PREROLL -->
    <frontLoadFactor>0|10|20|30|40|50|60|70|80|90|100</frontLoadFactor>    <!-- Defaults to match the global frontload setting or the campaign frontload setting if it overrides the global one -->
    <goalValue>number</goalValue>    <!-- Required; see note below for more information -->
    <id>string</id>    <!-- This should only be set when updating a goal -->
    <name>string</name>
    <priority>integer</priority>    <!-- 1-10; defaults to match the global priority setting or the campaign priority setting if it overrides the global one -->
    <start>2016-09-01T19:44:14</start>    <!-- Required -->
    <type>SHARE_OF_VOICE|IMPRESSION|UNLIMITED_IMPRESSION</type>    <!-- Required -->
    <unlimitedImpressions>boolean</unlimitedImpressions>
    <variant>NORMAL|BUMPER</variant>    <!-- Required --> 
</goalBean>
```

**Note:** Setting the goalValue parameter for unlimited impression goals is ignored. Valid values for goal types:

-   Share of voice goals: 0.01-1.0
-   Impression goals: any positive number

## Create a Goal

|Method|POST|
|URI path|/goal|
|Matrix params|-|
|Query params|-|
|Content type|application/xml|
|XML Body|goalBean|
| | |
|*Returns*|goal id|

**Example:**

*Request header:*

```
POST /api/1.0/goal
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<goalBean>     
        <campaignId>c3abb649-e45f-4692-a467-083e9968af6b</campaignId>
        <end>2016-10-30T00:00:00+0200</end>       
        <goalValue>30000.0</goalValue>        
        <name>Royco Midroll</name>
        <start>2016-09-30T00:00:00+0200</start>
        <type>IMPRESSION</type>
        <unlimitedImpressions>false</unlimitedImpressions>
        <variant>NORMAL</variant>
    </goalBean>

```

*Success response:*

```
HTTP status:
  200 (OK)

Body:
8e81973f-51f3-4769-9627-885546d7c450
```

## Update a Goal

|Method|PUT|
|URI path|/goal/by\_goal\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|XML Body|goalBean|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
PUT /api/1.0/goal/by_goal_id;id=8e81973f-51f3-4769-9627-885546d7c450
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <goalBean>
        <customId>My custom goal ID.</customId>
        <campaignId>c3abb649-e45f-4692-a467-083e9968af6b</campaignId>        
        <description>Changed the description for the impression goal through API.</description>
        <end>2016-10-30T00:00:00+0200</end>
        <formatType>MIDROLL</formatType>
        <frontLoadFactor>40</frontLoadFactor>
        <goalValue>50000.0</goalValue>
        <id>8e81973f-51f3-4769-9627-885546d7c450</id>
        <name>Royco Midroll</name>
        <priority>6</priority>
        <start>2016-09-30T00:00:00+0200</start>
        <type>IMPRESSION</type>
        <unlimitedImpressions>false</unlimitedImpressions>
        <variant>NORMAL</variant>
    </goalBean>
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

## Delete a Goal

|Method|DELETE|
|URI path|/goal/by\_goal\_id|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
DELETE /api/1.0/goal/by_goal_id;id=8e81973f-51f3-4769-9627-885546d7c450
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  204 (No Content)
```

## List Goal\(s\) by Id

|Method|GET|
|URI path|/goal/by\_goal\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of goals|

**Example:**

*Request header:*

```
GET /api/1.0/goal/by_goal_id;id=2b0d9c09-4256-448c-af54-a9d36596e5fb
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
    <goalBean>
        <budget>
            <value>0.0</value>
        </budget>
        <campaignId>c3abb649-e45f-4692-a467-083e9968af6b</campaignId>
        <cpm>
            <value>0.0</value>
        </cpm>
        <end>2016-10-30T00:00:00+0200</end>
        <formatType>POSTROLL</formatType>
        <goalValue>0.0</goalValue>
        <id>2b0d9c09-4256-448c-af54-a9d36596e5fb</id>
        <name>Royco Postroll</name>
        <start>2016-09-30T00:00:00+0200</start>
        <type>IMPRESSION</type>
        <unlimitedImpressions>false</unlimitedImpressions>
        <variant>NORMAL</variant>
    </goalBean>
</collection>
```

## List Goal\(s\) by Campaign Id

|Method|GET|
|URI path|/goal/by\_campaign\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of goals|

**Example:**

*Request header:*

```
GET /api/1.0/goal/by_campaign_id;id=c3abb649-e45f-4692-a467-083e9968af6b
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
    <goalBean>
        <budget>
            <value>0.0</value>
        </budget>
        <campaignId>c3abb649-e45f-4692-a467-083e9968af6b</campaignId>
        <cpm>
            <value>0.0</value>
        </cpm>
        <end>2016-10-30T00:00:00+0200</end>
        <formatType>POSTROLL</formatType>
        <goalValue>0.0</goalValue>
        <id>2b0d9c09-4256-448c-af54-a9d36596e5fb</id>
        <name>Royco Postroll</name>
        <start>2016-09-30T00:00:00+0200</start>
        <type>IMPRESSION</type>
        <unlimitedImpressions>false</unlimitedImpressions>
        <variant>NORMAL</variant>
    </goalBean>
    <goalBean>
        <budget>
            <value>0.0</value>
        </budget>
        <campaignId>c3abb649-e45f-4692-a467-083e9968af6b</campaignId>
        <cpm>
            <value>0.0</value>
        </cpm>
        <end>2016-10-30T00:00:00+0200</end>
        <formatType>PREROLL</formatType>
        <goalValue>30000.0</goalValue>
        <id>36597e76-1582-4983-8e44-8c3fec0f2a26</id>
        <name>Royco Sauce</name>
        <start>2016-09-30T00:00:00+0200</start>
        <type>IMPRESSION</type>
        <unlimitedImpressions>false</unlimitedImpressions>
        <variant>NORMAL</variant>
    </goalBean>
    <goalBean>
        <budget>
            <value>0.0</value>
        </budget>
        <campaignId>c3abb649-e45f-4692-a467-083e9968af6b</campaignId>
        <cpm>
            <value>0.0</value>
        </cpm>
        <end>2016-10-30T00:00:00+0200</end>
        <formatType>PREROLL</formatType>
        <goalValue>30000.0</goalValue>
        <id>d1e8ba62-72a3-41f4-8875-38d592b38570</id>
        <name>Royco Soup</name>
        <start>2016-09-30T00:00:00+0200</start>
        <type>IMPRESSION</type>
        <unlimitedImpressions>false</unlimitedImpressions>
        <variant>NORMAL</variant>
    </goalBean>
</collection>
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

