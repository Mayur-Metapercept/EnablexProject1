---
title: "Requesting CDR for a Room and Period"
date: 
description:
type: "docs"
weight: 2
---
This API Route deploys a filter on the CDR Reporting. API call returns CDR for a given room and period. The specified date and Room ID format is described below in the URL Structure.
- [**API Route**](https://api.enablex.io/video/v2/cdr/room-period/{room_id}/{from-date}/{to-date}) 
- **HTTP Request**: GET
- **Date Format**: YYYY-MM-DD
- **Time Zone**: UTC
- [Try in Open API Tool](https://openapi.enablex.io/video/v2/api-docs/#/CDR/getCDRByRoomAndPeriod)

**Sample Request:**
```
GET https://api.enablex.io/video/v2/cdr/room/{room_id}  
Authorization: Basic XXXXXXX 
```
**Response JSON:**
```
{
     "result": "0",
     "cdr": [
         {
             "trans_date": "YYYY-MM-DDTHH:II:SS.mmmZ",
             "conf_num": "XXX",
             "call_num": "XXX",
             "call_log_id": "XXX",
             "room": {
                 "room_id": "XXXX",
                 "connect_dt": "YYYY-MM-DDTHH:II:SS.mmmZ",
                 "disconnect_dt": "YYYY-MM-DDTHH:II:SS.mmmZ",
                 "duration": 9999.999
             },
             "user": {
                 "ip": "1.1.1.1",
                 "name": "",
                 "role": "moderator",
                 "ref": "",
                 "agent": "okhttp/3.5.0",
                 "token": "",
                 "confName": ""
             },
             "sigserver": {
                 "connect_dt": "YYYY-MM-DDTHH:II:SS.mmmZ",
                 "ip": "",
                 "disconnect_dt": "YYYY-MM-DDTHH:II:SS.mmmZ",
                 "duration": 9999.999,
                 "hold_duration": 9.999
             },
             "published_track": {
                 "audio": "true",
                 "data": "true",
                 "video": "true",
                 "screen": "false",
                 "url": "false"
             },
             "usage": {
                 "subscribed_minutes": 9999.999,
                 "published_minutes": 9999.999
             },
             "app_id": "xyzxyzxyz",
             "cdr_id": "abcabcabc"
         }
     ]
 }
 ```
