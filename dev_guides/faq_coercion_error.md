# Type Coercion Error when Initiating

I get a "Type Coercion" error when initiating the ad player.

exception, information=TypeError: Error \#1034: Type Coercion failed: cannot convert as3\_videoplaza\_bootloader@2e80d31 to com.videoplaza.api.VideoplazaBootLoaderWrapper

Make sure that you are creating the necessary Vp Wrappers and not casting objects to them.

**Example**

```
var vpBootLoader:VideoplazaBootLoaderWrapper = new VideoplazaBootLoaderWrapper(videoplaza);
```

and

```
var adPlayer:VpAdPlayerWrapper = new VpAdPlayerWrapper(vpBootLoader.createAdPlayer(conf));
```

instead of

```
var vpBootLoaderWrapper:VideoplazaBootLoaderWrapper = VideoplazaBootLoaderWrapper(videoplaza);
```

and

```
var adPlayer:VpAdPlayerWrapper = VpAdPlayerWrapper(vpBootLoader.createAdPlayer(conf));
```

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

