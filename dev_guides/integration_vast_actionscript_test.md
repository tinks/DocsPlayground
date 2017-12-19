# Test VAST 404 and Timeout Error Handling Using Actionscript 3

## Introduction

This article describes how to correctly error handle and test HTTP requests when using VAST in a custom video player. The two key concepts of this article are:

1.  Your player should always be able to display the video content in case Ooyala's servers are unavailable or timeout.
2.  Your player should not rely on the VAST response to initiate, play/pause, display the player controls, menus and other functionalities. Remember that a VAST response may be unavailable or turned on/off in some cases by the client.

## Prerequisites

1.  AS3 Video player
2.  Knowledge programming in AS3
3.  Charles Proxy or other Http tracker

**Example 404 Error Handling in AS3**

```
var loader:URLLoader = new URLLoader();
loader.addEventListener(HTTPStatusEvent.HTTP_STATUS, httpStatusHandler);

function httpStatusHandler(e:HTTPStatusEvent):void {
    trace("status: " + e.status);
    
    switch (e.status) {
        case 200:
            trace("request to server successful!");
            // load ad player
            break;
        case 404:
            trace("request return 404");
            //video player should proceed without ad player
            break;
        default:
            trace("request to server failed!");
            // video player should proceed without ad player
        break;
    }
}
```

**Example Timeout Error Handling in AS3**

```
var timeoutAmount:int = 3000; // wait 3 seconds

//load ad player
var myURLReq:URLRequest = new URLRequest();
var myURLLoader:URLLoader = new URLLoader();
myURLReq.url = "http://xx-companyName.videoplaza.tv/...";
myURLLoader.addEventListener(Event.COMPLETE, onURLLoaderComplete);

//add a timer to check for HTTP request timeout
loadTimer = new Timer(timeoutAmount);
loadTimer.addEventListener(TimerEvent.TIMER, onURLLoaderTimeout);
loadTimer.start();

private function onURLLoaderTimeout(e:TimerEvent):void {
    //start video player without ad player

    //abort ad player from loading if it takes more than 3 seconds
    myURLLoader.removeEventListener(Event.COMPLETE, onURLLoaderComplete);

    //remove timer
    loadTimer.stop();
    loadTimer.removeEventListener(TimerEvent.TIMER, loadTimerHandler);
    loadTimer = null;
}

private function onURLLoaderComplete(e:Event):void {
    //start ad player
 
    //remove timer
    loadTimer.stop();
    loadTimer.removeEventListener(TimerEvent.TIMER, loadTimerHandler);
    loadTimer = null;
}
```

**Important: The code examples in this page should be used only as guidelines. Implementation may vary depending on the player/framework you are using.**

## Testing Your Integration

You can use Charles Proxy or any other proxy debugging tool to fake 404 or timeout requests. If you have correctly implemented 404 and timeout error handling your player will always display the video content while performing these tests.

**404 Error Handling**

1.  Start Charles Proxy and click Tools \> Map Remote
2.  Map all requests from videoplaza to any 404 page, for example, http://www.google.com/404
3.  Press OK and start your video player

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

