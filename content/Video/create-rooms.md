---
title: "Create Room"
date: 
description:
type: "docs"
weight: 2
---
When a Room is created, it merely creates a database entry with a room-id for EnableX platform. The room-id is required to carry out CRUD operations for the Room.

- [**API Route**](https://api.enablex.io/video/v2/rooms)
- **HTTP Request**: **POST**
- [Try Open API Tool](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/createRoom)

**Sample Request**
```
{
  "name": "Topic or Room Title",
  "owner_ref": "xyz",
  "settings": {
    "description": "Descriptive text",
    "mode": "group",
    "scheduled": false,
    "adhoc": false,
    "duration": 30,
    "moderators": "1",
    "participants": "5",
    "billing_code": "",
    "auto_recording": false,
    "quality": "SD",
    "canvas": false,
    "screen_share": false,
    "abwd": true,
    "max_active_talkers": 4,
    "knock": false,
    "wait_for_moderator": false,
    "media_zone": "US",
    "single_file_recording": false,
    "role_based_recording": {
      "moderator": "audiovideo",
      "participant": "audio"
    },
    "live_recording": {
      "auto_recording": true,
      "url": "https://your-custom-view-url"
    }
  },
  "sip": {
    "enabled": false
  },
  "data": {
    "custom_key": ""
  }
}
```

**JSON Raw Body Payload on Request**
| Name     | Description | Required | Value |
| ----------- | ----------- | ----------- | ----------- |
| name      | Name of Room or Topic of Meeting | Yes | Alpha Numeric |
| owner_ref   | Room Owner ID of Reference. You may use it from your Information System. Post Call Reports include this data for your reference or reporting.        | Yes | Alpha Numeric |
| settings    | Type of Room. Not editable. Lecture mode auto-implements restriction on stream publishing by Participants and Moderator gets exclusive control of the floor.        | Yes | Enumerated Values: group (default), lecture |
| settings.scheduled   | Whether the room is a permanent room or scheduled for a specific duration. Setting it false creates a permanent room. Not editable.        | Yes | Boolean Value: true, false (default) |
| settings.adhoc   | Whether the room is a Adhoc room i.e. for one time use. To create a Adhoc room, you need to set it to true along with settings.scheduled as false. Not editable.       | Yes | Boolean value: true, false (default) |
| settings.scheduled_time   | Only for scheduled room. This is scheduled start time of the Room. Token will be issues before 15 minutes of start time. Token will not be issued beyond scheduled duration if no participant is available in the room.        | | Date Format: YYYY-MM-DD HH:II:SS, Time Zone: UTC |
| settings.duration   | Total Duration of Room. Its required only for Scheduled Room, for Adhoc and Permanent room its irrelevant.        | Yes for Scheduled Room | Positive Number. No upper limit. |
| settings.moderators  | Total Number of Moderator's allowed in the Room. If omitted, 1 moderator is set by default.        | Yes | Numeric. 1-5, Default: 1 |
| settings.participants |  Total Number of Participants allowed in the Room. This value doesn’t count the Moderator.| Yes | Numeric |
|  settings.auto_recording  | If auto-recording is enabled, recordings gets started as soon as any participant publishes into the room. In Auto-Recording enabled sessions, Recording can be stopped and restarted manually using function calls.  | No | Boolean Value: true, false (Default) |
| settings.screen_share   | If you need Screen Share in a room, you may enable it.        | No | Boolean Value: true (Default), false |
| settings.canvas   |  If you need Canvas streaming (Streaming with contents of HTML5 Canvas Object) in a room, you may enable it.        | No | Boolean Value: true, false (Default) |
| settings.knock   | If you need participant to wait before he is allowed by moderator to join a session, then enable knock feature.        | No | Boolean value: true, false (Default) |
| settings.wait_for_moderator   | If you need participants to wait until a moderator joins the session. Once Moderator joins once, all waiting participants and new participants will be allowed to get into the session.        | No | Boolean value: true, false (Default) |
| settings.quality   | If your application setting and subscription allows HD streaming, you may opt to use either HD, SD or LD for a room. If not used, EnableX allows subscription based stream quality by default.        | No | Enumerated Values: HD, SD, LD   |
| **Note**: Quality LD has been introduced with Release 1.5.3.Video Resolutions: HD: Min 320X180@30fps. Max 1280X720@30fps, SD: Min 320X180@30fps. Max 640X480@30fps, LD: Min 80X45@30fps. Max 640X360@30fps |
| settings.billing_code   | This is for Applications own reference.        | No | Alpha Numeric |
| settings.abwd   | If you need disable ABWD (Auto-Bandwidth Detection) in a Room.        | No | Boolean Value: true (default), false |
| settings.facex   | If you need carry out Face Recognition Analysis in this Room.        | No | Boolean Value: true (default), false |
| settings.max_active_talkers   | You may define how many maximum streams you need in Active Talkers. Optional. Maximum 16 Active Talkers may be define.        | No | Number Range: 1-16, Default 6 |
| settings.single_file_recording   | You may enable this feature to get live-transcoding done in a room defined with 2 users only where a user comes with audio/video and other user comes with audio only. EnableX provides .webm file just after session ends. This is typically used by KYC Applications.        | No | Boolean value: true, false (Default) |
| settings.role_based_recording   | JSON Object to define if recording file needs to exclude Video Track from user’s stream in the Rool. By default, audio and video track for all users are recorded as received at Media Server. If required, audio only recording may be enabled for users joined with “participant” and/or “moderator” role.       | No | This Object may have one or both of the following keys { "moderator": "audiovideo", "participant": "audio" }. | 
|  |  |  | Here: moderator is Optional. String. 
|  |  |  |Enumerated values: audio, audiovideo. Default. audiovideo. participant: Optional. String. 
|  |  |  |Enumerated values: audio, audiovideo. Default. audiovideo, Value: audiovideo – It will record both Video with Audio Track, Value: audio – It will record only Audio Track. Video Track will be skipped.|
| settings.live_recording   | JSON Object to create a transcoded file in a live session without recording individual streams. You can enable live recording and define the url.        | No | Boolean value: true, false (Default) |
| settings.media_zone   | You may decide a Media Zone for the Room among available Zones. Note that its subscription controlled feature. By default, EnableX decides Media Zone at run time.        | No | Enumerated Values: IN (for India), SG (For Singapore), US (For United States). XX (Default – EnableX assigns Media Zone) |
| settings.watermark   | This enables Watermarking of recorded files for the Room.    | No | Boolean Value: true, false (Default) |
| sip   | JSON Object with SIP Configuration Keys. Value of each Key within sip will be validated to have legit value.        | | |
| enabled   | This is to enable SIP Connection to the Room.       | No  | Boolean Value: true, false (Default) |
| data   | JSON Object to carry custom data. You can define your own Keys in this object. None of the Keys and their values are validated by EnableX.        | | |

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