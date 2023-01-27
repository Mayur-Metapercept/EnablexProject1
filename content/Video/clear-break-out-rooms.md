---
title: "Clear All Break Out Rooms"
date: 
description:
type: "docs"
weight: 2
---
Availability: Web SDK 2.0.1+

The *EnxRoom.clearAllBreakOutSession()* method allows the participant to clear all Break-Out Rooms. The Participant gets disconnected from all breakout instances and resumes with the Parent Room.

**Class**: *EnxRoom*

**Method**: *EnxRoom.clearAllBreakOutSession()* – No Parameter required.

**Event Listeners**:

- *breakout-user-disconnected* – Notification to the Moderator/Owner of the Break-Out Room with information of the disconnected participant.
```
room.addEventListener("breakout-user-disconnected", function (event) {
	/* event is JSON with information of disconnected participant		
	{	type: 'breakout-user-disconnected', 
		message: {
			room_id: "String",
			client_id: "String"
		}
	}
	*/
});
```