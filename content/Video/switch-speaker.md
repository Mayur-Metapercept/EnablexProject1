---
title: "Switching Speaker"
date: 
description:
type: "docs"
weight: 2
---

The *EnxRoom.switchSpeaker()* method is used to switch to a different Speaker to play Audio.

**Method**: *EnxRoom.switchSpeaker(speakerId, Callback)*

**Parameters**:

- *speakerId* – DeviceId of the new Speaker. q
- *Callback* – Callback to handle status of the switching process.

```
room.switchSpeaker(newSpeakerId, function(res) {
         if(res.result == 0) {
             // Switching successful   
         }
         else {
             // Failed to switch
         }
 });
 ```