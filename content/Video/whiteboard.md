---
title: "Whiteboard"
date: 
description:
type: "docs"
weight: 2
---
# Overview
EnableX Whiteboard is an Independent Library shared over Github and Developer Center to help EnableX Developers easily deploy a Whiteboard with streaming and collaboration among participants of a session.

The EnableX Whiteboard has all basic tools inbuilt. It is developed using Open Source [Fabric.js](http://fabricjs.com/). In case you look to extend it and create richer set of Tools, you are free to do so using Fabric.js library.

![Overview](./whiteboard-overview.png)

# How to Integrate?
- Download the EnableX Whiteboard Library.
- Extract it. Move the *EnxWB.js* and *EnxWB.js.map* files to a designated folder within Virtual Root.
- Use the *EnxWB.js* file in your HTML through *< Script >* Tag.
- Refer the following section of document to know how to initiate, create, stream and collaborate Whiteboard among other participant of Session.
# Methods
## Initiate Whiteboard
Create an Object of *EnxWb* Class with a JSON Payload to define Whiteboard UI Components.
```
var wbObject  =  new EnxWb(
	{	canvasId: 'wb',		// id of the Canvas DOM Element 
		initialWidth: 1000,
		initialHeight: 500,
		scheme : 'default'
	}
);
```
**Parameter**: A JSON Object, attributes explained below:
- *canvasId*: The HTML CANVAS Element ID which will be used with the Whiteboard.
- *initialWidth*: Width of the Whiteboard in pixel.
- *initialHeight*: Height of the Whiteboard in pixel
- *scheme*: It’s a scheme / template definition of Whiteboard UI Components. You can use default scheme. In case you want to re-define, use custom scheme. And, when you use custom scheme, you need to define each UI component separately using a new object called custom in the JSON payload. E.g.
- *custom*: Optional. Custom Scheme definition object, in case you are usin scheme=custom.
```
Var wbObject  =  new EnxWb(
	{	canvasId: 'wb', // id of the canvas 
		initialWidth: 1000,
		initialHeight: 500,
		scheme : 'custom',
		custom: {
			bgColor : 'red',		/* WB Backbround */
			toolbarBGColor : 'black',	/* Toolbar Background */
			brushColor:'black',		/* Default Brush Color */
			icon : {			/* Toolbar Icon definition */
				size: 'medium', /* Enum: small,large,medium */
				type: 'rounded-square', /* Enum:  square,rounded-square */
				BGColor: '#f3f3f3',	/* Tool Background */
				FGColor: '#000000',	/* Tool Foreground */
				border: '1px solid grey'/* Tool Border */
			}
		}
	}
);
```
# Create Whiteboard
You need to draw the Whiteboard to get make it appear in the HTML DOM using the *EnxWb.create()* method.

**Method**: *EnxWb.create( EnxRoom-Object )
*
**Parameter**: *EnxRoom-Object*: It’s the Room Object with which the Whiteboard to get connected to for streaming and collaboration.
```
wbObject.create(roomObject);
```
# Start / Stop Whiteboard Streaming
If you want to start streaming your Whiteboard, the Whiteboard contents will be viewable to remote participants as video stream and will be playable in a Video Player. The Streamed Whiteboard may also be recorded for future reference.
**Methods**:

- *EnxWb.startStreaming()* – To start streaming
- *EnxWb.stopStreaming()* – To stop streaming
```
wbObject.startStreaming();
wbObject.stopStreaming();
```
**Note**: The Whiteboard Toolbar has toggle buttons to start/stop streaming. The methods explained above are called by clicking the buttons. However, these methods accessible to you to create your own UI to start / stop streaming.
# Start / Stop Whiteboard Collaboration
If you want to collaborate Whiteboard with other participants, they will also be able to use the Whiteboard to edit/collaborate in it. When you share the Whiteboard with others, the UI Component appears in the View in HTML DOM.
**Methods**:

- *EnxWb.startCollaboration()* – To start collaboration with others
- *EnxWb.stopStreaming()* – To stop collaboration with others
```
wbObject.startCollaboration();
wbObject.stopCollaboration();
```
**Note**: The Whiteboard Toolbar has toggle buttons to start/stop Whiteboard Collaboration. The methods explained above are called by clicking these buttons. However, these methods accessible to you to create your own UI to start / stop Collaboration.
# Whiteboard Collaboration with designated Participant
If you want to collaborate Whiteboard with specific participant, he will also be able to use the Whiteboard to edit/collaborate in it. When you share the Whiteboard with a participant, the UI Component appears in the View in HTML DOM at designated Participants’ end-point.
**Method**: EnxWb.shareWith(clientId) – To start collaboration with participant specified by clientId parameter.
**Parameter**: clientId– Client ID of the participant whom you wish to grant Collaboration Rights.
```
wbObject.shareWith(clientId);
```
**Note**: When you collaborate Whiteboard with all participants; you still need to use the *shareWith()* method to share the whiteboard with any new participant joining the session after the initial *startCollaboration()* was invoked. To do so, refer the following sample code:
```
// A new user connected. user JSON has user information
room.addEventListener("user-connected", function(event) {
     // Share the Whiteboard for Collaboration
     wbObject.shareWith(event.clientId);
});
```
