---
title: "Communicating with Video Embed"
date: 
description:
type: "docs"
weight: 2
---

EnableX provides a communication channel between IFRAME Embed and Parent Window. This enables Application Developers a tool of engagement with Embed in-session to create UI/UX. Developers can execute the predefined actions in Embed from Parent and get notified about status and events happening in Embed. 

**Table of Contents**

[How it works?](#how-it-works)

[Actions](#actions)

  [Notification Subscription](#notification-subscription)

  [Room Connection](#room-connection)

  [Stream Updates](#stream-updates)

  [Live Streaming](#live-streaming)

  [UI/UX](#ui--ux)

  [Messaging](#messaging)

[Notifications](#notifications)

  [Subscription](#subscription)

  [Room Connection](#room-connection)

  [User Connection](#user-connection)
 
  [Stream Updates](#stream-updates)

  [Live Streaming](#live-streaming)

  [Media Access](#media-access)

  [Messaging](#messaging)

# How it works?

JS Framework of Messaging between Browser Window Objects (parent, child, named-window) would help in this process. A window sends a message with JSON Data to other window which listens to incoming message and takes action on it.

So, Embed will listen to Message sent by Parent Page to take action on it and will also generate Message to Parent Page to notify various events.

To understand the overall workflow, follow the section below explanations with Code Samples:

## Action from Parent Window

**Example**: Parent Window sends message to Embed to Start Streaming:

```js
const message = JSON.stringify({
    action: 'start-live-streaming',
    data: {
	"name": "Youtube",
	"rtmp_endpoint": "rtmp://a.rtmp.youtube.com/live2",
	"rtmp_key": "XOXOXO"
	}
});

EmbedIFrameElementID.contentWindow.postMessage(message, '*'); 
// EmbedIFrameElementID is the "id" of IFRAME Tag that uses Low Code Meeting URL
```

## Listener at Parent Window

**Example**: Parent Window listens to notification message from Embed and takes appropriate action:

```js
window.addEventListener(‘notification’, function (e) {
	// Get the sent data
	var evtdata = e;

	// If you encode the notification  in JSON before sending them,
	// then decode here
	var data_decoded = JSON.parse(evtdata);
	
	// data_decoded example:
	/*
	{
	    notification: ‘room-connected',
	    data: {
		"room_name": "John’s Room",
		"conf_num": "XOXOXO"
		}
	}
	*/

	switch (data_decoded.notification) {
		case ‘room-connected’:
			doDBPost(data_decoded.data);
			break;
		case 'other-notice':
			do_other_notice()
			break;
	}
});
```

# Actions

Here are the list of Actions that can be passed from Parent Window to Embed in the form of JSON Object. Note that this Document only provides the format of JSON Object that is used effectively in message passing to get an action executed.

## Notification Subscription

Parent window must subscribe for Event Notifications from Embed to start receiving. Embed will keep sending Notifications of subscribed “Notification Groups” to Parent until unsubscribed.

### Subscribe to start receiving notifications

This is to subscribe to receive notifications of various events and action status from the Embed. You need to subscribe to one or more Notification Group(s) to start receive all event notifications under that group.
for example if you subscribe to *room-connection* group, embed will notify you of room connection, disconnection, reconnection and so on.

```js
{
  "action": "subscribe-notification",
  "data": [   /* one or more notification group */
    "live-streaming",
    "room-connection",
    "user-connection",
    "stream-updates",  
    "messaging"
  ]
}
```

**Data Object**: It contains an array of notification groups to subscribe to receive notifications related to that group until unsubscribed.

|Data object notification|Description|
|---|---|
|*live-streaming*|To receive start / stop live streaming notifications|
|*room-connection*| To receive notification related to room connection, disconnection, re-connection etc.|
|*user-connection*| To receive notification related to any user connecting to room or disconnecting from room.|
|*stream-updates*|To receive notification related to local and remote stream attribute, configuration updates.
|*messaging* |To receive notification related to custom signaling, chat (coming up) and so on.|


### Unsubscribe to stop receiving notifications

This is to unsubscribe from receiving notifications of various events from Embed. You may opt-out from one or more notification groups by passing multiple group names.

To unsubscribe notification from one or more notification groups, post the following:

```js
{
  "action": "unsubscribe-notification",
  "data": [
    "live-streaming",
    "room-connection",
    "user-connection",
    "stream-updates",  
    "messaging"
  ]
}
```
**Data Object**: It contains an array of notification groups to unsubscribe to stop receiving notifications related to that group.
|Data Object Notification|Description|
|---|---|
|*live-streaming*|To stop receiving start / stop live streaming notifications|
|*room-connection*| To stop receiving notification related to room connection, disconnection, re-connection etc.|
|*user-connection*| To stop receiving notification related to any user connecting to room or disconnecting from room.|
|*stream-updates*| To stop receiving notification related to local and remove stream attribute, configuration updates.|
|*messaging* |To stop receiving notification related to custom signaling, chat (coming up) etc.|

To unsubscribe notification from all notification groups, post the following:

```js
{
  "action": "unsubscribe-notification",
  "data": []
}
```
 
## Room Connection

### Disconnect from Room

This is to disconnect from the Virtual Room. Once disconnected, the Embed is not longer in Video Session and will not able to communicate with the Virtual Room anyway until it rejoins the Session.

To disconnect from Session with a Prompt to confirm exit from Session, send the following message:

```js
{
  "action": "disconnect-room",
  "data": {
    "alert": true
  }
}
```

**Data Object**:

|Data object notification|Type|Description|
|---|---|---|
|*alert*| Boolean| Use true to disconnect session only if user confirms through given Prompt Window|

To disconnect from Session immediately without a Prompt to confirm exit from Session, send the following message:

```js
{
  "action": "disconnect-room",
  "data": {
    "alert": false
  }
}
```

**Data Object**:

|Data type notification|Type|Description|
|---|---|---|
|*alert*| Boolean| Use *false* to disconnect  immediately without any prompt|

### Destroy Video Session

A Moderator or Host can destroy Virtual Room to stop the Session immediately. Once the Session is destroyed, all connected users will be disconnected automatically from the Room.

To destroy Session with a Prompt to confirm, send the following message:
```
{
  "action": "destroy-room",
  "data": {
    "alert": true
  }
}
```
**Data Object**:

- *alert*– Boolean. Use true to destroy session only if user confirms through given Prompt Window

To destroy Session immediately without a Prompt to confirm, send the following message:
```
{
  "action": "destroy-room",
  "data": {
    "alert": false
  }
}
```
**Data Object**:

- *alert*– Boolean. Use false to destroy session immediately without any prompt
**Note**: This a Host only feature, so must be executed from the Moderator/Host Side of UI only.

## Stream Updates

These set of actions are related to updated local and remote stream media tracks, attributes and configuration.

### Mute Video

This is to stop Video from Local Stream. The Stream immediately drops Video Track until unmuted.

To mute Video, send the following message:

```js
{
  "action": "mute-video"
}
```

### Unmute Video

This is to unmute Video in Local Stream. The Stream immediately adds Video Track.

To unmute Video, send the following message:

```js
{
  "action": "unmute-video"
}
```

### Mute Audio

This is to mute Audio from Local Stream. The Stream immediately drops Audio Track until unmuted.

To mute Audio, send the following message:

```js
{
  "action": "mute-audio"
}
```

### Unmute Audio

This is to unmute Audio in Local Stream. The Stream immediately adds Audio Track.

To unmute Audio, send the following message:

```js
{
  "action": "unmute-audio"
}
```

## Live Streaming

These set of actions are related to Live Streaming of ongoing Video Session to an RTMP Endpoint for content distribution to larger audience.

**Note**: These are Host only features. So, these messages must be sent from the Moderator/Host Side of UI only.

### Start Live Streaming

This is to start Live Streaming of ongoing Video Session to an RTMP Endpoint.

To start Live Streaming, send the following message:

```js
{
  "action": "start-live-streaming",
  "data": {
    "name": "Youtube",
    "rtmp_endpoint": "rtmp://a.rtmp.youtube.com/live2",
    "rtmp_key": "XOXOXO"
  }
}
```

**Data Object:**
|Data Object notification|Description|
|---|---|
| *name*|Plain Text to describe the Stream|
|*rtmp_endpoint*| The RTMP Endpoint URL where the stream to be sent|
|*rtmp_key* | The RTMP Key|

### Stop Live Streaming

This is to stop ongoing Live Streaming of the Video Session from all RTMP End Points.

To stop Live Streaming, send the following message:

```js
{
  "action": "stop-live-streaming"
}
```

## UI / UX

These set of actions are related to UI and UX of the Video Embed on ongoing Video Session.

### Change Video Layout

This is to change VIdeo Grid Layout either to Gallery View or Leader View at RTMP End Point and/or each End Point.

To change Layout, send the following message:

```js
{
  "action": "change-layout",
  "data": {
    "target": "rtmp",
    "layout": "leader"  }
}
```
**Data Object**:
|Data Object notification|Description|
|---|---|
|*target*| Values: rtmp, all. When “rtmp” is used, the layout is affected at RTMP End Point only. When “all” is used, the layout is affected at all End Points.|
|*layout*| Values: leader, gallery. The layout to be used.|

 ## Messaging

These set of actions are related to signaling and messaging among users in the Video Session..

### Send Custom Signaling

This is to send a custom data structure among all users in the Video Session. EnableX doesn’t work End Point and/or each End Point. EnableX only broadcast the message among users; doesn’t do anything else. Therefore, its a signaling means among users. Use limited size custom data structure to broadcast.

Define your data structure and send the following message for broadcasting:

```js
{
	"action": "signal",
	"data": {
		/* Define your custom object here */
	}
}
```

**Data Object**:
|Data Object notification|Type|Description|
|---|---|---|
|*data*| Object| All Keys are be defined by you to broadcast among users.|

# Notifications

Video Embed sends out notifications to Parent Window to notify various events, status of actions in the Video Session. Parent Window must subscribe to receive notification, otherwise notifications are not generated by the Video Embed.

Parent Window must listen to the Events and take appropriate action.

## Subscription

This notification group need not be subscribed. and area always available. These notifications are generated by Video Embed as a response of Notification Subscription and Subscription process.

### Notification Subscribed
This is to notify that Parent Window has successfully subscribed to receive one or more notification groups.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "notification-subscribed",
  "data": [
    "live-streaming",
    "room-connection"
  ]
}
```

**Data Object**: It is an array of notification groups to which the Parent Window has subscribed to receive.

|Data Object notification|Description|
|---|---|
|*live Streaming*||
|*room-connection*||

### Notification Unsubscribed

This is to notify that Parent Window has successfully unsubscribed from receiving one or more notification groups.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "notification-unsubscribed",
  "data": [
    "live-streaming",
    "room-connection"
  ]
}
```

**Data Object**: It is an array of notification groups to which the Parent Window has subscribed to receive.

|Data Object notification|Description|
|---|---|
|*live Streaming*||
|*room-connection*||


## Room Connection

This is a Room Connection Notification Group. This covers notification related to room connection, disconnection and auto-reconnection into the Room. To receive some of these notifications, Parent Page need to subscribe to room-connection Notification Group.

### Room Connected
This is to notify that the Video Embed is connected to Virtual Room for communication. Parent page needn’t subscribe to receive this notification.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "room-connected",
  "data": {
    "room_name": "John's Room",
    "conf_num": "XOXOXO"
  }
}
```

**Data Object**:
|Data Object notification|Description|
|---|---|
|*room_name* | Name of the Virtual Room|
|*conf_num*| – Conference Number of Session ID. It uniquely identifies the Video Session|

### Room Not Connected

This is to notify that the Video Embed is not connected to Virtual Room for communication. Parent page needn’t subscribe to receive this notification.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "room-not-connected",
  "data": {}
}
```

### Room Disconnected

This is to notify that the Video Embed is disconnected from the Video Session. No longer communication is feasible hence forth until the Embed rejoins or reconnects the Virtual Room. Parent page needn’t subscribe to receive this notification.

JSON Message: Parent Window receives the following notification

```js
{
	"notification": "room-disconnected",
	"data": {
		"message": "Reason for disconnection"
	}
}
```

You may get following reasons for disconnection:

- Session expired
- Room access denied
- Failed to reconnect
- Disconnected by Moderator
- Unexpected disconnection
- Normal disconnect

### Room Re-connected

This is to notify that the Video Embed is reconnected to the Virtual Room. The Embed resumed communication. Parent page needs to subscribe to 
*room-notification* group to receive this notification.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "room-reconnected"
}
```
## User Connection

This is a User Connection Notification Group. This covers notification related to user connection and disconnection. To receive some of these notifications, Parent Page need to subscribe to user-connection Notification Group.

### UserConnected

This is to notify that the a new user got connected to the Virtual Room.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "user-connected",
  "data": {
    "clientId": "XOXO",
    "name": "John",
    "role": "participant"
  }
}
```
**Data Object**:

|Data Object notification|Description|
|---|---|
|*clientId*| The Unique ID assigned to each user connected to Video Room.|
|*name*|Name of the user connected the Video Room.|
|*role*| -Role of the user. It may have the following enumerated data *moderator, participant, viewer, audience*|

### UserDisconnected

This is to notify that the a user got disconnected from the Virtual Room.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "user-disconnected",
  "data": {
    "clientId": "XOXO",
    "name": "John",
    "role": "participant"
  }
}
```

**Data Object**:

|Data Object notification|Description|
|---|---|
|*clientId*| The Unique ID assigned to each user connected to Video Room.|
|*name*|Name of the user disconnected from the Video Room.|
|*role*|Role of the user. It may have the following enumerated data *moderator, participant, viewer, audience*|

##  Stream Updates

This is a Stream Updates Notification Group. This covers notification related to local stream configuration, track, attribute updates. To receive one or all notification, Parent Page must subscribe to stream-updates Notification Group.

### Video Muted

This is to notify that the Video is muted or stopped in the Local stream.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "video-muted"
}
```

### Video Unmuted

This is to notify that the Video is unmuted or restarted in the Local stream.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "video-unmuted"
}
```

### Audio Muted

This is to notify that the Audio is muted or stopped in the Local stream.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "audio-muted"
}
```

### Audio Unmuted

This is to notify that the Audio is unmuted or restarted in the Local stream.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "audio-unmuted"
}
```

## Live Streaming

This is a Live Streaming Notification Group. To receive one or all notification, Parent Page must subscribe to live-streaming Notification Group.

### Live Streaming Started

This is to notify that the Live Streaming has started.

JSON Message: Parent Window receives the following notification

```js
{
    "notification": "live-streaming-started",
    "data": {
	"name": "Youtube",
	"rtmp_endpoint": "rtmp://a.rtmp.youtube.com/live2",
	"rtmp_key": "XOXOXO"
	}
}
```

**Data Object**:
|Data Object notification|Description|
|---|---|
|*name*| Plain Text to describe the Stream.|
|*rtmp_endpoint*| The RTMP Endpoint URL where the stream to be sent.|
|*rtmp_key*| The RTMP Key.|

### Live Streaming Stopped

This is to notify that ongoing Live Streaming of the Video Session to all RTMP End Points are stopped.

JSON Message: Parent Window receives the following notification

```js
{
    "notification": "live-streaming-stopped",
    "data": {}
}
```

## Media Access

This is a Media Access Notification Group. This covers notification related to Media Device Accessibility. These notifications are always available, Parent Page needn’t subscribe to the Notification Group.

### Media Access Denied

This is to notify that the Video Embed failed to get Media Device Access (Media Device is a general term covers Camera and Microphone Devices). An end point may or may not join Video Room if Media Device Access is denied.

JSON Message: Parent Window receives the following notification

```js
// When room not connected
{
  "notification": "media-access-denied",
  "data": {
    "message": "Media access denied. Room not connected."
  }
}

// When room is connected without Media Device Access
{
  "notification": "media-access-denied",
  "data": {
    "message": ""Mic and Camera access denied"
  }
}
```

### Camera Access Denied

This is to notify that the Video Embed failed to get Camera Device Access. An end point may or may not join Video Room if Camera Device Access is denied.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "camera-access-allowed",
  "data": {}
}
```
### Camera Access Allowed

This is to notify that the Video Embed is allowed access to Camera Device.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "camera-access-allowed",
  "data": {}
}
```

### Microphone Access Denied

This is to notify that the Video Embed failed to get Microphone Device Access. An end point may or may not join Video Room if Microphone Device Access is denied.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "mic-access-denied",
  "data": {}
}
```
### Microphone Access Allowed

This is to notify that the Video Embed is allowed access to Microphone Device.

JSON Message: Parent Window receives the following notification

```js
{
  "notification": "mic-access-allowed",
  "data": {}
}
```

## Messaging
This is a Messaging Group. This covers notification related to inter user messaging and signaling. Parent Page need to subscribe to “messaging” Notification Group to receive these notifications.

### Custom Signal Received
This is to notify that you have received a signal with custom data structure to be used by your Parent Window to use it anyway you want.

JSON Message: Parent Window receives the following notification

```js
{
	"notification": "signal-received",
	"data": {
		/* Custom data here */
	}
}
```
