---
title: "Reject Break Out Room Invitation"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.rejectBreakOutRoomInvite()* allows the invited user to reject the invitation to join a Break-Out Room.

**Class**: EnxRoom

**Method**: EnxRoom.rejectBreakOutRoomInvite(roomId, callback); 

**Parameter**:

- *roomId* – The Break-Out Room identifier to which the user is invited.
- *callback* – To know the result of the reject Break-out Room invite.

**Event Listeners**:

- *breakout-invite-rejected* – Notification to the moderator when a user rejects an invitation to a Break-Out Room.
```
// User rejects break-out room invitation.
EnxRoom.rejectBreakOutRoomInvitation(roomId, function(resp) {
	// Status 
}); 

// The moderator is notified when a user rejects an invitation to a Break-Out Room
room.addEventListener("breakout-invite-rejected", function (result) {
	
});
```