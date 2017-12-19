# Loop Through All the Ads in a Break

This tutorial covers how to create the ad player view controller, which will be used to display the ads, and how to loop through all the ads served from Ooyala Pulse.

\[ooyala:J2bXZ0dToerQ4yjQnrk7hGFW-gQxrFSX\]



## VPAdPlayerViewController.h

```
#import <UIKit/ UIKit.h>
#import "VideoplazaCore.h" 

@protocol VPAdPlayerDelegate 
- (void) adSpotComplete;
@end 

@interface VPAdPlayerViewController : UIViewController 
-(id) init;
-(void) playAds: (NSArray *) ads;

@property (nonatomic, weak) id delegate;

@end
```

## VPAdPlayerViewController.m

```
-(void) playAds:(NSArray *) ads{
  self.ads = ads;
  self.currentAdIndex = 0;
  self.spotDuration = 0;

  // Calculating the total duration of the ad spot.
  for (VPAd *ad in self.ads) {
    for (id c in ad.creatives) {
      if ([c isKindOfClass:[VPLinearCreative class]]) {
        VPLinearCreative *creative = c;
        self.spotDuration += creative.duration;
      }
    }
  }
  [self playNext];
}

-(void) playNext{
  if([self.ads count] > self.currentAdIndex){
    VPAd *ad = [self.ads objectAtIndex:self.currentAdIndex];
    self.currentAdIndex++;
    [self playAd:ad];
  } else{
    [self closeAdPlayer];
  }
}

-(void) playAd:(VPAd *) ad{
}

-(void) closeAdPlayer{
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 1.x\)](../../../oadtech/ad_serving/dg/ios_phase2.md)

