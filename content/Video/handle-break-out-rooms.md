---
title: "Handle All Destroyed Break Out Rooms"
date: 
description:
type: "docs"
weight: 2
---
Availability: Web SDK 2.0.1+

The *EnxRoom.destroyAllBreakOutSession()* method allows the moderator to destroy all the Breakout Room sessions. When all the Breakout Room sessions get destroyed, the Parent Room is automatically resumed and unmuted.

**Class**: EnxRoom

**Method**: *EnxRoom.destroyAllBreakOutSession()* – No Parameter required

**Event Listeners**:

- *breakout-room-destroyed* – Notification to the owner when the Breakout Room gets destroyed.
```
room.destroyAllBreakOutSession(); 

room.addEventListener("breakout-room-destroyed", function (event) {
	 
});
```