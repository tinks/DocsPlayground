# Setting up Development Environment

Follow these step to set up your development environment in Xcode. A few extra steps are needed, if you choose to code your application in Swift.

1.  Start a new Xcode project, and select the appropriate template from the iOS Applications.
2.  Enter a Product Name, and select the Language.
3.  Finish creating the project, and after the main project window opens, drag the framework into the project.
4.  In the options window, select Copy items if needed, and make sure that your project is selected as a target. Click Finish.
5.  Proceed with the following steps to create a bridging header file, if you chose Swift as the coding language, otherwise you are finished with the setup.
    1.  In Xcode, select File\>New\>File, select Cocoa Touch Class, and click Next
    2.  Call the file something temporary, select Objective-C as the language, and click Next.
    3.  Select your project, and click Create.
    4.  The pop-up window asks you to create the bridging header file, click Create Bridging Header.
    5.  Open the bridging header file, called <Project\_Name\>-Bridging-Header.h, and enter the import statement for the framework.

        ```
        #import <VideoplazaCore/VideoplazaCore.h>
        ```

    6.  Remove the tempory Cocoa Touch Class files.

**Parent topic:**[Phase 2 - Developing Your Integration \(iOS 2.x\)](../../../oadtech/ad_serving/dg/ios_2_phase2.md)

