---
title: "Initiate Stream with specific Devices"
date: 
description:
type: "docs"
weight: 2
---

You can initiate a Stream using either the browser’s default Audio Device or by specifying the ID of the Audio Device connected to the device running the client application which requires you to get the Device IDs of all the connected devices. 

The *EnxRoom.getDevices()* method provides a list of all the Microphones connected to your Device. You can also use this method to build UI Element allowing users to choose an Audio Device from the list.
```
var streamOpt = {
     audio: {deviceId: "XXX"}, 
     video: {deviceId: "XXX"}, 
     data: true, 
     attributes: { name:'My-Stream-Name' }
 };

 var localStream = EnxRtc.EnxStream( streamOpt ).init(); 
 ```
 When the Client Application is used in Mobile browser, it generally starts video stream using Rear Camera. To use the Front Camera instead of Rear Camera, use *facingMode*: '*user*'. To use Rear Camera, use *facingMode: 'environment*'.
 ```
 var streamOpt = {
     audio: {deviceId: 'XXX'}, 
     video: {facingMode: 'user'}, 
     data: true, 
     attributes: { name:'My-Stream-Name' }
 };

 var localStream = EnxRtc.EnxStream( streamOpt ).init();
 ```