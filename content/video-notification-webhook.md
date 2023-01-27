---
title: "Video Notification Webhook"
date: 
description:
type: "docs"
weight: 2
---
Enhanced Video Service notifies many important events to your Application Server through a Webhook. Once setup, you can start receiving HTTP Posts with Raw Body Contents and use them to develop an effective and well integrated Video Application with EnableX.
# Overview
EnableX Video Service features a Server-to-Server Notification Service to share important events of a Session and Post Processing updates. This Service helps you to implement an effective and complete workflow of your application.

EnableX notifies your Application Server through a HTTP POST to a configured Notification Web Hook URL.
# Setup Notification URL
A Notification URL is a Project specific setting. Therefore, each project can have different Notification URL. However, you are free to use the same Notification URL against multiple projects to get notified. Note that the JSON Data posted to the Notification URL, will carry the app_id of the Project which you can use to segregate data for each project.

To setup Notification URL:

- Login to the Portal
- Navigate to “Projects / My Projects”.
- To get started with EnableX video services, go to “Get Started” under “Video” in the Left Bar. “Select Project” to choose whether you want low code integration or will prefer to code yourself for the selected project. In case if you have set this preference for your project, clicking on the project navigates to the “Settings” page.
- Next, go to the “Setup Webhook” tab under the “Settings” option to set up a URL to receive Notifications from the platform.​
- You get a form. Enter the URL and click submit to set up your Notification URL.
- In case you look to implement Access Security in your Webhook, EnableX supports HTTP Basic Authentication. You need to check the “HTTP Authentication” checkbox and enter related username & password that EnableX must use to access your Webhook.
![Advance Settings](./advance-settings.png)
You are all set to receive Notification Events explained below:
# Notification Events
Once you configured your Notification Webhook URL, EnableX does HTTP POST with JSON Raw Body to the URL to notify you on few events related to your Session and Post Session Processing. The JSON Body contains a key named type which contains a String Constant for different type of event notification.
```
{
	"type": "String" /* Constants: roomdrop, recording, transcoded, file-transfer */
}
```
## Notification# 1: Session Ended
EnableX notifies you as soon as any session ends in EnableX Video Room. The JSON posted to Notification Webhook URL as Raw Body contains META information of the Session (e.g. Room ID, Conf Num et and so on.).
```
{ 
	 "type": "roomdrop",
	 "trans_date": "Unix Timestamp",  /* In UTC */
	 "app_id": "String",
	 "room_id": "String",
	 "conf_num": "String" 
}
```
**Note**: *"type": "roomdrop"* for Session End Notification.

In case your Application needs to get Call Detail Report (CDR) for the concluded Session, you can use Server API call on the *conf_key* data. The Room ID and Conf Num may be used to data reference.
## Notification# 2: Recording File(s) Ready
EnableX notifies you as soon as any Recording file(s) are available for your concluded sessions. The JSON posted to Notification Webhook URL as Raw Body contains META information of the Session (e.g. Room ID, Conf Num etc.) along with an Array of Recorded File paths.
```
{ 
	 “type”: “recording”,
	 “trans_date”: “Unix Timestamp”,  /* In UTC */
	 “app_id”: “String”,
	 “room_id”: “String”,
	 “conf_num”: “String”,
	 “recording”: [ 
		"http://FQDN/path/file"
	 ]
}
```
**Note**: *"type": "recording"* for Recording File Notification.

In case your application needs to download all recorded files to store locally, you can do so by looping through the Array and download each file individually. The Room ID and Conf Num may be used to data reference.
## Notification# 3: Transcoded File(s) Ready
EnableX notifies you as soon as any transcoding is done and the transcoded file(s) are available to you. The JSON posted to Notification Webhook URL as Raw Body contains META information of the Session (e.g. Room ID, Conf Num etc.) along with an Array of Transcode File paths.
```
{ 
	 "type": "transcoded",
	 "trans_date": "Unix Timestamp",  /* In UTC */
	 "app_id": "String",
	 "room_id": "String",
	 "conf_num": "String",
	 "recording": "http://FQDN/path/file",
	 "stage": "String",  /* Sequence of File within Session */
	 "file_size": "String", /* In byte */
}
```
**Note**: *"type": "transcoded"* for Transcoded File Notification.

In case your Application needs to download all transcoded files to store locally, you can do so by looping through the Array and download each file individually. The Room ID and Conf Num may be used to data reference.
## Notification# 4: Recording / Transcoded File(s) Transferred
EnableX notifies you as soon as a Recording or Transcoded file is transferred to your Location through our Video Recording Delivery Service. The JSON posted to Notification Webhook URL as Raw Body contains META information of the Session (e.g. Room ID, Conf Num etc.) along with Destination Server Information and transferred file location.
```
{
	"type": "file-transfer",
	"trans_date": "Unix Timestamp", /* In UTC */
	"app_id": "String",
	"room_id": "String",
	"conf_num": "String",
	"destination": {
		"name": "",	/* Constants: awss3, ftp, sftp, ssh */
		"host": "",	/* In case of ftp, sftp, ssh */
		"account": ""	/* In case of awss3  */
	},
	"files": [
		{ "url": "http://FQDN/path/file" }
	]
}
```
**Note:** *"type": "file-transfer"* for File Transfer Notification.

The *files* array may contain one or many transferred files new location on the destination. The Room ID and Conf Num may be used to data reference.