# Asset Factory

Generate video assets to run on any device of your choosing, by uploading a source video file to Pulse, to trigger the built-in Asset Factory. The source file can be of almost any file format and quality. For more information, refer to [Appendix B - Creative Asset Specification](appendix_b.md).

The assets are transcoded and generated asynchronously, meaning you can complete your campaign booking while the video files are being created. The campaign goes live as soon as the files are ready \(or when the campaign is configured to go live\). If a campaign needs to target a new device, just add it to the targeting options and the Asset factory generates a transcoded file that works for that device.

The Asset Factory enables you to:

-   see a list of all the uploaded files,
-   search for uploaded files,
-   preview uploaded files,
-   reuse files for another ad,
-   see all the files being transcoded, as well as their transcoding progress and status,
-   abort transcoding,
-   download source files,
-   download transcoded files,
-   delete the files that are not currently used in a campaign.

## Asset Factory Interface

When you click on the Asset Factory from the menu \(![Asset Factory icon](../../image/pulse_asset_factory_icon.png)\), a new page opens up:

![Asset Factory interface](../../image/pulse_asset_factory_overview.png)

## Parts of the Asset Factory

|Part|Name|Description|
|----|----|-----------|
|1|Search asset|Search for an asset based on the file name. Type in the text you want to search for and click the Search button. Searches are not case sensitive.|
|2|File list|A list of all the uploaded files showing: -   file status,
-   date of upload,
-   number of campaigns the file is in.

|
|3|Menu|Click the menu for more options: -   Download source file
-   Download transcoded files
-   Delete file

|
|4|Transcoding progress|Transcoding progress bar and information. If any errors occur during transcoding, the uploaded file is marked as failed in the Asset Factory. You need to upload the file again to re-trigger the file transcoding process.|
|5|Preview area|When you click on a file from the list, you see a preview of the file with additional information. From the preview area you can also: -   click the ![Download icon](../../image/pulse_asset_factory_download_icon.png) to download transcoded files \(a package of all the generated assets\)
-   click the ![Trash can icon](../../image/pulse_asset_factory_trash_can_icon.png) to delete the file.

|

## FTP Account for Asset Uploading

Pulse allows external FTP access \(for accounts defined by you\) to upload assets to your Asset Factory. Anyone with access granted by Ooyala staff can upload files. The access is limited to uploading only to maintain a high security level. For information on your FTP account details, refer to [Integration Information](settings.md#integration_information).

**Parent topic:**[Uploading Ad Assets Manually or Automatically](../../../oadtech/ad_serving/ug/uploading_ad_assets.md)

