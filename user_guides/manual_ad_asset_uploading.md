# Manual Ad Asset Uploading

If you do not use the Asset Factory to generate files you can upload files manually for any device you want to target. For more information on file requirements, refer to [Appendix B - Creative Asset Specification](appendix_b.md).

When you upload an asset \(or fetch it from a URL\) in the **Add new ad** window, Pulse tries to match it with the file requirements for the devices you wish to target. The requirements are visible in the **Expected files** table. By following these requirements, the file can play in the device specific video player, by matching the configuration of video codec, bitrate and file extension to the uploaded file. The bitrate can be up to 10% higher than the expected value, and still be accepted. However, the video codecs and file extensions must be the same as stated in the "Expected files" table.

![Manual upload of Expected files](../../image/pulse_upload_creative_now.png)

If the asset does not match the required configuration, it is placed in a separate table for **other uploaded files**. A common case would be where you upload a file with higher bitrate than the required 700 kilobits per second. Pulse tries to serve this file if it meets the requirements of codec and file extension.

**Parent topic:**[Uploading Ad Assets Manually or Automatically](../../../oadtech/ad_serving/ug/uploading_ad_assets.md)

