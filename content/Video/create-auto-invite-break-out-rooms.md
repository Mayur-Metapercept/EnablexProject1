---
title: "Create Break-Out Room and Auto-Invite Users"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.createAndInviteBreakoutRoom()* is used to support certain use-cases where auto-assignment of users into different Break-Out Rooms is required. This method creates a Break-Out Room with given specifications and invites users to join a Break-Out Room randomly depending on the Room’s capacity.

**Class**: *EnxRoom*

**Method**: **EnxRoom.createAndInviteBreakoutRoom(RoomDefinition, Callback)**

**Parameters**:

- *RoomDefinition* – JSON object with Room definition parameters as explained in [Create Breakout Room](./create-break-out-rooms.md).
- *Callback* – To get result of Create Break-Out Room as JSON Array
```
RoomDefinition = {
	"participants": 2, 
	"audio": true,
	"video": false, 
	"canvas": false, 
	"share": false, 
	"max_rooms": 1
};

room.createAndInviteBreakoutRoom(RoomDefinition, function(data) {
	// data is JSON with created Break-Out Room Information, e.g.
	/*		
	{	msg: {​​
			rooms: [ 
				xxx, xxx
			]
		},
		result: 0
	}
	*/
});
```