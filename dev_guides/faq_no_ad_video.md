# How to Avoid Ads on Certain Content

## I have a custom player

Use the [flags](integration_tags_flags.md) property on the ItemInfo class.

Example:

```
...
itemInfo.flags = ["nocom"];
...
adPlayer.setNewItem(itemInfo);
...
```

## I have a pre-integrated player

In the integration, at the same location that you provided your vpDomain, you need to add the flags variable with the appropriate flag.

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

