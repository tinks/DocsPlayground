# Examples: Targeting Template Rules Requests

This page gives examples of using the Targeting Template API endpoints for getting and updating the rules of a targeting template.

## Get the Rules of a Targeting Template

**Example: Get the rules of the "Frequency Capping 5" targeting template**

*Request header:*

```
GET /api/2.0/targeting-template/053a4218-87c1-491d-83ac-6136abf0a866/rules HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)

Body:
{
  "locationRules": [],
  "tagAndPartnerRules": [],
  "categoryRules": [],
  "ipRules": [],
  "userAgentRules": [],
  "timeRules": [],
  "frequencyRules": [
    {
      "impressions": 5,
      "timeUnit": "CAMPAIGN_LIFETIME"
    }
  ],
  "audienceRules": {}
}
```

## Update the Rules Belonging to a Targeting Template

To update the rules of a targeting template, you need to supply a body to the request with the following format:

```
{
 "frequencyRules": [ FrequencyRuleBean... ],
 "locationRules": [ LocationRuleBean... ],
 "timeRules": [ TimeRuleBean... ],
 "tagAndPartnerRules": [ TagRuleBean or ContentPartnerRuleBean... ],
 "categoryRules": [ CategoryRuleBean... ],
 "ipRules": [ IpRuleBean... ],
 "userAgentRules": [ UserAgentRuleBean... ],
 "audienceRules": {"<audience data provider id>": AudienceSegmentRuleBean...} (Required only if you have an audience data integration added for your account)
  }
```

-   **FrequencyRule Bean**

    ```
    {
     "impressions": <number of impressions to allow in this time period>,
     "timeUnit": "QUARTER_HOUR" | "HALF_HOUR" | "HOUR" | "DAY" | "WEEK" | "MONTH" | "GOAL_LIFETIME" | "CAMPAIGN_LIFETIME"
      }
    ```

-   **LocationRuleBean**

    ```
     {
     "locationId": "<location id>",
     "locationType": "CITY" | "REGION" | "COUNTRY" ,
     "locationName": "Germany" | "Berlin" | ... ,
     "access": "ALLOW" | "DENY"
      }
    ```

    **Note:** "locationName" property can be skipped when saving. Ignored if provided.

-   **TimeRuleBean**

    ```
    {
     "active": true | false,
     "days": [ "MONDAY" | "TUESDAY" | "WEDNESDAY" | "THURSDAY" | "FRIDAY" | "SATURDAY" | "SUNDAY" , ... ],
     "fromHour": 0 - 23,
     "fromMinute": 0 - 59,
     "toHour": 0 - 23,
     "toMinute": 0 - 59
      }
    ```

-   **TagRuleBean**

    ```
    {
     "tag": "<tag  value>",
     "resourceType": "TAG",
     "ruleType": "ALL_OF" | "AT_LEAST_ONE_OF" | "NONE_OF"
      }
    ```

-   **ContentPartenrRuleBean**

    ```
    {
     "partnerId": "<content partner ID>",
     "partnerName": "<content partner name>",
     "resourceType": "CONTENT_PARTNER",
     "ruleType": "ALL_OF" | "AT_LEAST_ONE_OF" | "NONE_OF"
      }
    ```

    **Note:** "partnerName" property can be skipped when saving. Ignored if provided.

-   **CategoryRuleBean**

    ```
    {
     "categoryId": "<category ID>",
     "categoryName": "<category name>",
     "ruleType": "AT_LEAST_ONE_OF" | "NONE_OF"
      }
    ```

    **Note:**

    -   "ALL\_OF" is not allowed for categories.
    -   "categoryName" property can be skipped when saving. Ignored if provided.
-   **IpRuleBean**

    ```
    {
     "ipMatcher": "192.168.0.1" | "192.168.0.1-68" | "192.168.0.*",
     "access": "ALLOW" | "DENY"
      }
    ```

-   **UserAgentRuleBean**

    ```
    {
     "browsers": [ "IE" | "FIREFOX" | "CHROME" | "SAFARI" | "OPERA" | "OTHER" , ... ],
     "operatingSystems": [ "WINDOWS" | "MACOSX" | "LINUX" | "IOS" | "ANDROID" | "OTHER" , ... ],
     "access": "ALLOW" | "DENY"
      }
    ```

-   **AudienceSegmentRuleBean**

    **Note:** You can leave this part out if you do not use the **Pulse Audience Management** functionality and you do not have an audience data integration added for your account.

    ```
    {
     "segmentId": "<audience segment ID>[<index>]<value>",
     "segmentName": "<audience segment name>:<value name>",
     "ruleType": "ALL_OF" | "AT_LEAST_ONE_OF" | "NONE_OF"
      }
    ```

    **Note:** "segmentName" property can be skipped when saving. Ignored if provided.


**Example: Update the rules of the "Frequency Capping 5" targeting template**

*Request header:*

```
PUT /api/2.0/targeting-template/053a4218-87c1-491d-83ac-6136abf0a866/rules HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
Content-Type: application/json
Content-Length: 1713
```

*Request body:*

```
{
  "locationRules": [
    {
      "locationId": "124",
      "locationType": "COUNTRY",
      "locationName": "canada",
      "access": "ALLOW"
    },
    {
      "locationId": "840",
      "locationType": "COUNTRY",
      "locationName": "united states",
      "access": "ALLOW"
    }
  ],
  "tagAndPartnerRules": [
    {
      "resourceType": "TAG",
      "ruleType": "NONE_OF",
      "tag": "violence"
    }
  ],
  "categoryRules": [
    {
      "categoryId": "4d4ca496-4bd7-45a1-ae97-fa83a0e3faa3",
      "categoryName": "Entertainment",
      "ruleType": "AT_LEAST_ONE_OF"
    }
  ],
  "ipRules": [
    {
      "ipMatcher": "192.168.0.1-68",
      "access": "ALLOW"
    }
  ],
  "userAgentRules": [
    {
      "access": "ALLOW",
      "browsers": [
        "FIREFOX",
        "CHROME"
      ],
      "operatingSystems": [
        "WINDOWS",
        "MACOSX"
      ]
    }
  ],
  "timeRules": [
    {
      "active": true,
      "days": [
        "SUNDAY",
        "SATURDAY"
      ],
      "fromHour": 0,
      "fromMinute": 0,
      "toHour": 23,
      "toMinute": 59
    }
  ],
  "frequencyRules": [
    {
      "impressions": 5,
      "timeUnit": "CAMPAIGN_LIFETIME"
    }
  ],
  "audienceRules": {
    "4b621d55-219e-414b-abd4-045b23f69fa8": [
      {
        "segmentId": "4b621d55-219e-414b-abd4-045b23f69fa8[0]=2",
        "segmentName": "Gender:Female",
        "ruleType": "ALL_OF"
      },
      {
        "segmentId": "4b621d55-219e-414b-abd4-045b23f69fa8[1]=2",
        "segmentName": "Age:16-21",
        "ruleType": "ALL_OF"
      },
      {
        "segmentId": "4b621d55-219e-414b-abd4-045b23f69fa8[1]=3",
        "segmentName": "Age:21-29",
        "ruleType": "ALL_OF"
      }
    ]
  }
}
```

*Success response:*

```
HTTP status:
    204 (No Content)
```

**Parent topic:**[Targeting Template API](../../../oadtech/ad_serving/dg/rest_targeting_template_api.md)

