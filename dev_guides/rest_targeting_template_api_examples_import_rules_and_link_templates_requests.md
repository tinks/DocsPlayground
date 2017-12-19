# Examples: Import Rules from Targeting Templates and Link Targeting Templates Requests

This page gives examples of using the Targeting Template API endpoints for importing rules from a targeting template to a campaign or goal, linking targeting templates to a campaign or goal, and deleting that link.

## Import the Rules from the Specified Targeting Template into a Campaign or Goal

The rules of a targeting template can be imported into a campaign or goal by using the following query parameters:

-   **campaignId**: the id of the campaign to import the rules to
-   **goalId**: the id of the goal to import the rules to

**Example: import the rules from the "Frequency Capping 5" targeting template to a campaign**

*Request header:*

```
POST /api/2.0/targeting-template/053a4218-87c1-491d-83ac-6136abf0a866/import?campaignId=f7dacaa0-e3af-4f0e-b29d-87152a8c3cc5 HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    204 (No Content)
```

## Link a Targeting Template to a Campaign or Goal

**Example: link the "Frequency Capping 5" targeting template to a campaign**

*Request header:*

```
POST /api/2.0/targeting-template/053a4218-87c1-491d-83ac-6136abf0a866/link?campaignId=bbf0fc4b-c775-43aa-9b7a-d802167ccca0 HTTP/1.1
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
    204 (No Content)
```

## Delete the Link between a Targeting Template and a Campaign or Goal

**Example: delete the link between the "Frequency Capping 5" targeting template and a campaign**

*Request header:*

```
DELETE /api/2.0/targeting-template/053a4218-87c1-491d-83ac-6136abf0a866/link?campaignId=bbf0fc4b-c775-43aa-9b7a-d802167ccca0 HTTP/1.1
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

