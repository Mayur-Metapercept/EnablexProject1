---
title: "Get Media Devices"
date: 
description:
type: "docs"
weight: 2
---
This MediaStream API provides a way to access device cameras and microphones which may be used to create Media Stream to publish into Video Room. It also exposes information about devices able to capture and render media.

You can initiate a Stream using either the browser’s default Audio Device or by specifying the ID of the Audio Device connected to the device running the client application which requires you to get the Device IDs of all the connected devices. 

The *EnxRoom.getDevices()* method provides a list of all the Microphones connected to your Device. On the method call, the browser prompts the user to grant access to the application for one or both the devices (as applicable). The user must allow access for successful initiation of the stream. If allowed access, *media-access-allowed* event is the end point and the method returns list of devices.

If user doesn’t allow access, *media-access-denied* event is received at the end point and the method returns error code 1144.

**Method**: *EnxRtc.getDevices(Callback)*

**Event Listeners**:
- *media-access-allowed* – When the user grants permission to the application to access the media devices. 
- *media-access-denied* – When the user denies permission to the application to access the media devices. 

**Returns**: List of Devices
```
EnxRtc.getDevices( function(response) { 
     if( response.result === 0 ) {   // success                     
         /* Device Lists in response.devices */ 
         var camList =  response.devices.cam; 
         var micList =  response.devices.mic; 
	 var speakerList = response.devices.speaker;
     }
     else if(response.result === 1144){ // Error case  
       
     }
});

stream.addEventListner('media-access-allowed', function (response) {
	/* response = {
		stream: StreamObject,
		type: "media-access-allowed"
	}*/
});

stream.addEventListner('media-access-denied', function (response) {
	/* response = { type: 'media-access-denied', msg: err }*/
});
```
**Response JSON** (With list of devices):
```
{
     "result": 0,       
     "devices": { 
             "cam":[ 
                 { 
                 "deviceId": "", 
                 "groupId": "", 
                 "label": "" , 
                 "kind" : "" 
                 } 
             ], 
             "mic": [ 
                 { 
                 "deviceId": "", 
                 "groupId": "", 
                 "label": "" , 
                 "kind" : "" 
                 } 
             ],
	     "speaker": [ 
                 { 
                 "deviceId": "", 
                 "groupId": "", 
                 "label": "" , 
                 "kind" : "" 
                 } 
             ] 
         } 
 } 
 ```
 If you’re using *getUserMedia()* within an , you can request permission just for that frame, which is clearly more secure than requesting a more general permission. Here, indicate we need the ability to use both camera and microphone:

 ```
 <iframe src="https://my-website/rtc" allow="camera;microphone">
</iframe>
```
**Error Codes**

| Error Code     | Description |
| ----------- | ----------- |
| 1144      | Device Access denied       |
| 1146    | Failed to execute getUserMedia on MediaDevices       |
| 1150    | Unknown Reason       |

**Browser Compatibility**

![Browser Compatibility](./browser-compatibility.png)
