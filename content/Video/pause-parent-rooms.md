---
title: "Pause or Resume Parent Room"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.pause()* method allows the user to pause the Parent Room after joining the Break-Out Room.

The *EnxRoom.resume()* method is used to resume the Parent Room if it was paused while joining the Break-Out Room.

**Method**: 

- EnxRom.pauseRoom(Callback)
- EnxRom.resumeRoom(Callback)

**Parameters**:

- Callback – To know status of the pause or resume API call.
```
room.pauseRoom(function(resp) {
	// resp carries status
	/*
	{	"msg": "Room paused",
		"result": 0
	}
	*/
}

room.resumeRoom(function(resp) {
	// resp carries status
	/*
	{	"msg": "Room resumed",
		"result": 0
	}
	*/
}
```
**Error Codes or Exceptions**

| Code     | Description |
| ----------- | ----------- |
| 1138      | Internal Server Error.       |