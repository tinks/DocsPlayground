# Parse and Test VAST Using Actionscript 3

## Introduction

This article describes how to parse VAST XML node elements in the video player. You should be familiar with the VAST standard before reading this article, please visit iab website at [http://www.iab.net/vast](http://www.iab.net/vast) and read the VAST Template Guidelines. You should also be aware that VAST XML templates are dynamic documents were XML nodes may have from 0~N number of elements. The key concepts of this article are:

1.  Understanding how to parse the VAST XML
2.  How to handle errors, timeouts and empty responses
3.  How to test a video player's VAST integration

## Prerequisites

1.  AS3 Video player
2.  Knowledge programming in AS3
3.  Charles Proxy or other Http tracker

## Example 404 and Timeout Error Handling in AS3

See this page: [Test VAST 404 and Timeout Error Handling Using Actionscript 3](integration_vast_actionscript_test.md#)

## Example VAST Parsing in AS3

You can use this [example VAST ticket](http://vp-validation.videoplaza.tv/proxy/distributor?tt=preroll&tags=standard&shares=validation&rnd=8170019078998&accepts=vast_2.0) \(2 pre-roll ads\).

```
// 1. retrieve the VAST document
var xmlLoader:URLLoader = new URLLoader();
xmlLoader.load(new URLRequest("http://vast.xml"));

xmlLoader.addEventListener(Event.COMPLETE, init);
xmlLoader.addEventListener(IOErrorEvent.IO_ERROR, ioErrorHandler);

private function ioErrorHandler(event:IOErrorEvent):void {
  trace("ioErrorHandler: " + e);
//start video player without ads
}

// 2. parse VAST xml document into usable properties 
private function init(e:Event):void {

var Ad_array:Array = new Array();
try {
 var myXML:XML = XML(e.target.data);
} catch(e:Error) {
 trace('xml element is undefined ' + e);
 //start video player without ads
}

//get all ads in the VAST document
for (var i:int = 0; i < myXML.Ad.length(); i++) {

 //get all parameters for each ad
 ad_array[i] = new Object();
 ad_array[i].id = myXML.Ad[i].attribute("id") ? myXML.Ad[i].attribute("id").text() : trace('id is undefined');
 ad_array[i].impression = get_All_xml_nodes(myXML.Ad.InLine.Impression);
 ad_array[i].creative = get_All_xml_nodes(myXML.Ad.InLine.Creatives.Creative); 
 .
 .
 .
}
dispatchEvent(new Event("VAST_parse_complete"));
}

//error handler missing nodes, and return array containing all node values
private function get_all_xml_nodes(node:Object):Array {

var nodesArray:Array = [];
if (node !== null && node !== undefined) {
for (var i:int = 0; i < node.length(); i++) {
   nodesArray.push(node[i].text());
}
} else {
trace('node element is undefined');
//start video player without ads
}
return nodesArray;
  } 
```

**Important: The code examples in this page should be used only as guidelines. Implementation may vary depending on the player/framework you are using.**

## Testing Your Integration

You can use Charles Proxy or any other proxy debugging tool to check your incoming and outgoing HTTP requests.

**Empty VAST response Error Handling \('nocom'\)**

1.  Add the following property to your VAST request flags=nocom
2.  It should look like this: vp-validation.videoplaza.tv/proxy/distributor?tt=preroll&tags=standard&shares=validation&rnd=8170019078998&accepts=vast\_2.0&flags=nocom
3.  You will get a VAST response with no commercials
4.  Start your video player, the player should error handle the empty response and start playing the video

**Tracking ad impressions**

1.  Start Charles Proxy and click on the Star Recording button
2.  Start your player, notice that Charles Proxy is tracking all requests made by your player
3.  Your player should be able to make multiple HTTP requests to all impressions from the image below

**Parent topic:**[Common Integration Articles](../../../oadtech/ad_serving/dg/common_integration.md)

