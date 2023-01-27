---
title: "Interactive Session with 250 Users"
date: 
description:
type: "docs"
weight: 2
---
EnableX now supports up to 250 users in Interactive Video Sessions. With Active Talkers in effect, endpoints receive a maximum of 16 most actively talking user’s videos at any given time. As other users talk, their videos will become part of the Active Talkers List, dropping others from the list.
**Note**:
- Interactive Video Sessions are held in Group Mode that is, a Room defined with `{ "settings:: { "mode: "group"}}`.
- Users in interactive sessions are calculated based on the total of Moderators and Participants in the Session. Users with the “Viewer” role are excluded.