# VAST Development

The VAST development topic provides information on how to do VAST development for iOS and Android apps, STBs, AS2 players, and so on.

## Background

Some environments do not support dynamically loaded code to be run within the application, for example, apps written for iOS/Android or some IPTV set top boxes, and so on. For those environments, we can use the more traditional VAST approach instead. Additionaly, the VAST approach is encouraged for some legacy environments that actually do support the loading of dynamic code but have too small a market to maintain a plugin \(for example, AS2 in Flash, the vast majority of the players out there uses AS3\).

VAST differs from the plugin approach on the following points:

-   You need to make one ad call for each "ad break" instead of one session-wide call
-   You need to connect the ad calls with an ID so that the ad server can see them as one call

Though this might seem like huge responsibilities put on you as a client side developer, it is quite easy to handle. What you need to be able to do to handle ads for a content item \(commonly video, but could as well be audio, game, and so on\) is basically the following:

1.  Create the pre-roll ad call. Include tt=p, and necessary targeting keywords and shares so that the ad server can return pre-rolls.
2.  Parse the VAST XML response and extract the information about the ads \(video source, impression/click-through track URLs\).
3.  Play the pre-roll ads and track the impressions. If user clicks on a pre-roll, open its corresponding click-through URL in a browser window if possible\).
4.  When the last pre-roll ad has been shown, start playing your content.
5.  If you reach a cue point for a mid-roll ad, create a new ad call using the same parameters as for the pre-roll ad call, but replace tt=p with tt=m.
6.  Pause your main content item, repeat the process of parsing and displaying ads, and resume your main content item when the last mid-roll has played.
7.  When you reach the end of your item, create a new ad call using the same parameters as above, but this time use tt=po.
8.  Repeat process of parsing and displaying ads.
9.  Session has ended.

## Requesting VAST Ads

The VAST format is only enabled for standard pre-roll, mid-roll and post-rolls. To fetch a VAST ad from Ooyala, add the query string parameter "rt=vast\_2.0" to your distributor ad request.

## The Ooyala Ad Request

**Request Parameters:**`http://[SUBDOMAIN]/proxy/distributor/v2?tt=[AD_TYPE]&t=[TAGS]&f=[FLAGS]&s=[CATEGORY,CONTENT_PARTNER]&rnd=[RANDOM]&rt=vast_2.0&tid=[TICKET_ID]&pid=[PERSISTENT_ID]`

The Ooyala ad request is made up of the following parts:

-   SUBDOMAIN: your unique Ooyala domain. Usually something like "cc-name.videoplaza.tv"
-   AD\_TYPE: one of p \(pre-roll\), m \(mid-roll\), po \(post-roll\), o \(overlay\)
-   TAGS: a comma separated string of tags describing the content
-   FLAGS: a comma separated string of predefined flags to disable one or more ad formats: nocom, noprerolls, nomidrolls or nopostrolls
-   CATEGORY & CONTENT\_PARTNER: a comma separated list of IDs or aliases. Maximum 1 category and 1 content partner.
-   RANDOM: a random string to disable caching
-   TICKET\_ID: a random UUID that connects different ad calls from the same session. A new UUID should be generated for each new video session, then reused throughout the session.
-   PERSISTENT\_ID: an UUID \(unique identifier\) that identifies the end user and lives cross sessions. This parameter should be generated the very first time an end user uses the player. The parameter should be stored and reused for every future sessions.
-   MAX LINEAR BREAK DURATION: when the time based breaks feature is enabled for your account, you can override or set the maximum duration in seconds for pre-, mid- and post-roll ad breaks by adding the `tbbl` parameter when requesting VAST ads, for example `tbbl=60`. Refer to [Ad Insertion Policies](../ug/ad_insertion_policies.md) for more information regarding time based breaks, where to set it and its limitations.

    **Note:** Adding the maximum linear break duration in an ad session request to Pulse sets the maximum duration for each linear break requested, even if no maximum duration was previously defined in the applicable ad insertion policy in Pulse.


**Example Request:**

http://se-showroom.videoplaza.tv/proxy/distributor/v2?tt=p&t=vast-example&f=&s=category\_id1,content\_partner\_id1&rnd=8170019078998&rt=vast\_2.0

**The VAST response**

Read more on the VAST standard [here](http://www.iab.net/vast).

Sample of inline VAST response:

```
<VAST version="2.0" xsi:noNamespaceSchemaLocation="http://service.videoplaza.com/schema/iab/vast-2.0.xsd">
    <Ad id="b16b5cd5-7133-4057-b58d-6dda5849afb4">
        <InLine>
            <AdSystem>Videoplaza Monetizer</AdSystem>
            <AdTitle>The VAST preroll</AdTitle>
            <Impression>
                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=0&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680
            </Impression>
            <Impression>http://example.com/123.gif?rnd=1302863942011</Impression>
            <Creatives>
                <Creative>
                    <Linear>
                        <Duration>00:00:30</Duration>
                        <TrackingEvents>
                            <Tracking event="start">
                                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=14&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680
                            </Tracking>
                            <Tracking event="firstQuartile">
                                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=15&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680
                            </Tracking>
                            <Tracking event="midpoint">
                                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=16&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680
                            </Tracking>
                            <Tracking event="thirdQuartile">
                                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=17&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680
                            </Tracking>
                            <Tracking event="complete">
                                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=18&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680
                            </Tracking>
                        </TrackingEvents>
                        <VideoClicks>
                            <ClickThrough>
                                http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=b16b5cd5-7133-4057-b58d-6dda5849afb4&e=20&t=3&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=-948245680&redirect=http%3A%2F%2Fwww.videoplaza.com%2Fdev-corner
                            </ClickThrough>
                        </VideoClicks>
                        <MediaFiles>
                            <MediaFile bitrate="434" delivery="progressive" height="270" scalable="true" type="video/x-flv" width="480">
                                http://se-showroom.cdn.videoplaza.tv/creatives/5524066b-7dfe-40f1-8a26-2e168286c77b.flv
                            </MediaFile>
                            <MediaFile bitrate="434" delivery="progressive" height="270" scalable="true" type="video/x-flv" width="480">
                                http://se-showroom.cdn.videoplaza.tv/creatives/f70029fa-a2fe-4b4b-8214-09af0484e331.flv
                            </MediaFile>
                        </MediaFiles>
                    </Linear>
                </Creative>
                <Creative>
                    <CompanionAds>
                        <Companion id="7703a45c-a9cf-4e6c-b982-ed5d2142b49a" height="250" width="300">
                            <HTMLResource>
                                <a href="http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=7703a45c-a9cf-4e6c-b982-ed5d2142b49a&e=92&t=5&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=1383858707&redirect=http%3A%2F%2Fwww.videoplaza.com" target="_blank" alt=""><img src="http://se-showroom.cdn.videoplaza.tv/creatives/8d7161c8-6e1b-487d-834a-9248cc14b912.jpg" width="300" height="250" border="0" /></a><img src='http://se-showroom.videoplaza.tv/proxy/tracker?sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee&a=7703a45c-a9cf-4e6c-b982-ed5d2142b49a&e=90&t=5&tags=vast&shares=share_id_1&tid=14351fb3-01b3-4898-96bf-ab332ca2f0bd&pid=87a0a41c-4929-43ec-b2d8-6095f53e6324&rnd=1383858707'/>
                            </HTMLResource>
                        </Companion>
                    </CompanionAds>
                </Creative>
            </Creatives>
            <Extensions>
                <Extension type="CustomTracking" name="Videoplaza Custom Ids"/>
            </Extensions>
        </InLine>
    </Ad>
</VAST>
```

Sample of VAST Wrapper response:

```
<VAST version="2.0" xsi:noNamespaceSchemaLocation="http://service.videoplaza.com/schema/iab/vast-2.0.xsd">
    <Ad id="2b582fcb-ef46-4978-be87-3b6ed34777e5">
        <Wrapper>
            <AdSystem>Videoplaza Monetizer</AdSystem>
            <VASTAdTagURI>http://agency.com/campaign-vast.xml</VASTAdTagURI>
            <Impression>
                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=0&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
            </Impression>
            <Creatives>
                <Creative id="2b582fcb-ef46-4978-be87-3b6ed34777e5">
                    <Linear>
                        <TrackingEvents>
                            <Tracking event="start">
                                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=14&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
                            </Tracking>
                            <Tracking event="firstQuartile">
                                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=15&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
                            </Tracking>
                            <Tracking event="midpoint">
                                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=16&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
                            </Tracking>
                            <Tracking event="thirdQuartile">
                                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=17&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
                            </Tracking>
                            <Tracking event="complete">
                                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=18&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
                            </Tracking>
                        </TrackingEvents>
                        <VideoClicks>
                            <ClickTracking>
                                http://vp-demo-jf.videoplaza.tv/proxy/tracker?sid=a5b895ef-941f-44d3-9ecc-4e1a9ef496b4&a=2b582fcb-ef46-4978-be87-3b6ed34777e5&e=20&t=3&tags=vasten&shares=&tid=375301a0-6c30-4e6d-b13f-94bf5c57c8ad&pid=27652101-0cd2-4903-bde3-de197f575866&rnd=1018724390
                            </ClickTracking>
                        </VideoClicks>
                    </Linear>
                </Creative>
            </Creatives>
            <Extensions>
                <Extension type="CustomTracking" name="Videoplaza Custom Ids"/>
            </Extensions>
        </Wrapper>
    </Ad>
</VAST>
```

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

