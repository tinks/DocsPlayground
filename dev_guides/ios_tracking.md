# Tracking

This tutorial explains all the tracking events for the player.



## VPViewController.m

Add the tracker module to the VPViewController and apply lazy instantiation to the getter of the tracker.

```
#import "VPViewController.h" 
#import "VideoplazaCore.h" 
#import "VPAdPlayerViewController.h" 

@interface VPViewController ()

@property (nonatomic, strong) VPTracker *tracker;
//...

@end 

@implementation VPViewController 

@synthesize tracker = _tracker;
//...

-(VPTracker *) tracker{
  if(!_tracker){
    _tracker = [[VPTracker alloc] init];
  }
  return _tracker;
}
```

## VPAdPlayerViewController.m

Add the tracking events, Impression, Ad Started, Ad Quartiles, Ad Completed, and Ad Error.

```
@interface VPAdPlayerViewController ()

@property (nonatomic) BOOL newAd;
@property (nonatomic, strong) NSTimer *ticker;
// ...

@end

@implementation VPAdPlayerViewController

@synthesize newAd = _newAd;
@synthesize delegate = _delegate;
@synthesize ticker = _ticker;
// ...

-(void) playAd:(VPAd *) ad{
  self.currentAd = ad;

  if(self.currentAd.type == VPAdTypeInventory){
    [self trackAsInventoryForAd: ad];
  }

  for (id c in ad.creatives) {
    //The VAST standard says that there can only be one Linear creative per ad.
    if ([c isKindOfClass:[VPLinearCreative class]]) {
      VPLinearCreative *creative = c;

      if([creative.mediaFiles count] > 0){
        self.currentCreative = c;

        VPMediaFile *mediaFile;
        for (int i=0; i < creative.mediaFiles.count; i++) {
          mediaFile = [creative.mediaFiles objectAtIndex:i];
          // Ooyala Pulse's "Asset Selection" guarantees that only compatable video formats are served 
          // so the MIME type check is not nessesary for native Ooyala Pulse media files but Ooyala Pulse 
          // cannot give the same guarantee any 3rd party ads booked in Ooyala Pulse.

          // Ooyala Pulse will sort the files, putting the media file it feels is most appropriate
          // first. If you want more control, you can implements additional checks here.
          if ([mediaFile.mimeType isEqualToString: @"video/mp4"]){
            break;
          }
        }

        if(mediaFile.URL){
          [self startAplayerFromURL:mediaFile.URL];
          return;
        }else{
          // If no appropriate media files are found, report the error for the creative and move on to the next ad.
          [[self.delegate tracker] reportErrorEvent:VPCreativeErrorEventInvalidCreative forCreative:self.currentCreative];
          [self playNext];
          return;
        }
      }
    }
  }
}

// ...

-(void) trackAsInventoryForAd:(VPAd *) ad{
  [[self.delegate tracker] trackEvent:VPAdTrackingEventImpression forAd:ad];
  [self playNext];
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

-(void)onTimerEvent{
  MPMoviePlayerController *player = self.videoPlayer;
  VPLinearCreative *creative = self.currentCreative;
  double duration = player.duration;
  double time =  player.currentPlaybackTime;

  if(duration){
    if (time >= duration / 4 * 3) {
      [[self.delegate tracker] trackEvent:VPCreativeTrackingEventThirdQuartile forCreative:creative];
    }else if (time >= duration / 2) {
      [[self.delegate tracker] trackEvent:VPCreativeTrackingEventMidPoint forCreative:creative];
    }else if (time >= duration / 4) {
      [[self.delegate tracker] trackEvent:VPCreativeTrackingEventFirstQuartile forCreative:creative];
    }
  }
  [[self.delegate tracker] trackEvent:VPCreativeTrackingEventTimeSpent forCreative:self.currentCreative];
}

- (void)moviePlayBackDidFinish:(NSNotification *)notification {
  int reason = [[[notification userInfo] valueForKey:MPMoviePlayerPlaybackDidFinishReasonUserInfoKey] intValue];
  if (reason == MPMovieFinishReasonPlaybackEnded) {
    // Track creative complete
    [[self.delegate tracker] trackEvent:VPCreativeTrackingEventComplete forCreative:self.currentCreative];
    //Play the next ad.
    [self playNext];
  }else if (reason == MPMovieFinishReasonUserExited) {
    //user interupted playback
    [[self.delegate tracker] trackEvent:VPCreativeTrackingEventClose forCreative:self.currentCreative];
  }else if (reason == MPMovieFinishReasonPlaybackError) {
    [[self.delegate tracker] reportErrorEvent:VPCreativeErrorEventInvalidCreative forCreative:self.currentCreative];
    [self playNext];
  }
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

