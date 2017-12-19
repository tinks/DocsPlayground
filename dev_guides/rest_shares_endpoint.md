# Shares

Categories and Content Partners are different **share groups**. The groups have separate id’s that are account specific. Specific categories/sub-categories and specific content partners are referred to as **shares** in the Ooyala Pulse platform. When accessing a share, you need to supply both a share id and the corresponding share group id.

To create and update a share, you need to supply a body to the request with the following format:

**Note:** All parameters are optional unless explicitly stated.

```
<shareBean>
    <aliases>string</aliases>    <!-- None or multiple aliases, comma separated -->
    <customId>string</customId>
    <description>string</description>
    <discardDuplicateAliases>boolean</discardDuplicateAliases>
    <enabled>boolean</enabled>    <!-- Required -->
    <id>string</id>    <!-- Specific category/sub-category id or specific content partner id; set only when updating a share -->
    <name>string</name>    <!-- Required -->
    <overridesInsertionPolicies>boolean</overridesInsertionPolicies>    <!-- Defaults to false -->
    <parentId>string</parentId>    <!-- Parent category id; setting this value for content partners is ignored -->
    <shareGroupId>string</shareGroupId>    <!-- Account specific Category id or Content Partner id -->
    <unassigned>false</unassigned>    <!-- It should always be set to false -->
</shareBean>
```

## Get All Share Groups

|Method|GET|
|URI path|/share\_group|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|list of share groups \( the two predefined groups, Categories and Content Partners\)|

**Example:**

*Request header:*

```
GET /api/1.0/share_group
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
    <shareGroupBean>
        <id>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</id>
        <name>Sites</name>
        <type>CATEGORIES</type>
    </shareGroupBean>
    <shareGroupBean>
        <id>d041c497-06c8-415b-97cb-226522a72984</id>
        <name>Content partners</name>
        <type>CONTENT_PARTNERS</type>
    </shareGroupBean>
</collection>
```

## Create a Share

|Method|POST|
|URI path|/share|
|Matrix params|-|
|Query params|-|
|Content type|application/xml|
|Body|shareBean|
| | |
|*Returns*|share id|

**Example:**

*Request header:*

```
POST /api/1.0/share
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<shareBean>   
    <enabled>true</enabled>
    <name>Celebrity reality shows</name>   
    <parentId>dc74b090-c275-4646-a37f-4d5cff09997a</parentId>
    <shareGroupId>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</shareGroupId>    
</shareBean>
```

*Success response:*

```
HTTP status:
  200 (OK)

Body:
bb7047c5-5615-4912-93dd-9c10de4e19f5
```

## Update a Share

|Method|PUT|
|URI path|/share/by\_share\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|Body|share|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
PUT /api/1.0/share/by_share_id;id=bb7047c5-5615-4912-93dd-9c10de4e19f5
Host: api.videoplaza.com
Content-type: application.xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<shareBean>
    <aliases>celebrity,reality</aliases> 
    <customId>My custom id.</customId>  
    <description>All celebrity reality shows.</description>
    <discardDuplicateAliases>true</discardDuplicateAliases>
    <enabled>true</enabled>
    <id>bb7047c5-5615-4912-93dd-9c10de4e19f5</id>  
    <name>Celebrity Reality Shows</name>
    <overridesInsertionPolicies>true</overridesInsertionPolicies>
    <parentId>dc74b090-c275-4646-a37f-4d5cff09997a</parentId>
    <shareGroupId>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</shareGroupId>
    <unassigned>false</unassigned>
</shareBean>
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

## Delete a Share

|Method|DELETE|
|URI path|/share/by\_share\_id|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|-|

**Note:** You cannot delete an unnasigned share.

**Example:**

*Request header:*

```
DELETE /api/1.0/share/by_share_id;id=bb7047c5-5615-4912-93dd-9c10de4e19f5
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  204 (No Content)
```

## List All Shares by Share Group Id

|Method|GET|
|URI path|/share/by\_share\_group\_id|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|list of shares|

**Example:**

*Request header:*

```
GET /api/1.0/share/by_share_group_id;id=d041c497-06c8-415b-97cb-226522a72984
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
    <shareBean>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>44321757-3711-4c60-bacb-0a2c52dcd96f</id>
        <name>Fremantle Media</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <shareGroupId>d041c497-06c8-415b-97cb-226522a72984</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
    <shareBean>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>b4277b13-c0d5-4759-ad27-6baf2c8ca348</id>
        <name>Disney</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <shareGroupId>d041c497-06c8-415b-97cb-226522a72984</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
    <shareBean>
        <aliases>foodnetwork.com</aliases>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>a99b986d-758e-4cc7-a5e5-0e8c02002c5e</id>
        <name>Food Network</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <shareGroupId>d041c497-06c8-415b-97cb-226522a72984</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
    <shareBean>
        <aliases>cookingchanneltv</aliases>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>c8e3f7a4-d8a4-46e5-8b3a-dc2297413a46</id>
        <name>Cooking Channel TV</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <shareGroupId>d041c497-06c8-415b-97cb-226522a72984</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
    <shareBean>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>a76f6dfc-61a7-43b9-a003-4f0e47d6f496</id>
        <name>Unassigned</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <shareGroupId>d041c497-06c8-415b-97cb-226522a72984</shareGroupId>
        <unassigned>true</unassigned>
    </shareBean>
</collection>
```

## List All Shares by Name

|Method|GET|
|URI path|/share|
|Matrix params|-|
|Query params|name|
| | |
|*Returns*|list of shares|

**Note:** Entering part of a name, for example "cook", lists all shares in both share groups that start with "cook".

**Example:**

*Request header:*

```
GET /api/1.0/share?name=cook
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
    <shareBean>
        <aliases>cooking</aliases>
        <aliases>food</aliases>
        <aliases>kitchen</aliases>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>82534cde-c2fa-4ae4-947b-1bdd46e3d764</id>
        <name>Cooking show</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <parentId>dc74b090-c275-4646-a37f-4d5cff09997a</parentId>
        <shareGroupId>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
    <shareBean>
        <aliases>cookingchanneltv</aliases>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>c8e3f7a4-d8a4-46e5-8b3a-dc2297413a46</id>
        <name>Cooking Channel TV</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <shareGroupId>d041c497-06c8-415b-97cb-226522a72984</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
</collection>
```

## List All Shares by Id\(s\)

|Method|GET|
|URI path|/share/by\_share\_id|
|Matrix params|id \[1‐n\]|
|Query params|-|
| | |
|*Returns*|list of shares|

**Example:**

*Request header:*

```
GET /api/1.0/share/by_share_id;id=82534cde-c2fa-4ae4-947b-1bdd46e3d764
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
    <shareBean>
        <aliases>cooking</aliases>
        <aliases>food</aliases>
        <aliases>kitchen</aliases>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>82534cde-c2fa-4ae4-947b-1bdd46e3d764</id>
        <name>Cooking show</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <parentId>dc74b090-c275-4646-a37f-4d5cff09997a</parentId>
        <shareGroupId>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
</collection>
```

## List All Shares by Parent Id\(s\)

|Method|GET|
|URI path|/share/by\_parent\_id|
|Matrix params|id \[1-­n\]|
|Query params|-|
| | |
|*Returns*|list of shares|

**Example:**

*Request header:*

```
GET /api/1.0/share/by_parent_id;id=dc74b090-c275-4646-a37f-4d5cff09997a
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
    <shareBean>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>3f489e69-69af-4828-aa1b-bdd5ca8f0b4e</id>
        <name>Reality show</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <parentId>dc74b090-c275-4646-a37f-4d5cff09997a</parentId>
        <shareGroupId>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
    <shareBean>
        <aliases>cooking</aliases>
        <aliases>food</aliases>
        <aliases>kitchen</aliases>
        <discardDuplicateAliases>false</discardDuplicateAliases>
        <enabled>true</enabled>
        <id>82534cde-c2fa-4ae4-947b-1bdd46e3d764</id>
        <name>Cooking show</name>
        <overridesInsertionPolicies>false</overridesInsertionPolicies>
        <parentId>dc74b090-c275-4646-a37f-4d5cff09997a</parentId>
        <shareGroupId>8132a29c-d8fa-4bdf-82df-e72b197ed6f2</shareGroupId>
        <unassigned>false</unassigned>
    </shareBean>
</collection>
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

