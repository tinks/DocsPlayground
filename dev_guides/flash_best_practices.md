# Flash Integration: Best Practices

-   Third-party players and the Ooyala integration should be easily decoupled. For example, the client may want turn the Ooyala plugin on/off depending on occasion, or add new functionalities to the plugin without the need to rewrite large amounts of code.
-   Your player core functionalities should not be dependent on the Ooyala integration. For example, your player should not always rely on Ooyala events to display the player controls, menus and other functionalities. Remember that the client may turn the integration on/off at occasions.
-   The Ooyala configuration should not be hard-coded into the player. The client and developers should be able to change the configuration easily without having to access the player code. For example, the integration should get its configuration from Flashvars, client CMS, XML, JSON, and so on.
-   You should avoid initiating the Ooyala plugin modules only when the user clicks the play button. Loading the plugin when your player loads improves the user experience and avoids timing issues. You should, however, only make a new ad request \(setNewItem\) when the user clicks play.

**Parent topic:**[Phase 2 - Developing Your Integration \(Flash\)](../../../oadtech/ad_serving/dg/flash_phase2.md)

