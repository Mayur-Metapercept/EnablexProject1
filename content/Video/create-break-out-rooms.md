---
title: "Create Break-Out Room"
date: 
description:
type: "docs"
weight: 2
---

The *EnxRoom.createBreakOutRoom()* method is used to create a Break-Out Room.

**Method**: *EnxRoom.createBreakoutRoom(RoomDefinition, Callback);*

**Parameters**:
- *RoomDefinition* – Required. JSON Object with Room definition parameters defined as following keys:
    - *participants* – Numeric. Required. Total number of Participants in the Break-Out Room. Range: Min: 2. Max: max_active_talkers of Parent Room – 1
    - *audio* – Boolean. Required. Set to true to enable Audio Communication in Break-Out Room.
    - *video* – Boolean. Required. Set to true to enable Video Communication in Break-Out Room. (This is currently not supported).
    - *canvas* – Boolean. Required. Set to true to enable Canvas Streaming in Break-Out Room.
    - *share* – Boolean. Required. Set to true to enable Screen Share in Break-Out Room.
    - *max_rooms* – Numeric. Required. The total number of Break-Out rooms to be created.
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

room.createBreakoutRoom(RoomDefinition, function(data) {
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
**Error Codes or Exception**

| Code        | Description |
| ----------- | ----------- |
| 1724        | Participant Count not found.|
| 1725        | Participant Count is more than Parent Room Size.|
| 1726        | Permissible limit to create Break-Out Room has exceeded        |
| 1729        | Failed to generate Token.        |
| 1731        | Failed to create Break-Out Room.        |
| 1734        | Required parameter missing. Participant count is mandatory        |