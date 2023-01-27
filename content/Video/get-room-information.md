---
title: "Get Room Information"
date: 
description:
type: "docs"
weight: 2
---
To get a complete room definition of a given Room, you may use this Route. Note the API Route has the room-id appended
- [API Route](https://api.enablex.io/video/v2/rooms/{room_id})
- **HTTP Request**: GET
- [Try Open API Tool](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/getRoomById)

**Sample Request**
```
GET https://api.enablex.io/video/v2/rooms/{room_id}
Authorization: Basic XXXXXXX 
```
**Response**
```
{
  "result": 0,
  "room": {
    "name": "Topic or Room Title",
    "owner_ref": "xyz",
    "settings": {
      "description": "Descriptive text",
      "mode": "group",
      "scheduled": false,
      "adhoc": false,
      "duration": 50,
      "moderators": "2",
      "participants": "10",
      "billing_code": "",
      "auto_recording": false,
      "quality": "HD",
      "canvas": true,
      "screen_share": true,
      "max_active_talkers": true,
      "role_based_recording": {
        "moderator": "audiovideo",
        "participant": "audio"
      },
      "live_recording": {
        "auto_recording": true,
        "url": "rtmp-client.enablex.io/?token="
      }
    },
    "sip": {
      "enabled": true,
      "pin": 99999,
      "meeting_id": 99999
    },
    "data": {
      "custom_key": ""
    },
    "created": "2018-07-12T11:30:24.851Z",
    "room_id": "xxxxxxxxxxxxxxx"
  }
}
```