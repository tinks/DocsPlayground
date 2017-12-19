# Get Insertion Point from Session

We requested and stored the session object, which allows us to access the insertion points. An insertion point object contains 2 lists of objects which are needed to show the right ads at the right time. The object types of these lists are:

-   **Slots**: contain the actual ads which need to be shown.
-   **Conditions**: dictate when the ads in the slots should be shown.

To find the right insertion point, you need to evaluate the conditions of each insertion point to match the ad request event from the video player. Conditions can be relatively simple, like pre-roll or mid-roll, but they can also be time based, like the amount of video content playback time. Handling the events from the video player together with parsing the conditions of the insertion points is what we refer to as the **condition engine**, and contains the main logic of the integration.

## Condition Evaluation

When you evaluate conditions, there are a number of things to keep in mind:

-   **Class**: there are 2 classes of conditions:
    -   Event \(EventCondition\): is a condition based on an event, for example, a mid-roll.
    -   Property \(PropertyCondition\): is a condition where a property needs to be evaluated against a set value, for example, the playback position.
-   **Sub conditions**: a condition can itself have a condition.
-   **One path of true conditions** must be found in the tree of conditions related to the insertion point before you can serve the related ads.

The last point is illustrated with the following decision tree:

![Insertion point condition evaluation path](../../image/integration_cond_eval.png)

## Example: Retrieve Pre-roll Insertion Point

**Java**

```
/*
 * Retrieve the pre-roll insertion point without taking any other conditions into account
 */

public InsertionPoint getPrerollInsertionPointForSession(Session successfulSession) {

    InsertionPoint prerollInsertionPoint = null;

    List<InsertionPoint> insertionPointList = successfulSession.getInsertionPoints();

    if (insertionPointList.size() > 0) {
        for (InsertionPoint insertionPoint : insertionPointList) {

            // preroll/midroll/postroll conditions are the first condition in each insertion point.
            Condition condition = insertionPoint.getConditions().get(0);
            if (condition != null) {
                // the pre-roll condition constant is ON_BEFORE_CONTENT
                if (condition.getType() == Condition.Type.ON_BEFORE_CONTENT) {
                    prerollInsertionPoint = insertionPoint;
                }
            } else {
                Log.i("Demo Player", "No conditions found for the insertion point");
            }
        }
    } else {
        Log.i("Demo Player", "No insertion points found for session");
    }
    
    return prerollInsertionPoint;
}
```

**Parent topic:**[Phase 2 - Developing Your Integration \(Android 2.x\)](../../../oadtech/ad_serving/dg/android_2_phase2.md)

