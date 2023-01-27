---
title: "Moderate Participants’ entry to a Session"
date: 
description:
type: "docs"
weight: 2
---

In a [knock-enabled Room](./create-rooms.md), a user needs to wait until the Moderator grants them permission to join the Session. The *EnxRoom.approveAwaitedUser()* method allows the Moderator to approve a user’s entry and *EnxRoom.denyAwaitedUser()* method is used to decline a user’s entry to the Session.
**Methods**:

- *EnxRoom.approveAwaitedUser(ClientID, Callback)*
- *EnxRoom.denyAwaitedUser(ClientID, Callback)*

**Event Notifications**:

- *user-awaited* – Notification to the Moderator when a user awaits their permission to join Room.
- *room-allowed* – Notification to the user when the user is permitted to join Room after waiting on a wait-for-moderator or knock-enabled Room.
```
// Moderator is notified about awaited user
room.addEventListener("user-awaited", function(event, user) {
      // Client Info: user.clientId
      // Create UI for Moderator Interaction to allow or deny 

	// To allow
	room.approveAwaitedUser(clientId, function(success, error) {
	     // Check Success / Error result
	});

	// To deny
	/*
	room.approveAwaitedUser(clientId", function(success, error) {
	     // Check Success / Error result
	});
	*/
});
```