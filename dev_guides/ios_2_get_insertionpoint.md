# Get Insertion Point from Session

We requested and stored the session object \(\_adSession\), which allows us to access the insertion points. An insertion point object contains 2 arrays of objects which are needed to show the right ads at the right time. The object types of these arrays are:

-   **Slots**: contain the actual ads which need to be shown.
-   **Conditions**: dictate when the ads in the slots should be shown.

To find the right insertion point, you need to evaluate the conditions of each insertion point to match the ad request event from the video player. Conditions can be relatively simple, like pre-roll or mid-roll, but they can also be time based, like the amount of video content playback time. Handling the events from the video player together with parsing the conditions of the insertion points is what we refer to as the **condition engine**, and contains the main logic of the integration.

## Condition Evaluation

When you evaluate conditions, there are a number of things to keep in mind:

-   **Class**: there are 2 classes of conditions:
    -   Event \(VPEventCondition\): is a condition based on an event, for example, a mid-roll.
    -   Property \(VPPropertyCondition\): is a condition where a property needs to be evaluated against a set value, for example, the playback position.
-   **Sub conditions**: a condition can itself have a condition.
-   **One path of true conditions** must be found in the tree of conditions related to the insertion point before you can serve the related ads.

The last point is illustrated with the following decision tree:

![Insertion point condition evaluation path](../../image/integration_cond_eval.png)

## Example: Retrieve Pre-roll Insertion Point

**Objective-C**

```
/*
 * Retrieve the pre-roll insertion point without taking any other conditions into account
 */

- (void) getPrerollInsertionPointForSession:(VPSession *) adSession
                                    success:(void(^)(VPInsertionPoint *insertionPoint))onSuccess
                                       fail:(void(^)(NSString *error))onFail {
    if (adSession.insertionPoints) {
        for (VPInsertionPoint *insertionPoint in adSession.insertionPoints) {
            if (insertPoint.conditions) {
                for (VPCondition *condition in insertionPoint.conditions) {
                    // the pre-roll condition constant is VPConditionTypeOnBeforeContent
                    if (condition.type == VPConditionTypeOnBeforeContent) {
                        onSuccess(insertionPoint);
                        break;
                    }
                }
            } else {
                onFail(@"No conditions found for insertion point: %@", insertionPoint);
            }
        }
    } else {
        onFail(@"No insertion points found for session: %@", adSession);
    }
}
```

**Swift**

```
func getPrerollInsertionPointForSession(adSession: VPSession, sucess: (VPInsertionPoint) -> Void, fail: (String) -> Void) {
	guard let insertionPoints = adSession.insertionPoints().map( {$0 as! VPInsertionPoint} ) else {
		fail("No insertion points found for session ", adSession)
	}
	
	let matchingInsertionPoint = insertionPoints.filter({ (insertionPoint: VPInsertionPoint) -> Bool in
		if let conditions = insertionPoint.conditions().map( {$0 as! VPCondition} ) {
			return conditions.filter({$0.type() == .OnBeforeContent})
		} else {
			return false
		}
	})
	
	success(matchingInsertionPoint)
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

