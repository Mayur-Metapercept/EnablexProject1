---
title: "Disconnect from Break Out Room"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.disconnect()* method allows the user to disconnect from the Break Out Room.

**Class**: EnxRoom

**Method**: *EnxRoom.disconnect()* – No Parameter required.

*Event Listeners*:

- *breakout-room-disconnected* – Acknowledgment to the user when successfully disconnected from the Break-Out Room.
- *user-disconnected-breakout-room* – Notification to everyone in the Break-Out Room when a user gets disconnected from the Room.
```
breakout_room.disconnect();

// User is notified that he is disconnected from Break-Out Room
room.addEventListener("breakout-room-disconnected", function (event) {
	 
});

// Others are notified about the user disconnected from Break-Out Room
room.addEventListener("user-disconnected-breakout-room", function (event) {
	 
});
```