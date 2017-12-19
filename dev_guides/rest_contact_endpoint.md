# Contact

Contacts are contact details for clients. The contact endpoint allows you to create, update, delete, and list available contacts.

To create or update a contact, you need to supply a body to the request with the following format:

**Note:** All parameters are optional unless explicitly stated.

```
<contactBean>
    <description>string</description>
    <firstName>string</firstName>    <!-- Required -->
    <lastName>string</lastName>
    <id>string</id>    <!-- Set only when updating a contact -->
    <email>string</email>
    <faxNumber>
        <countryCode>string</countryCode>
        <number>string</number>
    </faxNumber>    
    <mobilePhoneNumber>
        <countryCode>string</countryCode>
        <number>string</number>
    </mobilePhoneNumber>
    <workPhoneNumber>
        <countryCode>string</countryCode>
        <number>string</number>
    </workPhoneNumber>
</contactBean>
```

## Create a Contact

|Method|POST|
|URI path|/contact|
|Matrix params|-|
|Query params|-|
|Content type|application/xml|
|XML Body|contactBean|
| | |
|*Returns*|contact id|

**Example:**

*Request header:*

```
POST /api/1.0/contact
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<contactBean>
    <description>CEO</description>
    <firstName>John</firstName>
    <lastName>Doe</lastName>
    <email>johndoe@ikea.com</email>
    <faxNumber>
        <countryCode>+46</countryCode>
        <number>87654321</number>
    </faxNumber>   
    <mobilePhoneNumber>
        <countryCode>+46</countryCode>
        <number>12345678</number>
    </mobilePhoneNumber>
    <workPhoneNumber>
        <countryCode>+46</countryCode>
        <number>11115555</number>
    </workPhoneNumber>
   </contactBean>
```

*Success response:*

```
HTTP status:
  200 (OK)

Body:
6d2d4fe9-c531-47ce-8581-e5bb0dfc9212
```

## Update a Contact

|Method|PUT|
|URI path|/contact/by\_contact\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|XML Body|contactBean|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
PUT /api/1.0/contact/by_contact_id;id=6d2d4fe9-c531-47ce-8581-e5bb0dfc9212
Host: api.videoplaza.com
Content-type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<contactBean>
    <description>CEO IKEA Sverige</description>
    <firstName>John</firstName>
    <lastName>Doe</lastName>
    <id>6d2d4fe9-c531-47ce-8581-e5bb0dfc9212</id>
    <email>johndoe@ikea.com</email>
    <faxNumber>
        <countryCode>+46</countryCode>
        <number>87654321</number>
    </faxNumber>   
    <mobilePhoneNumber>
        <countryCode>+46</countryCode>
        <number>12345678</number>
    </mobilePhoneNumber>
    <workPhoneNumber>
        <countryCode>+46</countryCode>
        <number>11115555</number>
    </workPhoneNumber>
   </contactBean>
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

## Associate a Contact with a Client

|Method|PUT|
|URI path|/contact/associate/by\_contact\_id|
|Matrix params|-|
|Query params|-|
|Content type|application/x-­www-­form-­urlencoded|
|Body|1.  contactId
2.  clientId

|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
PUT /api/1.0/contact/associate/by_contact_id
Host: api.videoplaza.com
Content-­type: application/x-­www-­form-­urlencoded
Content-Length: 50
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
contactId=6d2d4fe9-c531-47ce-8581-e5bb0dfc9212;clientId=0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

## Delete a Contact

|Method|DELETE|
|URI path|/contact/by\_contact\_id|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
DELETE /api/1.0/contact/by_contact_id;id=6d2d4fe9-c531-47ce-8581-e5bb0dfc9212
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  204 (No Content)
```

## List Contact\(s\) by Contact Id

|Method|GET|
|URI path|/contact/by\_contact\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of contacts|

**Example:**

*Request header:*

```
GET /api/1.0/contact/by_contact_id;id=dd24b869-d7cc-449d-a350-53c1312cf904
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
    <contactBean>
        <description>Chief Sales Officer</description>
        <email>janedoe@ikea.com</email>
        <faxNumber>
            <countryCode>+46</countryCode>
            <number>22226666</number>
        </faxNumber>
        <firstName>Jane</firstName>
        <id>dd24b869-d7cc-449d-a350-53c1312cf904</id>
        <lastName>Doe</lastName>
        <mobilePhoneNumber>
            <countryCode>+46</countryCode>
            <number>12345678</number>
        </mobilePhoneNumber>
        <workPhoneNumber>
            <countryCode>+46</countryCode>
            <number>11115555</number>
        </workPhoneNumber>
    </contactBean>
</collection>
```

## List Contact\(s\) by Client Id

|Method|GET|
|URI path|/contact/by\_client\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of contacts|

**Example:**

*Request header:*

```
GET /api/1.0/contact/by_client_id;id=f95936e0-­1977-­4222-­be68-­60ad90cec7d0
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
<contacts>
    <contacts clientId="f95936e0-­1977-­4222-­be68-­60ad90cec7d0">
        <contactList>
            <contacts>
                <description>CEO Royco.</description>
                <email>janedoe@royco.com</email>
                <faxNumber>
                    <countryCode>+44</countryCode>
                    <number>00006666</number>
                </faxNumber>
                <firstName>Jane</firstName>
                <id>7c94d869-0871-4db0-ab53-f8f08adca782</id>
                <lastName>Doe</lastName>
                <mobilePhoneNumber>
                    <countryCode>+44</countryCode>
                    <number>44448888</number>
                </mobilePhoneNumber>
                <workPhoneNumber>
                    <countryCode>+44</countryCode>
                    <number>11112222</number>
                </workPhoneNumber>
            </contacts>
        </contactList>
    </contacts>
</contacts>
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

