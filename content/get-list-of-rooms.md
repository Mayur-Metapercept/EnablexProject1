---
title: "Get a list of Rooms"
date: 
description:
type: "docs"
weight: 2
---
To get a complete list of Rooms created within an Application you may use this Route
- [API Route](https://api.enablex.io/video/v2/rooms)
- **HTTP Request:**GET
- [Try Open API](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/getRoomList)
**Sample Request**
```
GET https://api.enablex.io/video/v2/rooms
Authorization: Basic XXXXXXX  
```
**Response**
```
{
     "result": 0,
     "rooms": [{
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
	     "max_active_talkers": 6
         },
         "sip" : {
             "enabled": false
         },
         "data": {
             "custom_key": ""
         },
         "created": "2018-07-12T11:30:24.851Z",
         "room_id": "xxxxxxxxxxxxxxx"
     }]
 }
 ```