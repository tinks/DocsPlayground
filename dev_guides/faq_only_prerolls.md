# Pre-rolls Available, but no Mid-rolls or Overlays

## A1: You are probably not passing enough data in setNewItem method.

The ad session is initiated by calling

```
adPlayer.setNewItem(itemInfo);
```

The ItemInfo class has the following properies:

```
itemInfo.**tags**: Array of String values.
```

Use to pass keywords related to the item to Ooyala Pulse. Example: \["sport", "golf", "tiger woods"\]

```
itemInfo.**flags**: Array of String values.
```

Use to flag content as short or long form content, and/or to switch off certain ad formats \(eg \["long\_form"\] or \["short\_form"\]\). Required for the ad ops to be able to set different insertion policies in the backoffice for different content forms.

```
itemInfo.**cuePoints**: Array of Cue point objects.
```

The cuePoints Array identifies the ad breaks of the item. They have to have name = "vpspot" and time = position of ad break in seconds. Example: \[\{name: "vpspot", time: 30\}, \{name: "vpspot", time: 120\}\]. If you have no ad breaks for this item, pass an empty Array.

```
itemInfo.**duration**: Number (seconds).
```

Duration of item in seconds.

```
itemInfo.**timeReference**: ITimeReference.
```

The timeReference is used by the adPlayer to fetch the item's current play head position. The timeReference object can be any of your choice, but has to implement the ITimeReference interface, which has the read-only property time.

## How do I see that the correct values come through?

If you profile the http traffic \(using for example FireBug\), you should see an ad call similar to the one below being made:

```
http://service.videoplaza.com/proxy/distributor?**tags=summer,show\_one&cues=30,60&ct=194&flags=short\_form**&rnd=4696140726096&tt=preroll,overlay,midroll,postroll&rev=8523&tid=&sid=e8847228-0a6c-4715-bc71-b1a709c2e2ee
```

For this particular ad call, the following values were added to the itemInfo object:

```
tags = ["summer", "show_one"]; // descriptive keywords
cuePoints = [{name: "vpspot", time: 30},{name: "vpspot", time: 60}]; // two midroll breaks: at 30 and 60 seconds
duration = 194; // the item has a duration of 194 seconds
flags = ["short_form"]; // this item should be seen as short-form
```

## A2: The player state is probably not properly updated.

Make sure that you update the ad player on the player state every time it changes. This is done by calling

```
adPlayer.setPlayerState(PlayerState.<CURRENT_STATE>);
```

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

