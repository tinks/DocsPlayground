# Ads Crash App for iPod Touch and Android Users

## Issue identification on iPod Touch

**Note:** This issue does not occur on iPhones or iPads.

There is a "[known bug](http://stackoverflow.com/questions/3116259/mpmovieplayercontroller-slow-crashes-on-ipod-touch)" on iPod Touch that seems to have to do with the encoding of the videos. The problem appears when switching between two videos \(for example, the ad and the content\), and one of the videos does not have the exact encoding specification from Apple. The only solution is to use the exact specification provided by Apple. Most devices can handle tweaks to the encoding, but not the iPod Touch, so if you want to be sure to not bring down your iPod users' experience, make sure to use the specifications below when encoding the ads and the videos:

```
----- H.264 Baseline Profile Level 3.0 video, up to 640 x 480 at 30 fps. (The Baseline profile does not support B frames.)
----- MPEG-4 Part 2 video (Simple Profile)
```

Bitrate settings for high quality video \(WIFI\):

```
Video: Constant Bit Rate 604 kbits
Frame rate: Same as source (max 30 fps)
Audio: 96 kbits
```

Bitrate settings for low quality video \(3G\):

```
Video: Constant Bit Rate 304 kbits
Frame rate: Same as source (max 30 fps)
Audio: 96 kbits
```

## Creating compatible video using Handbrake + QT index swapper

Download Handbrake from [http://handbrake.fr/](http://handbrake.fr/).

Use defaults settings for the iPhone/iPod touch preset: ![iPhone and iPod Touch standard settings](../../image/HandBrake.jpg)

For all Android devices to play the video, you also need to make sure that its index is in the beginning and not the end of the file. This is done using QT index swapper:[http://renaun.com/blog/code/qtindexswapper/](http://renaun.com/blog/code/qtindexswapper/)

![QTIndexSwapper](../../image/QTIndex_swapper.png)

**Parent topic:**[Ooyala Pulse FAQ](../../../oadtech/ad_serving/dg/faq_overall.md)

