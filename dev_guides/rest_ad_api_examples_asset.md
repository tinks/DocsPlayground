# Examples: Asset Requests

This page gives a few examples of using the Ad API endpoints for assets.

**Note:** Only successful responses are shown in the examples. Details about unsuccessful responses are found in the swagger documentation: [https://api.videoplaza.com/v1/swagger](https://api.videoplaza.com/v1/swagger).

## Uploading Assets

You have two options to upload assets, like ad images and ad videos, to Ooyala Pulse through the Ad API:

-   by providing a URL to the asset in the body of the request.
-   by providing the asset itself as an octet-stream in the body of the request.

**Example: providing a URL for the asset**

*Request header:*

```
POST /assets/uri
Host: https://api.videoplaza.com/v1
Content-type: application/json
x-o-api-key="<your key>"
```

*Request body:*

```
{
  "name":"file-name.mp4",
  "downloadUri":"http://example.com/video/1234"
}
```

**Note:** The `name` parameter in the body needs to contain the correct file extension for the asset.

*Success response:*

```
HTTP status:
  201 (created)

Header:
  Location: <URI with the location of your asset>
```

**Example: providing the serialised asset**

*Request header:*

```
POST /assets/file?fileName='filename.mp4'
Host: https://api.videoplaza.com/v1
Content-type: application/octet-stream
x-o-api-key="<your key>"
```

*Request body:*

```
<your asset as an octet-stream>
```

*Success response:*

```
HTTP status:
  201 (created)

Header:
  Location: <URI with the location of your asset>
```

## Retrieving Asset Metadata

To retrieve the metadata \(name and transcoding status\) for an asset, formulate a request as follows.

*Request header:*

```
GET /assets/<your asset's id>
Host: https://api.videoplaza.com/v1
Content-type: application/json
x-o-api-key="<your key>"
```

*Request body:* NA

*Success response:*

```
HTTP status:
  200 (OK)

Body:
{
  "name":"filename.mp4",
  "id":"<your asset's id>",
  "transcondingStatus":"<NOT_AVAILABLE|FAILED|INITIAL|UPLOADING|TRANSCODING|DOWNLOADING|FINISHED>"
}
```

**Note:** Transcoding does not start until the asset is linked to an ad.

**Parent topic:**[Ad API](../../../oadtech/ad_serving/dg/rest_ad_api.md)

