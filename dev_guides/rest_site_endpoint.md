# Site

The Site data endpoint describes your account with Ooyala.

## List Site Settings by Site Id

|Method|GET|
|URI path|/site/by\_site\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|siteSettingsBean, list of site settings for the given site|

**Example:**

*Request header:*

```
GET /api/1.0/site/by_site_id;id=ty72earb-­4c56-­4e46-­b351-­52a5ooa011an
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
<siteSettingsBean>
    <archiveAfter>14</archiveAfter>
    <availableFormatTypes>SEEKROLL</availableFormatTypes>
    <availableFormatTypes>COMPANION_BANNER</availableFormatTypes>
    <availableFormatTypes>PAUSE_AD</availableFormatTypes>
    <availableFormatTypes>PREROLL</availableFormatTypes>
    <availableFormatTypes>MIDROLL</availableFormatTypes>
    <availableFormatTypes>OVERLAY</availableFormatTypes>
    <availableFormatTypes>POSTROLL</availableFormatTypes>
    <availableFormats>preroll_pixeltracker</availableFormats>
    <availableFormats>midroll_standard</availableFormats>
    <availableFormats>overlay_imageset</availableFormats>
    <availableFormats>preroll_standard</availableFormats>
    <availableFormats>postroll_standard</availableFormats>
    <availableFormats>pause_ad</availableFormats>
    <availableFormats>postroll_pixeltracker</availableFormats>
    <availableFormats>companion_browser_flash</availableFormats>
    <availableFormats>overlay_splash</availableFormats>
    <availableFormats>midroll_interactive</availableFormats>
    <availableFormats>companion_browser_image</availableFormats>
    <availableFormats>companion_flash_flash</availableFormats>
    <availableFormats>preroll_interactive</availableFormats>
    <availableFormats>midroll_pixeltracker</availableFormats>
    <availableFormats>postroll_interactive</availableFormats>
    <availableFormats>seekroll</availableFormats>
    <availableFormats>overlay_site</availableFormats>
    <availableFormats>overlay_video</availableFormats>
    <availableFormats>companion_browser_3rdparty</availableFormats>
    <currency>USD</currency>
    <dateFormat>YYYYMMDD</dateFormat>
    <defaultCampaignPriority>5</defaultCampaignPriority>
    <defaultPageSize>15</defaultPageSize>
    <frontLoadFactor>30</frontLoadFactor>
    <id>ty72earb-­4c56-­4e46-­b351-­52a5ooa011an</id>
    <inventoryOverrideSettings>
        <entry>
            <key>SEEKROLL</key>
            <value>
                <inventory>0</inventory>
                <inventoryOverride>false</inventoryOverride>
                <overrideValue>0</overrideValue>
            </value>
        </entry>
        <entry>
            <key>COMPANION_BANNER</key>
            <value>
                <inventory>0</inventory>
                <inventoryOverride>false</inventoryOverride>
                <overrideValue>0</overrideValue>
            </value>
        </entry>
        <entry>
            <key>PAUSE_AD</key>
            <value>
                <inventory>0</inventory>
                <inventoryOverride>false</inventoryOverride>
                <overrideValue>0</overrideValue>
            </value>
        </entry>
        <entry>
            <key>PREROLL</key>
            <value>
                <inventory>74752</inventory>
                <inventoryOverride>true</inventoryOverride>
                <overrideValue>86400</overrideValue>
            </value>
        </entry>
        <entry>
            <key>MIDROLL</key>
            <value>
                <inventory>74625</inventory>
                <inventoryOverride>true</inventoryOverride>
                <overrideValue>86400</overrideValue>
            </value>
        </entry>
        <entry>
            <key>OVERLAY</key>
            <value>
                <inventory>0</inventory>
                <inventoryOverride>true</inventoryOverride>
                <overrideValue>86400</overrideValue>
            </value>
        </entry>
        <entry>
            <key>POSTROLL</key>
            <value>
                <inventory>74575</inventory>
                <inventoryOverride>true</inventoryOverride>
                <overrideValue>86400</overrideValue>
            </value>
        </entry>
    </inventoryOverrideSettings>
    <language>en_US</language>
    <nameTest Site</name>
    <subdomain>ts</subdomain>
    <tagAliasesAvailable>false</tagAliasesAvailable>
    <timeZone>Europe/Stockholm</timeZone>
    <vastEnabledByDefault>true</vastEnabledByDefault>
</siteSettingsBean>
```

## List Site Rules by Site Id

|Method|GET|
|URI path|/site/rule/by\_site\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|rulesBean, list of global targeting rules|

**Example:**

*Request header:*

```
GET /api/1.0/site/rule/by_site_id;id=ty72earb-­4c56-­4e46-­b351-­52a5ooa011an
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
    <frequencyCappings>
        <impressions>5</impressions>
        <timeUnit>WEEK</timeUnit>
    </frequencyCappings>
    <ignoreParentContentRules>false</ignoreParentContentRules>
    <ignoreParentFrequencyRules>false</ignoreParentFrequencyRules>
    <ignoreParentLocationRules>false</ignoreParentLocationRules>
    <ignoreParentTagRules>false</ignoreParentTagRules>
    <ignoreParentTimeRules>false</ignoreParentTimeRules>
    <locations>
        <allowed>false</allowed>
        <country>south africa</country>
        <id>710</id>
        <iso2>za</iso2>
        <locationType>COUNTRY</locationType>
    </locations>
    <parentId>301af24d-d8bf-4ddf-985a-c94cdf254ebb</parentId>
    <tags>
        <resourceId>violence</resourceId>
        <resourceName>violence</resourceName>
        <ruleType>NONE_OF</ruleType>
        <variableType>TAG</variableType>
    </tags>
</rulesBean>
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

