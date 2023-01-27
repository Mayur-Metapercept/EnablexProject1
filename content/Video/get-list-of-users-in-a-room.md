---
title: "Get list of users in a Room"
date: 
description:
type: "docs"
weight: 2
---
If a Room is active that is room with ongoing session; you may get a list of all users (participants + moderator) connected to the Room using this API call. Note that if room is not active, the API call returns a null list.

- [API Route](https://api.enablex.io/video/v2/rooms/{room_id}/users)
- **HTTP**: GET
- [Try Open API](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/getRoomUsers)

**Sample Request**
```
GET https://api.enablex.io/video/v2/rooms/{room_id}/users 
Authorization: Basic XXXXXXX  
```
**Response**
```
{
     "result": 0,
     "total": 1,
     "users": [
         {
         "name": "User Name",
         "user_ref": "xxx",
         "role": "participant",
         "permissions": {
             "publish": true,
             "subscribe": true,
             "record": false,
             "stats": true,
             "controlhandlers": true
             }
         } 
     ]
 }
 ```
 