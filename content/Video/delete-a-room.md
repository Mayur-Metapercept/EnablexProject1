---
title: "Delete a Room"
date: 
description:
type: "docs"
weight: 2
---
You can delete a Room using this API call only if the Room is not an active Room that is without any ongoing session in it.

- [API Route](https://api.enablex.io/video/v2/rooms/{room_id})
- **HTTP**: DELETE
- [Try Open API](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/deleteRoom)

**Sample Request**
```
DELETE https://api.enablex.io/video/v2/rooms/{room_id} 
Authorization: Basic XXXXXXX 
```
**Response**
```
{
     "result": 0    
}
```