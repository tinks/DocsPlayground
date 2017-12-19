# How To Trigger Cue Points

**Note:** NB: This feature is still only available in the Flash SDK.

How do I trigger cue points myself, instead of letting the ad player handle them.

The ad player plugin keeps track of the player's current position and triggers cue points \(and in effect mid-roll breaks\) automatically, so you don't have to bother about it. However, if you want more control over when mid-rolls are triggered, you can take ownership of this event yourself by taking the steps below:

**Setup of adPlayer**

```
…
adPlayer.setAutoTriggerCuePoints(false);
…
```

**On new item**

```
…
itemInfo.cuePoints = [{name: "vpspot", time: 120}, {name: "vpspot", time: 240}]; // midroll breaks at seconds 120 and 240
…
adPlayer.setNewItem(itemInfo);
…
```

**To trigger cue point**

```
adPlayer.eventTriggered(AdTriggerType.OnCuePoint, {name: "vpspot", time: 120}); // to trigger the first break
```

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

