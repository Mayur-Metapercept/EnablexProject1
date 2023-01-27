---
title: "Mute or Unmute Parent Room"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.muteRoom()* method allows the user to mute Audio and/or Video of the Parent Room after joining the Break-Out Room.

The *EnxRoom.unmuteRoom()* is used to unmute Audio and/or Video of the Parent Room after disconnecting from Break-Out Room and resuming the Parent Room.

**Class**: EnxRoom

**Methods**: 

- *EnxRoom.muteRoom(muteInfo, Callback)*
- *EnxRoom.unMuteRoom(unmuteInfo, Callback)*

*Parameters*:

- *mutetInfo* – JSON object with options to mute Audio and Video separately.
    - *audio* – Boolean. Set true mute Audio.
    - *video* – Boolean. Set true to mute Video.
- *unmuteInfo* – JSON Object with options to unmute Audio and Video separately.
    - *audio* – Boolean. Set true unmute Audio.
    - *video* – Boolean. Set true to unmute Video.
- *Callback* – To know status of the API call.
```
MuteInfo = {
	"audio" : true, 
	"video" : true
};

UnmuteInfo = {
	"audio" : true, 
	"video" : true
};

room.muteRoom(MuteInfo, function(resp) {
	// resp carries status
	/*
	{	"msg": "Room muted",
		"result": 0
	}
	*/
}

room.unMuteRoom(function(resp) {
	// resp carries status
	/*
	{	"msg": "Room unmuted",
		"result": 0
	}
	*/
}
```