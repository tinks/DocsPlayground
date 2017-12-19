# Examples: Targeting Template Requests

This page gives examples of using the Targeting Template API endpoints for getting information about targeting templates, as well as listing, updating, deleting, and creating targeting templates.

## Get Usage Information for Targeting Templates

*Request header:*

```
GET /api/2.0/targeting-template/usage HTTP/1.1
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
  "active": 5,
  "max": 10,
  "messageTitle": "", (Value provided when you reach template limit)
  "messageBody": ""   (Provides information and instructions when you reach template limit)
}
```

## List Existing Targeting Templates

The list of all existing targeting templates can be filtered by using the following query parameters:

-   **campaignId**: only lists templates linked to the corresponding campaign
-   **goalId**: only lists templates linked to the corresponding goal

**Example: List all existing targeting templates**

*Request header:*

```
GET /api/2.0/targeting-template HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)

Body:
[
  {
    "id": "053a4218-87c1-491d-83ac-6136abf0a866",
    "name": "Frequency capping 5",
    "siteId": "<id of your site>",
    "created": "2016-03-22T14:34:40.000+0000"
  },
  {
    "id": "fef506b4-d304-4bfc-986c-40a0b30155b1",
    "name": "Geotargeting-Volvo",
    "siteId": "<id of your site>",
    "created": "2016-03-22T14:33:22.000+0000"
  },
  {
    "id": "b0fd3da7-8452-456c-9642-99e34253f0de",
    "name": "Local",
    "siteId": "<id of your site>",
    "created": "2016-03-14T15:17:29.000+0000"
  },
  {
    "id": "4903058d-8a06-4ba1-b74d-16dcf3c134e9",
    "name": "Mobile",
    "siteId": "<id of your site>",
    "created": "2016-03-21T10:28:08.000+0000"
  },
  {
    "id": "f940b752-bdce-44d1-9917-072a2863f7cc",
    "name": "Sport",
    "siteId": "<id of your site>",
    "created": "2016-03-14T15:16:48.000+0000"
  }
]
```

**Example: List targeting templates linked to a specific campaign**

*Request header:*

```
GET /api/2.0/targeting-template?campaignId=f7dacaa0-e3af-4f0e-b29d-87152a8c3cc5 HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    200 (OK)

Body:[
  {
    "id": "053a4218-87c1-491d-83ac-6136abf0a866",
    "name": "Frequency capping 5",
    "siteId": "<id of your site>",
    "created": "2016-03-22T14:34:40.000+0000"
  }
]
```

## Get information about a targeting template

**Example: Get information about the "Frequency capping 5" targeting templates**

*Request header:*

```
GET /api/2.0/targeting-template/053a4218-87c1-491d-83ac-6136abf0a866 HTTP/1.1
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
  "id": "053a4218-87c1-491d-83ac-6136abf0a866",
  "name": "Frequency capping 5",
  "siteId": "<id of your site>",
  "created": "2016-03-22T14:34:40.000+0000"
}

```

## Create a new targeting template

To create a new targeting template, you need to supply a body to the request with the following format:

```
{
  "name": "string" (The name of the targeting template)
}
```

**Note:** This creates an empty template. To set the rules of a template, you need to do a PUT request. For more information and examples, see [Update the Rules Belonging to a Targeting Template](rest_targeting_template_api_examples_template_rules_requests.md#update_template_rules).

**Example: Create a targeting template called "New template"**

*Request header:*

```
POST /api/2.0/targeting-template HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
Content-Type: application/json
Content-Length: 24
```

*Request body:*

```
{
"name": "New template"
}
```

*Success response:*

```
HTTP status:
    200 (OK)
 
Body:
{
  "id": "08865183-b228-4d47-aa8f-ca00a6ba54a6",
  "name": "New template",
  "siteId": "<id of your site>",
  "created": "2016-06-23T10:21:13.007+0000"
}

```

**Note:** If you have already reached the maximum number of targeting templates and try to create a new template, you see the following:

*Success response:*

```
HTTP status:
  403 (Forbidden)

Body:
{
  "type": "ForbiddenError",
  "message": "You have used 5 (100%) of your 5 templates. Please remove obsolete templates in order to create new ones."
}
```

## Update a Targeting Template

**Note:** Only the name of the targeting template can be changed.

To update a targeting template, you need to supply a body to the request with the following format:

```
{
  "id": "string", (The id of the targeting template you want to update)
  "name": "string", (The new name of the targeting template)
  "siteId": "string" (The ID of your site)
}
```

**Example: Change targeting template name from "New template" to "My new targeting template"**

*Request header:*

```
PUT /api/2.0/targeting-template/08865183-b228-4d47-aa8f-ca00a6ba54a6 HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
Content-Type: application/json
```

*Request body:*

```
{
  "id": "08865183-b228-4d47-aa8f-ca00a6ba54a6",
  "name": "My new targeting template",
  "siteId": "<id of your site>"
}
```

*Success response:*

```
HTTP status:
    204 (No Content)
```

## Delete a Targeting Template

**Example: Delete "My new targeting template"**

*Request header:*

```
DELETE /api/2.0/targeting-template/08865183-b228-4d47-aa8f-ca00a6ba54a6 HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    204 (No Content)
```

**Parent topic:**[Targeting Template API](../../../oadtech/ad_serving/dg/rest_targeting_template_api.md)

