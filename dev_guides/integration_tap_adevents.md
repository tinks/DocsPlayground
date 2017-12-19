# Tapping Into Ad Events

Tapping into ad event, for example,for 3rd party metric services and similar services.

## Introduction

If you have a metric service of some kind and want to log some events parallel to us, you can tap into our JS or AS APIs. This post describes how to listen for the events in AS or JS as well as the event structure and what events you should expect to receive.

**Note:** Due to a limitation in the Internet Explorer browser family, we require all embedded Flash players to include an object ID to enable our Flash plugin to communicate with our JavaScript API. Additionally, you should set the object param "allowScriptAccess" with the value "always".

For example:

```
<object id="flashObj" width="480" height="270">
    <param name="bgcolor" value="#FFFFFF" />
    <param name="allowFullScreen" value="true" />
    <param name="allowScriptAccess" value="always" />
    <embed src="..." bgcolor="#FFFFFF" ...></embed>
</object>
```

## Javascript

Create a JS event handler function that registers to videoplaza\_js\_support:

```
(function() {
    // Custom onEvent functionality. This js is dependent on vpsupport.js and needs to be loaded after it.
    var customEventHandler = function(event) {
        if (event.logEvent) {
            event = event.logEvent;
            //console.log("event", event);
            
            parseEvent(event);
            
            // if this is a dummy ad (has id == 0)
            if (event.ad.id == 0) {
                return;
            }
            
            // create the custom log url
            var customLogURL = "http://example.com/trackstuff?event=${eventType}&sid=${sid}&adno=${ad.id}&camp=${ad.cid}&loc=${escape(document.location.href)}&t=${new Date().getTime()}";
            
            var context = {
                ad: event.ad,
                sid: event.sid,
                eventType: String(event.type)
            };
            
            // add custom campaign id to url if available
            if (event.ad.hasOwnProperty("customcid")) {
                   context.customcid = event.ad.customcid;
                   customLogURL += "&cuscid=${customcid}"
            }
            
            // add custom goal id to url if available
            if (event.ad.hasOwnProperty("customgid")) {
                   context.customgid = event.ad.customgid;
                   customLogURL += "&cusgid=${customgid}"
            }
            
            // add custom ad id to url if available
            if (event.ad.hasOwnProperty("customid")) {
                   context.customid = event.ad.customid;
                   customLogURL += "&cusid=${customid}"
            }
            
            
            // replace the values in the track url with their corresponding values in context
            customLogURL = videoplaza_js_support.evalReplace(customLogURL, context); 
            
            // load the url
            // ... code to load customLogURL
        }
    };
    
    // register this event handler with Ooyala Ad Products
    videoplaza_js_support.registerEventHandler(customEventHandler);
})();
```

This event handler code must then be included as a JS plugin. Please ask your Technical Account Manager or refer to team-support@ooyala.com to get help with this step.

## Actionscript

In your bridge code, add an event listener to "vpOnEvent" \(VpEventType.ON\_EVENT\) and parse the information you need from the dispatched events:

```
...
adPlayer.addEventListener(VpEventType.ON_EVENT, onEvent);
...
...
private function onEvent(evt:Object):void {
  // get the logEvent
  var logEvent:Object = evt.getData().logEvent;
  // use the information you need within logEvent
  ...
}
```

## The logEvent Object

The structure of the logEvent Object looks as follows:

```
event: {
    type: "AdVideoStart",
    sid: "e8847228-0a6c-4715-bc71-b1a709c2e2ee",
    ad: {
        id: "3de589a4-e373-4183-8df0-b79c763dc4f7", // unique ad id
        customid: "val1=1234;val2=testvalue", // custom ad id values
        gid: "92e6deb0-7598-4193-9f2f-3bf2fa77f6e3", // unique goal id
        customgid: "valueone=one;valuetwo=2" // custom goal id values
        cid: "7d704894-4788-4d68-ae00-59fd43b3b1fb", // unique campaign id
        customcid: "this=that;that=this;five=six" // custom campaign id values 
        variant: "normal",
        flv: [object Object],
        ticket: {
            id: "a714b8d7-05c4-4af7-97f2-ebfca7f31011", // unique ad session ticket id. all ads during the same clip will have the same ticket id
            language: en_US,
            ticketType: "preroll",
            display: 20,
            pid: "667cdfc1-5659-461a-9b3c-27334773b4b3" // persistent user id. 
        },
        source: http://service.videoplaza.com/resources/preroll_standard,
        type: "preroll",
        parameters: [object Object]
    }
}
```

The most important values here are the following:

-   event.type: \(AdImpression, AdVideoStart, AdVideoFirstQuartile, AdVideoMidpoint, AdVideoThirdQuartile, AdVideoComplete - only video ads have the ..Video.. events\)
-   event.sid: your unique client id
-   event.ad.id, .gid, .cid
-   event.ad.customid, .customgid, .customcid
    -   This is a string with semi-colon \(;\) separated key/value pairs. Entered on campaign- goal- and/or ad level in Monetizer and can be for example ids to map the ad or campaign to your 3rd party metric system's ad or campaign ids.
-   event.ad.ticket.id
-   event.ad.ticket.pid
-   event.ad.type

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

