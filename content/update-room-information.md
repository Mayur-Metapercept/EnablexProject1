---
title: "Update Room Information"
date: 
description:
type: "docs"
weight: 2
---
If you need to update Room information you may do so with this API Route. The JSON Payload contains only those keys that are permissible to update. Note that any update on the Room definition will take effect only on subsequent sessions of the Room. To update schedule room, you should do so 15 minutes prior to the scheduled start time.
- [API Route](https://api.enablex.io/video/v2/rooms/{room_id})
- **HTTP Request**:
- [Try Open API](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/updateRoomById)
**Sample Request**
```
PATCH https://api.enablex.io/video/v2/rooms/{room_id}
Authorization: Basic XXXXXXX
Content-Type: application/json

{
      "name": "Topic or Room Title",
      "settings": {
          "participants": "15",
          "auto_recording": true 
      }            
 }
 ```
 **Response**
 ```
 {
     "result": 0    
}
```