# Campaign Rules

The Campaign Rules endpoint allows you to list and update campaign rules.

## Get Campaign Rules

|Method|GET|
|URI path|/campaign/rule/by\_campaign\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
| | |
|*Returns*|list of rules|

**Example:**

*Request header:*

```
GET /api/1.0/campaign/rule/by_campaign_id;id=c3abb649-e45f-4692-a467-083e9968af6b
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  200 (OK)

Body:
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<rulesBean>
    <frequencyCappings>
        <impressions>2</impressions>
        <timeUnit>DAY</timeUnit>
    </frequencyCappings>
    <ignoreParentContentRules>false</ignoreParentContentRules>
    <ignoreParentFrequencyRules>false</ignoreParentFrequencyRules>
    <ignoreParentLocationRules>false</ignoreParentLocationRules>
    <ignoreParentTagRules>false</ignoreParentTagRules>
    <ignoreParentTimeRules>false</ignoreParentTimeRules>
    <locations>
        <allowed>true</allowed>
        <country>norway</country>
        <id>578</id>
        <iso2>no</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <locations>
        <allowed>true</allowed>
        <country>sweden</country>
        <id>752</id>
        <iso2>se</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <parentId>c3abb649-e45f-4692-a467-083e9968af6b</parentId>
    <tags>
        <resourceId>violence</resourceId>
        <resourceName>violence</resourceName>
        <ruleType>NONE_OF</ruleType>
        <variableType>TAG</variableType>
    </tags>
    <timeRestrictions>
        <active>true</active>
        <days>SUNDAY</days>
        <days>SATURDAY</days>
        <fromHour>0</fromHour>
        <fromMinute>0</fromMinute>
        <toHour>23</toHour>
        <toMinute>59</toMinute>
    </timeRestrictions>
</rulesBean>
```

## Update Campaign Rules

|Method|PUT|
|URI path|/campaign/rules/by\_campaign\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|XML Body|rulesBean|
| | |
|*Returns*|-|

To update campaign rules, you need to supply a body to the request with the following format:

```
<rulesBean>
    <parentId>string</parentId>    <!-- Campaign id -->
    <content>
        <resourceId>string</resourceId>    <!-- Category id/Content Partner id/Tag value -->
        <!-- <resourceName>string</resourceName> (Category/Content Partner/Tag name; setting this value is ignored) -->
        <ruleType>ALL_OF|AT_LEAST_ONE_OF|NONE_OF</ruleType>
        <variableType>CONTENT_PARTNER|SITE|TAG</variableType>
    </content>
    <frequencyCappings>
        <impressions>integer</impressions>    <!-- Number of impressions to allow in this time period -->
        <timeUnit>HOUR|DAY|WEEK|MONTH</timeUnit>
    </frequencyCappings>
    <locations>
        <allowed>boolean</allowed>
        <!-- <country>string</country> (Name of the country; setting this value is ignored) -->
        <id>string</id>
        <iso2>string</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <locations>
        <allowed>boolean</allowed>
        <!-- <region>string</region> (Name of the region; setting this value is ignored) -->
        <id>string</id>
        <iso2>string</iso2>
        <locationType>REGION</locationType>
    </locations>
    <locations>
        <allowed>boolean</allowed>
        <!-- <city>string</city> (Name of the city; setting this value is ignored) -->
        <id>string</id>    <!-- Location id -->
        <iso2>string</iso2>
        <locationType>CITY</locationType>
    </locations>
    <timeRestrictions>    <!-- Time restrictions should be specified in the site's time zone -->
        <active>boolean</active>
        <days>MONDAY|TUESDAY|WEDNESDAY|THURSDAY|FRIDAY|SATURDAY|SUNDAY</days>        
        <fromHour>0-23</fromHour>
        <fromMinute>0-59</fromMinute>
        <toHour>0-23</toHour>
        <toMinute>0-59</toMinute>
    </timeRestrictions>
    <tags>
        <resourceId>string</resourceId>    <!-- Category id/Content Partner id/Tag value -->
        <!-- <resourceName>string</resourceName> (Category/Content Partner/Tag name; setting this value is ignored) -->
        <ruleType>ALL_OF|AT_LEAST_ONE_OF|NONE_OF</ruleType>
        <variableType>CONTENT_PARTNER|SITE|TAG</variableType>
    </tags>
    <ignoreParentContentRules>boolean</ignoreParentContentRules>
    <ignoreParentFrequencyRules>boolean</ignoreParentFrequencyRules>
    <ignoreParentLocationRules>boolean</ignoreParentLocationRules>
    <ignoreParentTagRules>boolean</ignoreParentTagRules>
    <ignoreParentTimeRules>boolean</ignoreParentTimeRules>
</rulesBean>
```

**Note:** The ignoreParentRules parameters can be set to:

-   **true**: override global targeting rules, meaning the campaign applies its own targeting rules.
-   **false**: no targeting rules override, meaning the campaign rules are merged with the parent rules.

For more information on targeting rules, refer to [Targeting Rules Overview](../ug/targeting_rules_overview.md).

**Example:**

*Request header:*

```
PUT /api/1.0/campaign/rules/by_campaign_id;id=c3abb649-e45f-4692-a467-083e9968af6b
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<rulesBean>
    <parentId>c3abb649-e45f-4692-a467-083e9968af6b</parentId>
    <content>
        <resourceId>dc74b090-c275-4646-a37f-4d5cff09997a</resourceId>
        <resourceName>Entertainment</resourceName>
        <ruleType>AT_LEAST_ONE_OF</ruleType>
        <variableType>SITE</variableType>
    </content>
    <content>
        <resourceId>df5480fd-ca38-43c8-a44c-4240965e2023</resourceId>
        <resourceName>Sport</resourceName>
        <ruleType>AT_LEAST_ONE_OF</ruleType>
        <variableType>SITE</variableType>
    </content>
    <frequencyCappings>
        <impressions>2</impressions>
        <timeUnit>DAY</timeUnit>
    </frequencyCappings>
    <locations>
        <allowed>true</allowed>
        <country>norway</country>
        <id>578</id>
        <iso2>no</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <locations>
        <allowed>true</allowed>
        <country>sweden</country>
        <id>752</id>
        <iso2>se</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <locations>
        <allowed>false</allowed>
        <country>iceland</country>
        <id>352</id>
        <iso2>is</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <timeRestrictions>
        <active>true</active>
        <days>SUNDAY</days>
        <days>SATURDAY</days>
        <fromHour>0</fromHour>
        <fromMinute>0</fromMinute>
        <toHour>23</toHour>
        <toMinute>59</toMinute>
    </timeRestrictions>
    <tags>
        <resourceId>violence</resourceId>
        <resourceName>violence</resourceName>
        <ruleType>NONE_OF</ruleType>
        <variableType>TAG</variableType>
    </tags>
    <ignoreParentContentRules>true</ignoreParentContentRules>
    <ignoreParentFrequencyRules>true</ignoreParentFrequencyRules>
    <ignoreParentLocationRules>true</ignoreParentLocationRules>
    <ignoreParentTagRules>true</ignoreParentTagRules>
    <ignoreParentTimeRules>true</ignoreParentTimeRules>   
</rulesBean>
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

