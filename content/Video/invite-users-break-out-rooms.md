---
title: "Invite Users to join a Break-Out Room"
date: 
description:
type: "docs"
weight: 2
---

The *EnxRoom.inviteToBreakOutRoom()* method allows the Creator or Owner of a Break-Out Room to invite one or more users from the Parent Room to join the Break-Out Room.

This method must be invoked from the Parent Room and NOT from the Break-Out Room.

**Class**: *EnxRoom*

**Method**: *EnxRoom.inviteToBreakoutRoom(invitee, Callback)*

**Parameters**:
- *invitee* – JSON Object with invitation details.
    - *clients* – Array of Client IDs of users to be invited.
    - *room_id* – String. Room ID of the Break-Out Room to which the users are being invited.
    - *force_join* – Boolean. If set to true, the invited participant will be forced to join the Break-Out Room. Availability: Web SDK 2.0.1+.
- *Callback* – To get result of invitation process.

**Event Listeners**

- *join-breakout-room* – Notification sent to the invited users when they are invited to join a Break-Out Room.
- *breakout-room-joining* – Notification sent to the invited Participant that he has to join the breakout room.
- *breakout-room-connected* – Notification sent to the invited Participant when he gets connected to the Break-Out Room.

```
invitee = {
	"clients" : "[clientId1, clientId2]", 
	"room_id" : "RoomID",
        "force_join" : true
};

room.inviteToBreakoutRoom(invitee, function(resp) {
	// resp is the result of invitation process, e.g.
	/*		
	{	"msg": "Success",
		"result": 0,
	}
	*/
});
 
// Users get invite to join Break-Out Room. When "force_join: false" is used or omitted
room.addEventListener("join-breakout-room", function (event) {
	// event carries the invitation details, e.g.
	/*		
	{	type: 'join-breakout-room', 
		message: {
			room_id: "String",
			requestor: "String"
		}
	}
	*/

	// User may join room now. This is optional.  
	// User may be presented with UI to either Join or Reject
	// In case, he needs to join, Read JoinBreakOutRoom() later in the document
	Joinee = {
		"role" : "participant", 
		"room_id" : "RoomID"
	};

	StreamInfo = {
		"audio": true, 
		"video" : false,
		"canvas" : false,
		"screen" : false
	};
	
	room.joinBreakOutRoom(Joinee, StreamInfo, function(resp) {
		// Status 
	});
});

// Users get notification to join directly when invited with  "force_join: true".
room.addEventListener("breakout-room-joining", function (event) {
	// event carries the invitation details, e.g.
	/*		
	{	type: 'breakout-room-joining', 
		message: {
			room_id: "String",
			requestor: "String"
		}
	}
	*/

}

// Users get notification when connected with Break-Out Room with invited with "force_join: true".
room.addEventListener("breakout-room-connected", function (event) {
	// event carries the room meta 
	// Ref: https://www.enablex.io/developer/video-api/client-api/appendix/#room-meta

}
```