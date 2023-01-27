---
title: "Join a Room without or with Stream"
date: 
description:
type: "docs"
weight: 2
---

A typical process to connect to a room is as follows: 

1. Initiate a room and connect to it. 
2. Initiate streaming after connecting which requires you to check media accessibility.
3. Publish local stream.
4. Check if the stream is successfully published. 

To successfully join a Room, you need to ensure the success of each step before proceeding to the next thus making it a complex process.

The *EnxRtc.joinRoom()* method allows you to quickly join a room and get started without having to follow the above procedure step by step.

**Class**: *EnxRtc*

**Method**: *EnxRtc.joinRoom( Token, StreamOpt, Callback, ReConnectOpt )*

**Parameters**:
- *Token* – String. A JWT Token to connect to the Room as received using Server API Call via Application Server.
- *StreamOpt* – [Stream Initialization Meta Info.](./stream-initialization.md) Optional. If you don’t want to publish your local Stream, pass blank JSON object i.e *{ }*.
- *ReConnectOpt* – Optional. JSON Object with Reconnection Options. JSON keys are explained below:
    - *allow_reconnect*: Boolean. Default: true. Set to true to enable Auto-Reconnect feature. When set to false, Client endpoint does not try to reconnect to EnableX.
    - *number_of_attempts*: Numeric. Min Value: 1. Max Value: Not specified, use any number. Default: 3. A maximum number of attempts made by the Client endpoint to reconnect to EnableX.
    - *timeout_interval*: Numeric. Timeout Interval in Millisecond required by the Client endpoint to wait before attempting to reconnect.

**Returns**: Published Local Stream JSON Object

```
var VideoSize = {
     "HD": [320, 180, 1280, 720], 
     "SD": [320, 180, 640, 480],
     "LD": [80, 45, 640, 360]
};

var StreamOpt = {
         video: true,
         audio: true,
         data: true,
         videoSize: VideoSize.HD,
         attributes: { name: "XX" }
};

var reConnectOpt = {
    "allow_recnnect": true,
    "number_of_attempts": 3,
    "timeout_interval": 10000
}; 

localStream = EnxRtc.joinRoom(Token, StreamOpt, function (success, error) {
     if (error && error != null) {
         // Look for error.type and error.msg.name to handle Exception
         if(error.type == "media-access-denied") {
              // Media Media Inaccessibility
         }
     }
    
     if (success && success != null) { 
		room = success.room;
		if (room.waitRoom && room.me.role != "moderator") {
			// Wait for Moderator
		} else {
			remoteStreams = success.room.streams; 
		}
     }
 },
 reConnectOpt
)

```
**Error Codes or Exceptions**

| Code      | Description |
| ----------- | ----------- |
| 1000  | Unsupported browser. |
| 1142  | OverconstrainedError: Invalid Device Id. |
| 1130  | Moderator not present/Wait for Moderator. |
| 1144  | NotAllowedError: The request is not allowed by the user agent or the platform in the current context. |
| 1145  | NotReadableError: Could not start video source. |
| 1146  | TypeError: At least one of the audio and video must be requested. |
| 1149  | One of the constraints (Height, Width, Device Id) is not satisfied. |
| 1153  | Non-supported browser. |
| 1152  | Only Audio-only calls are allowed with your current browser version. |
| 1170  | Feature is not supported under current Service subscription or not enabled in the Room’s setting. |
| 1171  | Room not connected. |
| 1172  | Failed to connect Room. |
| 1176  | Moderator declined right to control media devices. |
