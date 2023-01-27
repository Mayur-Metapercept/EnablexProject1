---
title: "Requesting Archives for a Room"
date: 
description:
type: "docs"
weight: 2
---
This API Route provides filter for Archives Reporting for a Room. Note the usage of *room_id* in the URL Structure.

- [**API Route**](https://api.enablex.io/video/v2/archive/room/{room_id}) 
- **HTTP Request**: GET
- [Try in Open API Tool](https://openapi.enablex.io/video/v2/api-docs/#/Archive/getArchiveByRoom)

**Sample Request:**
```
GET https://api.enablex.io/video/v2/archive/room/{room_id}  
Authorization: Basic XXXXXXX
```
**Response JSON:**
```
{
     "result": "0",
     "archive": [
         {
             "_id": "XXX",  
             "trans_date": "YYYY-MM-DDTHH:II:SS.mmmZ",
             "conf_num": "XXXXX",
             "app_id": "XXX",
             "room_id": "XXX",
             "recording": [
                 {"url": "https://FQDN/path/file.mkv"} 
             ],
             "transcoded": [
                 {"url": "https://FQDN/path/file.mp4"} 
             ],
             "chatdata": "https://FQDN/path/chatdata.json",
             "metadata": "https://FQDN/path/metadata.json"  
         } 
     ]
 }
 ```
 For more details on recorded files security, refer to the [Recording Files Security Documentation](./video-recording-file-security.md)
