---
title: "Break-Out Room: Web SDK – Video API"
date: 
description:
type: "docs"
weight: 2
---
Break-Out Rooms allow users to participate in a discussion outside of the main Video Room that is the Parent Room.

**Table of Contents**
- [Create Break-Out Room](./create-break-out-rooms.md)
- [Invite Users to join a Break-Out Room](./invite-users-break-out-rooms.md)
- [Create Break-Out Room & Auto-Invite Users to join](./create-auto-invite-break-out-rooms.md)
- [Join Break-Out Room](./join-break-out-rooms.md)
- [Reject Break-Out Room Invitation](./reject-break-out-rooms.md)
- [Pause/Resume Parent Room](./pause-parent-rooms.md)
- [Mute/Unmute Parent Room](./mute-parent-rooms.md)
- [Disconnect from Break-Out Room](./disconnect-break-out-rooms.md)
- [Clear All Break-Out Rooms](./clear-break-out-rooms.md)
- [Handle All Destroyed Break-Out Rooms](./handle-break-out-rooms.md)

The process of breaking-out takes place in the following manner:

- A creator or owner of the Break-Out Room invites one or more users from the Parent Room to the Break-Out Room.
- The invited users get notified about the request and need to accept the request to join the Break-Out room.
- Users moving out of the Parent Room are treated as “paused” users in the Parent Room until they return.

The implementation of Break-Out Room must be carried out with the following considerations:
- Break-Out Room is available in Group Mode room only, not in Lecture Mode.
- Break-Out room can be created by a user from the Parent Room only. A user cannot create another Break-Out Room while being within a Break-Out Room.
- A Break-Out Room can be created with a limit to the maximum allowed participants in it. In any case, the maximum allowed participants in the Break-Out Room must be less than the maximum Active Talkers in the Parent Room.
- Break-Out room currently supports only Audio Call with Screen Share and Canvas Streaming support.
- Maximum 10 Break-Out Rooms are allowed for a Parent Room.