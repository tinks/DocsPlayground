# Goal Rules

**Note:** There is a version 2 of the goal rules REST API endpoint. This endpoint complements the Booking API but it uses a different base URL and communication format. Capping the maximum number of impressions per 15 minutes, 30 minutes, and goal lifetime is only supported in version 2. For more information, refer to [Pulse Goal Rules REST API V2](http://community.ooyala.com/t5/Adtech-Knowledge-Articles/Pulse-Goal-Rules-REST-API-V2/ta-p/8926).

The Goal Rules endpoint allows you to list and update goal rules.

## List Goal Rules by Goal Id

|Method|GET|
|URI path|/goal/rule/by\_goal\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of rules|

**Example:**

*Request header:*

```
GET /api/1.0/goal/rule/by_goal_id;id=2b0d9c09-4256-448c-af54-a9d36596e5fb
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
<rulesBean>
    <content>
        <resourceId>0d828b6b-5753-47a9-9a72-8639765193b3</resourceId>
        <resourceName>News</resourceName>
        <ruleType>ALL_OF</ruleType>
        <variableType>SITE</variableType>
    </content>
    <ignoreParentContentRules>false</ignoreParentContentRules>
    <ignoreParentFrequencyRules>false</ignoreParentFrequencyRules>
    <ignoreParentLocationRules>false</ignoreParentLocationRules>
    <ignoreParentTagRules>false</ignoreParentTagRules>
    <ignoreParentTimeRules>false</ignoreParentTimeRules>
    <locations>
        <allowed>true</allowed>
        <country>finland</country>
        <id>246</id>
        <iso2>fi</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <parentId>2b0d9c09-4256-448c-af54-a9d36596e5fb</parentId>
</rulesBean>
```

## Update Goal Rules

|Method|PUT|
|URI path|/goal/rule/by\_goal\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|XML Body|rulesBean|
| | |
|*Returns*|-|

To update goal rules, you need to supply a body to the request with the following format:

```
<rulesBean>
    <parentId>string</parentId>    <!-- Goal id -->
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

-   **true**: override campaign targeting rules, meaning the goal applies its own targeting rules.
-   **false**: no targeting rules override, meaning the goal rules are merged with the parent rules.

For more information on targeting rules, refer to [Targeting Rules Overview](../ug/targeting_rules_overview.md).

**Example:**

*Request header:*

```
PUT /api/1.0/goal/rule/by_goal_id;id=2b0d9c09-4256-448c-af54-a9d36596e5fb
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<rulesBean>
    <parentId>2b0d9c09-4256-448c-af54-a9d36596e5fb</parentId>
    <content>
        <resourceId>0d828b6b-5753-47a9-9a72-8639765193b3</resourceId>
        <resourceName>News</resourceName>
        <ruleType>ALL_OF</ruleType>
        <variableType>SITE</variableType>
    </content>
    <frequencyCappings>
        <impressions>3</impressions>
        <timeUnit>DAY</timeUnit>
    </frequencyCappings>
    <locations>
        <allowed>true</allowed>
        <country>finland</country>
        <id>246</id>
        <iso2>fi</iso2>
        <locationType>COUNTRY</locationType>
    </locations>  
    <tags>
        <resourceId>entertainment</resourceId>
        <resourceName>entertainment</resourceName>
        <ruleType>ALL_OF</ruleType>
        <variableType>TAG</variableType>
    </tags>
    <tags>
        <resourceId>interior</resourceId>
        <resourceName>interior</resourceName>
        <ruleType>ALL_OF</ruleType>
        <variableType>TAG</variableType>
    </tags>
    <timeRestrictions>
        <active>true</active>
        <days>SUNDAY</days>
        <days>MONDAY</days>
        <days>TUESDAY</days>
        <days>WEDNESDAY</days>
        <days>THURSDAY</days>
        <days>FRIDAY</days>
        <days>SATURDAY</days>
        <fromHour>0</fromHour>
        <fromMinute>0</fromMinute>
        <toHour>23</toHour>
        <toMinute>59</toMinute>
    </timeRestrictions>
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

