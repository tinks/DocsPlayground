# Client

Clients are advertisers, agencies, and brands. The Client endpoint allows you to create, update, delete, and list available clients.

To create or update a client, you need to supply a body to the request with the following format:

**Note:** All parameters are optional unless explicitly stated.

```
<clientBean>
    <comments>string</comments>
    <id>string</id>    <!-- Set only when updating a client -->
    <name>string</name>    <!-- Required -->
    <type>ADVERTISER|AGENCY|BRAND</type>    <!-- Required -->
    <email>string</email>
    <faxNumber>
        <countryCode>string</countryCode>
        <number>string</number>
    </faxNumber>              
    <phoneNumber>
        <countryCode>string</countryCode>
        <number>string</number>
    </phoneNumber>
    <postalAddress>
        <address1>string</address1>
        <address2>string</address2>
        <city>string</city>
        <country>string</country>
        <stateProvinceRegion>string</stateProvinceRegion>
        <zipCode>string</zipCode>
    </postalAddress>       
    <visitingAddress>
        <address1>string</address1>
        <address2>string</address2>
        <city>string</city>
        <country>string</country>
        <stateProvinceRegion>string</stateProvinceRegion>
        <zipCode>string</zipCode>
     </visitingAddress>
</clientBean>
```

## Create a Client

|Method|POST|
|URI path|/client|
|Matrix params|-|
|Query params|-|
|Content type|application/xml|
|XML Body|clientBean|
| | |
|*Returns*|client id|

**Example:**

*Request header:*

```
POST /api/1.0/client
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:*

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <clientBean>
        <name>The BMW company</name>
        <type>BRAND</type>
        <phoneNumber>
            <countryCode>+46</countryCode>
            <number>01234567</number>
    </phoneNumber>       
    </clientBean>
```

*Success response:*

```
HTTP status:
  200 (OK)

Body:
84a19c28-­ba66-­411b-­a5bf-­49ecfce1e607
```

## Delete a Client

|Method|DELETE|
|URI path|/client/by\_client\_id|
|Matrix params|id \[1\]|
|Query params|-|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
DELETE /api/1.0/client/by_client_id;id=84a19c28-­ba66-­411b-­a5bf-­49ecfce1e607
Host: api.videoplaza.com
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  204 (No Content)
```

## List All Clients

|Method|GET|
|URI path|/client|
|Matrix params|-|
|Query params|-|
| | |
|*Returns*|list of clients|

**Example:**

*Request header:*

```
GET /api/1.0/client
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
    <clientBean>
        <faxNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </faxNumber>
        <id>0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9</id>
        <name>IKEA</name>
        <phoneNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </phoneNumber>
        <postalAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </postalAddress>
        <type>BRAND</type>
        <visitingAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </visitingAddress>
    </clientBean>    
    <clientBean>
        <faxNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </faxNumber>
        <id>f16dd041-a659-4f7f-bf53-b7f1fcd84bee</id>
        <name>IKEA Centres Sverige AB</name>
        <phoneNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </phoneNumber>
        <postalAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </postalAddress>
        <type>ADVERTISER</type>
        <visitingAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </visitingAddress>
    </clientBean> 
    <clientBean>
        <faxNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </faxNumber>
        <id>3f01fedc-06fe-442e-a185-0a8e6433cd96</id>
        <name>Bowen Media</name>
        <phoneNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </phoneNumber>
        <postalAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </postalAddress>
        <type>AGENCY</type>
        <visitingAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </visitingAddress>
    </clientBean>       
</collection>

```

## List Client\(s\) by Id

|Method|GET|
|URI path|/client/by\_client\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of clients|

**Example:**

*Request header:*

```
GET /api/1.0/client/by_client_id;id=0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9
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
    <clientBean>
        <faxNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </faxNumber>
        <id>0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9</id>
        <name>IKEA</name>
        <phoneNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </phoneNumber>
        <postalAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </postalAddress>
        <type>BRAND</type>
        <visitingAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </visitingAddress>
    </clientBean>
</collection>

```

## List Clients by Campaign Id

|Method|GET|
|URI path|/client/by\_campaign\_id|
|Matrix params|id \[1...n\]|
|Query params|-|
| | |
|*Returns*|list of clients|

**Example:**

*Request header:*

```
GET /api/1.0/client/by_campaign_id;id=93a31e4e-2158-4f03-8839-66ffe62660d1
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
    <clientBean>
        <faxNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </faxNumber>
        <id>f16dd041-a659-4f7f-bf53-b7f1fcd84bee</id>
        <name>IKEA Centres Sverige AB</name>
        <phoneNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </phoneNumber>
        <postalAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </postalAddress>
        <type>ADVERTISER</type>
        <visitingAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </visitingAddress>
    </clientBean>
    <clientBean>
        <faxNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </faxNumber>
        <id>0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9</id>
        <name>IKEA</name>
        <phoneNumber>
            <countryCode>+44</countryCode>
            <number></number>
        </phoneNumber>
        <postalAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </postalAddress>
        <type>BRAND</type>
        <visitingAddress>
            <address1></address1>
            <address2></address2>
            <city></city>
            <country>GBR</country>
            <stateProvinceRegion></stateProvinceRegion>
            <zipCode></zipCode>
        </visitingAddress>
    </clientBean>
</collection>

```

## Update a Client

|Method|PUT|
|URI path|/client/by\_client\_id|
|Matrix params|id \[1\]|
|Query params|-|
|Content type|application/xml|
|XML Body|clientBean|
| | |
|*Returns*|-|

**Example:**

*Request header:*

```
PUT /api/1.0/client/by_client_id;id=0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9
Host: api.videoplaza.com
Content-­type: application/xml
X-VP-AUTH:"<your X-VP-AUTH key>"
```

*Request body:* NA

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <clientBean>
        <comments>IKEA Sweden, furniture store.</comments>
        <id>0d1d3dfb-359a-4ab9-bcf9-fb555b5accd9</id>
        <name>IKEA</name>
        <type>BRAND</type>
        <email/>
        <faxNumber>
            <countryCode>+46</countryCode>
            <number>87654321</number>
        </faxNumber>        
        <phoneNumber>
            <countryCode>+46</countryCode>
            <number>12345678</number>
        </phoneNumber>
        <postalAddress>
            <address1>Modulvägen 1, Kungens Kurva</address1>
            <address2/>            
            <city>Stockholm</city>
            <country>SWE</country>
            <stateProvinceRegion/>            
            <zipCode>141 75</zipCode>
        </postalAddress>
        <visitingAddress>
            <address1>Folkungavägen 50</address1>
            <address2/>             
            <city>Järfälla</city>
            <country>SWE</country>
            <stateProvinceRegion/>            
            <zipCode>177 35</zipCode>
        </visitingAddress>
    </clientBean>
```

*Success response:*

```
HTTP status:
  204 (No Content)
```

**Parent topic:**[Booking REST API Endpoints](../../../oadtech/ad_serving/dg/rest_booking_api_endpoints.md)

