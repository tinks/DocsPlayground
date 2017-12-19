# Examples: Ad Requests

This page gives a few examples of using the Ad API endpoints for ads.

**Note:** Only successful responses are shown in the examples. Details about unsuccessful responses are found in the swagger documentation: [https://api.videoplaza.com/v1/swagger](https://api.videoplaza.com/v1/swagger).

## Request Body Format

To create or update ads, you need to supply a body to the request with the following format:

```
{
  "id": "<id of the ad>", (Only for the update request)
  "name": "Ad with asset",
  "goalId": "<Valid goal UUID>",
  "customId": "string", (Optional)
  "description": "string", (Optional)
  "enabled": false, (Optional, defaults to false)
  "weight": 40, (Optional, defaults to proportional split between ads in a goal)
  "creative": { (fields under the creative field depend on the type of creative)
    "type": "standard",
    "insertionPoint": "<preroll|midroll|postroll>",
    "assetId": "<fileId from /v1/assets>",
    "clickDestinationUri": "http://click-destination-uri.com" (Optional)
  },
  "start": "2016-04-01T10:05:23+01:00", (Optional, inherits from goal if not supplied)
  "end": "2016-04-02T10:05:23+01:00", (Optional, inherits from goal if not supplied)
  "externalTrackers": [ (Optional, you can provide multiple external trackers for an ad)
    {
      "url": "<URL>", 
      "event" : "<EVENT>"
    },
    {
      "url": "<URL>", 
      "event" : "<EVENT>"
    }
  ]
}
```

**Creative types**

We currently support the following `creative` types:

-   Standard spot ads \(pre-, mid- and post-rolls\): pass in the type of insertion point and the asset id:

    ```
    "creative": {
      "type": "standard",
      "insertionPoint": "<preroll|midroll|postroll>",
      "assetId": "<assetId>",
      "clickDestionationUri": "http://click-destination-uri.com" (Optional, to set the clickthrough URI)
    }
    ```

-   Third party ads: the asset is not stored in Ooyala Pulse, so you need to provide a URI for the location of the VAST ticket:

    ```
    "creative": {
      "type": "thirdparty",
      "vastUri": "http://vast-uri-example.com",
      "vpaidStrict": true, (Optional)
      "vpaidCountdown": false (Optional)
    }
    ```

-   Generic placeholder ads, where you do not specify the type of ad yet:

    ```
    "creative": {
      "type": "placeholder"
    }
    ```

-   Standard spot placeholder ads \(pre-, mid- and post-rolls\): pass in the type of insertion point, but you pass in the asset later:

    ```
    "creative": {
      "type": "spotPlaceholder",
      "insertionPoint": "<preroll|midroll|postroll>"
    }
    ```


**External tracking**

Ads can have multiple external trackers. The following tracking events are available:

```
IMPRESSION, CLICK_THROUGH, AD_START, AD_FIRST_QUARTILE, AD_MIDPOINT, AD_THIRD_QUARTILE, AD_COMPLETE, CLOSE, MUTE, UNMUTE, PAUSE, RESUME, REWIND, FULLSCREEN, EXPAND
```

## Creating Ads

**Example: create a pre-roll ad**

*Request header:*

```
POST /ads
Host: https://api.videoplaza.com/v1
Content-type: application/json
x-o-api-key="<your key>"
```

*Request body:*

```
{
  "name": "Test preroll ad with asset",
  "goalId": "fbda8a5d-5f32-4bc5-8b21-aff9f08c66ff",	
  "creative": {
    "type": "standard",
    "insertionPoint": "preroll",
    "assetId": "f345850f-38e6-47d1-9fe3-acca75bacea7"
  }
}
```

*Success response:*

```
HTTP status:
  201 (Created)

Header:
  Location: <URI to the location of the ad>

Body:
{
  "id": "315a133e-3c70-4b84-a237-7679d48064b6",
  "name": "Test preroll ad with asset",
  "goalId": "fbda8a5d-5f32-4bc5-8b21-aff9f08c66ff",
  "enabled": false,
  "creative": {
    "type": "standard",
    "insertionPoint": "preroll",
    "assetId": "f345850f-38e6-47d1-9fe3-acca75bacea7"
  },
  "externalTrackers": []
}
```

## Update Ads

**Note:** When updating ads, you must provide all fields set during creation, which you do not want to alter, again in the request body, otherwise these fields are unset and may inherit the settings from the goal the ad belongs to. For example, this applies to the start and end date of the ad.

**Example: update a pre-roll ad**

In this example, the ad's description changes and the ad is also enabled.

*Request header:*

```
PUT /ads
Host: https://api.videoplaza.com/v1
Content-type: application/json
x-o-api-key="<your key>"
```

**Note:** The ad id is not provided as a parameter in the URL, but it is a part of the body of the request.

*Request body:*

```
{
  "id": "315a133e-3c70-4b84-a237-7679d48064b6",
  "name": "Delicious perfume ad",
  "goalId": "fbda8a5d-5f32-4bc5-8b21-aff9f08c66ff",
  "enabled": true,	
  "creative": {
    "type": "standard",
    "insertionPoint": "preroll",
    "assetId": "f345850f-38e6-47d1-9fe3-acca75bacea7"
  }
}
```

*Success response:*

```
HTTP status:
  200 (OK)

Body:
{
  "id": "315a133e-3c70-4b84-a237-7679d48064b6",
  "name": "Delicious perfume ad",
  "goalId": "fbda8a5d-5f32-4bc5-8b21-aff9f08c66ff",
  "enabled": true,
  "creative": {
    "type": "standard",
    "insertionPoint": "preroll",
    "assetId": "f345850f-38e6-47d1-9fe3-acca75bacea7"
  },
  "externalTrackers": []
}
```

**Parent topic:**[Ad API](../../../oadtech/ad_serving/dg/rest_ad_api.md)

