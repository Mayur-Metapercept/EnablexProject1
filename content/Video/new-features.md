---
title: "New Features"
date: 
description:
type: "docs"
weight: 2
---

**Speaker Device Selection**
EnableX introduces Speaker Device Selection API in its Web SDK for supported browsers only. Few existing APIs are modified to support Speaker or Audio-Out Device configuration.

Refer the following sections to know details of new and updated APIs:

- [Select Speaker Device](./get-media-devices.md)
- Use Speaker Device
    - [Initiate Room](./initiate-room.md)
    - [Join Room](./join-room.md)
- [Switch to another Speaker Device](./switch-speaker.md)

**Live Media Statistics**

EnableX provides live Media Statistical Data to an end-point. Developer may opt to receive statistics as JSON along with an Event or get overlay with Statistical Data on each Video Player.

For more information see, [Live Media Statistics](./live-media-statistics.md)

**In-Session Live Transcoding**
To address immediate transcoding requirement for some use cases with two party call where one joins with Audio+Video and other joins with Audio only, EnableX now does live-transcoding of 2 streams to provide single .webm file immediately at end of session. You need to define room with *single_file_recording:true*.

For more information see, [Create Room](./create-rooms.md)

**Media Zone Selection for a Room**
A Session is hosted in any available Media Zone within EnableX Cluster which is decided at run-time while assigning resources for a Session. EnableX now provides control to the Developers to choose a suitable Media Zone for a Session among available list of Zones.
For more information see, [Create Room](./create-rooms.md)

**Use Front Facing Camera**
Web Application used on Mobile Browser generally uses Back Side Camera of the Device. A facingMode option helps to use the Front Camera in Mobility Browser. 
For more information see, [Initiate Stream with specific Devices](./initiate-stream-with-specific-devices.md)

**Break-Out Room**
EnableX introduces Break-Out Room feature where one or more users in a Video Session move out to a Break-Out Room for discussion aside and then they join back.
For more information see, [Break Out Room](./break-out-room.md)

**Moderated Entry to a Room for Participants**
EnableX introduces Moderated entry to a Room for Participants through Room Settings called “knock”. In knock enabled rooms, participants are awaited and host is notified about the awaited user. Moderator decides whether to allow or deny entry for the awaited participants through respective Method Call.
For more information see, [Moderate Participants’ entry to a Session](./moderated-entry-room-participants.md)

**Participants wait for Moderator to join first**
A Host now may now force all Participants to wait for him to join first. Until then, no one sees or communicates with others. This is achieved through Room Settings called “wait-for-moderator”. When moderator joins, all awaited participants automatically joins too. Subsequently all new participants joins automatically without having to wait.
For more information see, [Create Room](./create-rooms.md)

**Improvements**
EnableX v1.9+ comes with long list of improvements:
- **Low Bandwidth Signaling**: EnableX has improved significantly to handle Low Bandwidth Signaling and Connection.
- **Audio Iceland Issue**: Added few fixes for Audio Iceland Issue.