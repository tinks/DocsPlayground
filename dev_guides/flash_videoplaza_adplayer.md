# What is the Ooyala Flash Ad Player?

## The Ooyala Flash Ad Player

The Ooyala Flash Ad Player can be seen as an intelligent display object that can be resized and positioned any way you want, and then informed of the metadata for the content item that is to be monetised. The Ad Player is loaded by the bridge class and contains all the code necessary to load and display ads. The Ad Player contains its own video player, so your player never needs to worry about playing video ads. It will also interact with your video player when necessary, for example when pausing the player to display an ad.

## The Session

The session is an interactive information exchange between your video player and the Ooyala Ad Player. It is initiated when a user clicks the play button on your video player \(or when the video starts playing automatically if auto-play is enabled\), and finishes after the last ad has been shown. Ooyala Ad Products typically makes one session-wide ad call \(or two depending on how your player retrieves clip metadata from the CDN\), whose response will contain all ads to be shown for the specific video clip in the viewing session \(pre-rolls, mid-rolls, post-rolls, overlays, companion banners, and so on\).

**Parent topic:**[Phase 1 - Introduction to Ad Serving \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase1.md)

