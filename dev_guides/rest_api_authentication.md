# Authentication

Every use of Ooyala Pulse REST APIs requires authentication, ensuring that only authorised users interact with Ooyala Pulse content.

## Booking, Reporting, Targeting Template, and Forecasting API Authentication

To access these APIs Ooyala provides you with **login credentials**; a username and password, which are the same as the ones you use to access the Ooyala Pulse user interface.

Your first request is a request for access to the system. You achieve this with an HTTP POST and supplying login credentials in the body. The response is an HTTP status code 302, which contains an authentication key header **X-VP-AUTH**. Use this parameter in the future by adding the 'X-VP-AUTH' as a header to all of the requests.

**Note:** The header is renewed during the session. Make sure that you follow any "Set-Cookie" in your responses.

**Example Request**

```
POST /login_process
Host: api.videoplaza.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 50

username=myLoginName&password=myPassword
```

**Example Response HTTP header**

```
Set-Cookie: X-VP-AUTH="fSUqgVBECZx6mtvhbwZbrFWm3VNg+gkxVCO14LAQGZ1lLhGvXJeD9aPPAaIWZb/fdgjk5454+OzObaqtbksRCQf4I5F8NWDqFAlysfgfg3eDt/KJbmRJsLd8qw4"; Version=1; Max-Age=3600; Expires=Wed, 08-Feb-2012 14:41:05 GMT; Path=/
```

## Ad Api Authentication

To access the Ad API, Ooyala provides you with an **API key**. An API Key is your secret and permanent \(one time\) key, which should be included in each request as the **x-o-api-key** in the header.

**Example Request**

```
GET /ads/0a6dc27d-06d9-41aa-b360-ff279b7e316a
Host: https://api.videoplaza.com/v1
x-o-api-key:"AGZNQFCXKUTEZRUTIPYSXORGJDLU2QZVJRIVKRSRKM3VGOKKJMYEMVJSJNATCNSBKRFUUUSLIVHDGOCHHFLFGTBQG4ZVARKTGJBTMMZYKI3E2H9"
```

**Parent topic:**[Ooyala Pulse REST API](../../../oadtech/ad_serving/dg/ad_serving_api.md)

