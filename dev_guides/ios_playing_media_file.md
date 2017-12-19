# Playing an Ad's Media File

This tutorial demonstrates how to set up the media player and how to loop through the media files and play back the correct file.



**VPAdPlayerViewController.m**

Pick out the Media file for the ad.

```
/** Retrieve a linear creative from the ad and send that to the video player.   
* Here I take the first video file find. Our backend put the one we think is best first   
* but idealy you will want to check which one is best for you.   
*/
-(void) playAd:(VPAd *)ad{
  self.currentAd = ad;

  if(self.currentAd.type == VPAdTypeInventory){
    [self trackAsInventoryAndPlayNext];
    return;
  }

  for (id c in ad.creatives) {
    // The VAST standard says that there can only be one Linear creative per ad.
    if ([c isKindOfClass:[VPLinearCreative class]]) {
      VPLinearCreative *creative = c;

      if([creative.mediaFiles count] > 0){
        self.currentCreative = c;
        VPMediaFile *mediaFile;
        for (int i= 0;  i < creative.mediaFiles.count; i++) {
          mediaFile = [creative.mediaFiles objectAtIndex:i];
          /* Ooyala Pulse's "Asset Selection" guarantees that only compatable video 
          formats are served so the MIME type check is not nessesary for native Ooyala Pulse media 
          files but Ooyala Pulse cannot give the same guarantee any 3rd party ads booked in Ooyala Pulse. */ 
          /* Pulse will sort the files, putting the media file it feels is most appropriate first. 
          If you want more control, you can implements additional checks here. */ 
          if ([mediaFile.mimeType isEqualToString:  @"video/mp4"]){
            break;
          }
        }

        if(mediaFile.URL){
          [self startAplayerFromURL:mediaFile .URL];
          return;
        }else{
          /* If no appropriate media files are found, report the error for the creative and move on to the next ad.  */
          [[self.delegate tracker] trackEvent:VPCreativeErrorEventInvalidCreative forCreative:self.currentCreative];
          [self playNext];
          return;
        }
      }
    }
  }

  // If you reach this point, there are no valid creatives in the ad obejct. 
  // Track this ad as Inventory and move on to the next one.
  [self trackAsInventoryAndPlayNext];
}

/* Track inventory for the ad object and move on to the next ad.  */
-(void) trackAsInventoryAndPlayNext{
  [[self.delegate tracker] trackEvent:VPAdTrackingEventImpression forAd:self.currentAd];
  [self playNext];
}
```

Play the ad.

```
/* Play NSURL as ad. */
-(void) startAplayerFromURL:(NSURL *) mediaURL{
  self.newAd = TRUE;

  if(!self.videoPlayer){
    [self setupPlayer];
  }

  MPMoviePlayerController *player = self.videoPlayer;

  // Set the video content. 
  [player setContentURL:mediaURL];
  [player setMovieSourceType:MPMovieSourceTypeFile];

  //Disable controls and play the ad.
  player.controlStyle = MPMovieControlStyleNone;
  player.initialPlaybackTime = -1.0;
  [player play];
}

-(void)setupPlayer{
  // Create an Apple MPMoviePlayerController. Included in the standard MediaPlayer Framework.
  MPMoviePlayerController *player = [[MPMoviePlayerController alloc] init];
  self.videoPlayer = player;

  //Put the videoPlayer in a CGRect and put it in the view.
  CGRect rect = CGRectMake(0, 0, self.view.bounds.size.width, self.view.bounds.size.height);
  [player.view setFrame:rect];
  [self.view addSubview: player.view];

  // Movie playback complete
  [[NSNotificationCenter defaultCenter] addObserver:self 
                                           selector:@selector(moviePlayBackDidFinish:) 
                                               name:MPMoviePlayerPlaybackDidFinishReasonUserInfoKey
                                             object:self.videoPlayer];

  // Resume playback upon returning if you left the application. 
  [[NSNotificationCenter defaultCenter] addObserver:self 
                                           selector:@selector(onResume) 
                                               name:UIApplicationDidBecomeActiveNotification 
                                             object:nil];

  [[NSNotificationCenter defaultCenter] addObserver:self  
                                           selector:@selector(onPlayStatusChange:) 
                                               name:MPMoviePlayerPlaybackStateDidChangeNotification 
                                             object:self.videoPlayer];
}

- (void)onPlayStatusChange:(NSNotification*)notification {
  MPMoviePlayerController *player = (MPMoviePlayerController *) [notification object];
  NSInteger state = [player playbackState];

  if(self.newAd && state == MPMoviePlaybackStatePlaying){
    //Trigger impression.
    self.newAd = NO;
    [[self.delegate tracker] trackEvent:VPAdTrackingEventImpression forAd:self.currentAd];
    [[self.delegate tracker] trackEvent:VPCreativeTrackingEventStart forCreative:self.currentCreative];
  } 
}

-(void)onResume{
  [self.videoPlayer play];  
}

- (void)moviePlayBackDidFinish:(NSNotification *)notification {
  int reason = [[[notification userInfo] valueForKey:MPMoviePlayerPlaybackDidFinishReasonUserInfoKey] intValue];
  if (reason == MPMovieFinishReasonPlaybackEnded) {
    // Track creative complete
    [[self.delegate tracker] trackEvent:VPCreativeTrackingEventComplete forCreative:self.currentCreative];
    // Decrement the total spot duration
    self.spotDuration -= self.currentCreative.duration;
    //Play th next ad.
    [self playNext];

  }else if (reason == MPMovieFinishReasonUserExited) {
    //user interupted playback
  }else if (reason == MPMovieFinishReasonPlaybackError) {
    [[self.delegate tracker] trackEvent:VPCreativeErrorEventInvalidCreative forCreative:self.currentCreative];
    [self playNext];
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

