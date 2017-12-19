# Glossary

**Parent topic:**[Ooyala Pulse User Guide](../../../oadtech/ad_serving/ug/introduction.md)

## Ads:

-   **Asset**: the art work or file associated with a creative.
-   **Companion ads**: ads served along with linear or non-linear ads in the form of text, static image display ads, rich media, or skins that wrap around the video experience.
-   **Creative**: an advertising unit created by an ad designer, in accordance with publisher specifications and guidelines, for the purpose of communicating a marketing message to that publisher’s audience. One creative may consist of multiple files in various formats, such as standard images, animation, video, execution files \(.html, .js, etc.\) and other files that work together for an interactive experience.
-   **In-stream ads**: a generic term for video ad formats.
-   **Linear Ads**: ads that interrupt video content before \(pre-roll\), during \(mid-roll\), or after \(post-roll\) the streaming content. They can be accompanied by a companion ad, or they can include an interactive component.
-   **Mid-roll**: an ad that appears during the video content.
-   **Non-linear ads**: ads typically served as images that 'overlay' video content. The ad runs concurrently with the video content so the user sees the ad while also viewing the content without interruption. They can also be served with companion ads.
-   **Passback**: a backup ad source which is called upon in sequence until an ad is delivered or there are no more sources in the list. The player does not make any new requests to Pulse to get the passback ads, it is included in the original ad request.
-   **Post-roll**: an ad that appears after the video content finished playing.
-   **Pre-roll**: an ad that appears before the video content starts playing.
-   **Third party ad**: ad that comes from an external provider.

## Ad request

The event counted whenever your site requests ads to be displayed, even if no ads were returned.

## Break exclusivity

This means that an ad of the goal, if selected, is the only ad within the ad break. Break exclusive goals are only picked when they can run alone in a break. Exclusivity does not give the goal higher priority in any way. This allows clients to sell the opportunity to an advertiser of having the break completely or partially to oneself, and is something that a publisher can use to increase CPM.

## Content

Video content running in the player \(not the ad\).

## Cookies

For internet purposes, cookies are small text files downloaded to a user's computer that can be used to store user information and preferences. Many sites use cookies to customise and improve functionality on repeat visits to a site.

## Destination URL

The URL to which ads link. This is the page users see when they click through to an advertiser's site from an ad.

## Digital Video Standards:

-   **VAST**: Video Ad Serving Template, a universal XML schema for serving ads to digital video players. It is the standard for communication between ad servers and video players.
-   **VPAID**: Video Player Ad Interface Definition, industry standard for interactive in-stream video ads. VPAID defines a uniform run-time environment so that a compliant player can accept any compliant advertisement from any other party.

## Frontload

A feature intended to give you more manual control over the delivery pace which is otherwise completely controlled by Pulse's internal delivery algorithm \(which tries to deliver all campaigns evenly over time by forecasting future available inventory\). By using frontload, you can instruct Pulse that a certain share of a goal should be treated differently – served as soon as possible if there is spare room in current inventory that would otherwise be unused and wasted. For example, if a goal is booked to 100 000 impressions and the frontload is set to 30%, it means the goal should deliver 30,000 impressions "ahead of schedule". After 30,000 impressions are delivered, the goal slows down and starts to deliver as evenly as possible.

## Interactive metrics

Quantitative measurement of individual interaction events, for example:

-   **Accept Invitation**: number of times the user activated a control that launched an additional, often more engaging, creative portion of the ad.
-   **Close**: number of times the user removed the ad from the player in a way that it can not be re-displayed.
-   **Collapse**: number of times a user collapsed the ad either to its original size or to a different size. For overlays, this tracks the number of times the user minimizes the ad without fully removing it from the player.
-   **Expand**: number of times a user expanded the ad within the video player.
-   **Fullscreen**: number of times the ad played in full screen mode.
-   **Mute**: number of times the user clicked or otherwise activated the mute control during the ad.
-   **Pause**: number of times the user pressed pause or otherwise paused an ad.
-   **Resume**: number of times the user clicked or otherwise activated the resume control to re-start the ad.
-   **Rewind**: number of times the user clicked or otherwise activated the rewind control in order to move backwards along the ad's timeline.
-   **Unmute**: number of times the user clicked or otherwise activated the un-mute control during the ad.

## Metric

A quantitative measurement of data, for example:

-   **25% Ad completion**: first quartile, number of times the ad played to 25% of its length.
-   **50% Ad completion**: midpoint, number of times the ad played to 50% of its length.
-   **75% Ad completion**: third quartile, number of times the ad played to 75% of its length.
-   **100% Ad completion**: number of times the ad played to its completion.
-   **Ad started**: number of times the ad started playing.
-   **Click-throughs**: the total amount of clicks \(to the destination URL\) for a campaign during a specific time period.
-   **Completion rate**: percentage of times the video played to the end.
-   **Content start**: the start of the video content playback.
-   **CTR**: Click Through Rate. The number of clicks on an ad, divided by the number of impressions during a specific time period and expressed as a percentage.
-   **eCPM**: effective Cost Per Thousand or effective Cost Per Mille. A performance metric showing revenue generated from a thousand impressions of a particular advertisement. eCPM is calculated by dividing total earnings by total number of impressions in thousands.
-   **Fill rate**: the ratio of ad requests that are successfully filled \(used inventory\) in relation to the total number of ad requests made \(total inventory\), expressed as a percentage. It shows how much of your ad space has been rented out, and how much of it is standing empty. The higher the fill rate, the better. A high fill rate means you are satisfying advertiser's demand for ad space and that you are making money.
-   **Impression**: an event counted each time an ad request returns at least one ad to the site, meaning the ad was displayed in the player.
-   **Interactions**: an indication that the user interacted with the ad in some way during its display time, for example closed it, or clicked through to the destination page. Can only be triggered once per impression, but the individual events are still accounted for.
-   **Interaction rate**: the number of user interactions with the ad, divided by the number of impressions during a specific time period and expressed as a percentage.
-   **Inventory**: the amount of ad space a publisher has available to sell to an advertiser multiplied with the amount of ad views on the publisher's site, or site traffic, often calculated by the month.
-   **Revenue**: the amount of earnings for a specific time period.
-   **Time spent**: total display time of the ads in seconds or other appropriate time based unit.

## Pricing

-   **CPC**: Cost Per Click. The amount you earn each time a user clicks on your ad. The CPC for any ad is determined by the advertiser.
-   **CPM**: Cost Per Thousand or Cost Per Mille. The price of 1000 advertisement impressions on one webpage. If a website publisher charges $2 CPM, that means an advertiser must pay $2 for every 1000 impressions of its ad.

## Priority

Also referred to as 'prio', defines the importance of the campaigns/goals picked for delivery. Default value is 5, on a scale from 1‐10 where 1 is the most important. Setting a priority at goal level overrides any global or campaign priority settings.

## Pulse Audience Management \(PAM\)

A functionality which allows Pulse users to target 3rd party data directly through the Pulse platform once a data integration is added to the account.

-   **Audience data provider**: a provider of demographic data.
-   **Audience group**: a grouping of related segments, for example age, gender, or interests.
-   **Audience segment**: a specific segment of an audience, for example 10-27 years old, female, music lover, and so on.

## Share of Voice \(SOV\)

An ad revenue model that focuses on weight or percentage among other advertisers; used to represent the relative portion of ad inventory available to a single advertiser within a defined market over a specified time period. For example, if there are four advertisers on a website, each advertiser gets 25 percent of the advertising weight. SoV can be set at different percentages, for example one campaign getting 10%, one 20%, one 25%, and one 45%.

## Sponsor goal

Goal mode used for extra sponsor messages which guarantees a prime position directly after ad breaks in pre-rolls and mid-rolls and before post-roll ad breaks, meaning they are delivered closest to content. Sponsor goals act within their own sponsor break which means that the insertion policy for pre-rolls, mid-rolls, post-rolls and so on, is not affected by sponsors. For example, if you have set your pre-roll insertion policy to 3 pre-rolls and you book a sponsor, you first show 3 normal pre-rolls and then the sponsor goal. The sponsor goal mode only supports linear ads.

## Targeting

-   **DMA region**: Designated Market Area region, used by Nielsen Media Research to define a group of counties that form an exclusive geographic area in which the home market television stations hold a dominance of total hours viewed. There are 210 DMA regions, covering the entire continental United States, Hawaii, and parts of Alaska.
-   **Metro area**: the metropolitan area where your target viewers are located, comprised of the densely populated urban core and its less populated surrounding territories, sharing industry, infrastructure, and housing. Metro area targeting provides you with more precise targeting in case your business does not serve all regions or cities, or your advertising efforts focus on certain areas within a country.

## Tracking pixel

A 1×1 pixel-sized transparent image \(normally a GIF file\) inserted into an ad that provides information about an ad’s placement. In many cases, a tracking pixel is used to notify an ad tracking system that either an ad has been served \(or not served, in some cases\) or that a specific webpage has been accessed. Also known as: beacon, web beacon, action tag, redirect, and so on. Each time a viewer watches an ad associated with a tracking pixel, an HTTP request is made to the tracking pixel URL.

## Transcoding

The process of converting one compressed format to another.

## Wildcard

In computers, a symbol that has no particular meaning of its own so that its space can be filled by any real character that is necessary.

