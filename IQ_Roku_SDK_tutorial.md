James has made a change!

Tine made some changes to this file.

This tutorial shows you how to include and work with the IQ library in your Roku channel.

### Getting the library

To get the library, [go here](https://github.com/ooyala/iq-sdk-roku).

### Integrating the library in your project

Integrating the library in your project is as simple as copying `IQ.brs` to your source folder, like any other source file in your Roku channel. If you see issues when deploying your channel to a Roku device, make sure you have added the file in your zip build script/Makefile.

### Adding IQ to your channel

Using the library in a Roku channel is simple.
1.	Instantiate the `IQ` object in your init code.

	```
	Sub Main()
		m.iq = new IQ()
	```

	This step marks the start of the session, and does not report anything back to IQ.

2.	Init your IQ session using your pcode when you load your video player. The pcode can be found in your Ooyala Backlot account. For more information, refer to [Your API Credentials](http://support.ooyala.com/developers/documentation/concepts/api_keys.html).

	```
	Sub loadVideoPlayer()
		screen.show()
		pcode  : "YOUR_BACKLOT_PCODE"
		m.iq.init(pcode)

	```

3.	Give IQ the metadata about the video you are about to play.

	```
	m.iq.setContentMetadata({duration : 60, assetId : "AdDgFFGgEergergwrrehEj" , assetType: "external"} })
	```

	This code is typically called when you have retrieved information about the content from a server, and **before** the video starts. The duration should be in seconds.

4.	**Set the notification period of your video player to one second.** This is very important, because IQ needs the highest possible precision on time updates.

	```
	video = CreateObject("roVideoScreen")
	video.SetPositionNotificationPeriod(1)

	```

5.	When the user requests the content start, call `reportPlayRequested`. It takes one parameter `isAutoplay`. Set `isAutoplay` to true if the content was automatically played without user input.

	```
	video.show()
	m.iq.reportPlayRequested(false)
	```

6.	In the main event loop, forward all messages on the video message port to the library.

	```
	video.show()
	m.iq.reportPlayRequested(false)

	while true
        msg = wait(1000, video.GetMessagePort())
        m.iq.handleEvent(msg)
        doStuffWithTheEvents()
    end while
	```

7.	When the event loop is exited, call `reportEventLoopExit`. This allows the library to make sure that all the events were sent to the server.

	```
	while true
        msg = wait(1000, video.GetMessagePort())
        m.iq.handleEvent(msg)
        doStuffWithTheEvents()
  end while
  m.iq.reportEventLoopExit()
	```

8. Replays can be reported with `reportReplay()`. Custom events can also be reported with `reportCustomEvent(name, metadata)`.

	```
	m.iq.trackCustomEvent("myCustomEvent", {myCustomValue : 42, myCustomParameter : "Brightscript is awesome!"})
	```

### Debugging

The library possesses an attribute `private_debugEnabled` that can be set to true in order to get useful information about the tracked events in the console and to help troubleshoot problems.
