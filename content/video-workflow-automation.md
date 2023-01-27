---
title: "Video Workflow Automation"
date: 
description:
type: "docs"
weight: 2
---
# Webhook Notification
A Web Hook URL is used to send real-time notifications of various meeting-related and post-processing events via JSON Payload format. Using the Web Hook URL, EnableX sends notifications through an HTTP POST request.

- To configure a Web Hook URL, go to the EnableX Portal and then proceed to the “Video Configuration” section. EnableX sends notifications through the HTTP POST request with JSON Payload in the raw format on the Web Hook URL.
- For more details, refer to the [Web Hook Documentation](./video-notification-webhook.md)

# Recording Delivery
EnableX delivers video meeting recordings to FTP, SFTP, and Amazon Web Services S3. EnableX sends notifications through the HTTP POST request using JSON Data in raw format through Web Hook URL whenever a recorded file is transferred to the designated location.

To configure the Recording Delivery, proceed toward the EnableX Portal, and then move to the “Video Configuration” section.
For more details, refer to the [Recording Delivery Documentation](video-recording-delivery.md)

# Recording Files Security
Recorded files accessible through HTTP URL within the first 3 days of recording will no longer remain accessible over open HTTP URL, rather they will be protected through HTTP Basic Authentication Process w.e.f. May 15, 2022.

If your Business Application accesses the Recording file URL from EnableX Server, please read through the documentation to understand secured access implementation and update your application accordingly.

For more details, refer to the [Recording Files Security Documentation](./recording-file-security.md).