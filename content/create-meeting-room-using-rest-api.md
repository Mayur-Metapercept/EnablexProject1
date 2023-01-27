---
title: "Create Meeting Room Using Rest API"
date: 
description:
type: "docs"
weight: 2
---
Video Embed URL has embedded Room-ID for Virtual Sessions. Your Application’s business logic and workflow might need many rooms to meet your requirement. Know how you create more rooms of different kind and how to embed them into your EMBED URL to get connected to different Virtual Rooms.

A Video conferencing session takes place in the Meeting Room hosted on the EnableX server. A Room is a virtual meeting space within the EnableX platform to host real-time communication sessions. It facilitates communication among participants through Audio, Video & Chat.

The communication between your Application Server and the EnableX server is carried out via Rest API, which is also known as Server API. Access Credentials **APP_ID** and **APP_KEY**, which you get at the time of creating a Project, must be passed as Authorization Header for accessing the Server APIs.
![Communication](./create-meeting-room-1.png)

You can create a Meeting Room request by calling Server/Rest API through Meeting Room URL (see Example 1). To establish the room connection, IFRAME Embed URL requires a Meeting Room ID. Once the connection gets established, the IFRAME Embed starts playing Participant’s Videos on your platform.
**Example 1: Meeting URL Explanation**
1[Meeting URL](./meeting-url.png)

# Create a Room to get Room ID
To create a Meeting Room URL, you first need to create a Room and fetch the Room ID. You can [Create a Room using a Server API](./create-rooms.md) and the EnableX server responds with the JSON Payload containing the unique “room-id”. There are three different types of Meeting Rooms that can be created: Permanent, Scheduled, and Ad-hoc.

## Permanent Room
It is a meeting room that always remains available for use once created. You can start it anytime and schedule it for further use in the future. Use the following Settings in JSON Payload for API Call to create Permanent Room:

*{"settings": {"scheduled": false, "adhoc": false}}*

**Example 2: API Call to create Permanent Room**
```
POST https://api.enablex.io/video/v1/rooms
Content-Type: application/json
Authorization: Basic XXXXXXXX
 
{
  "name": "My Permanent Room",
  "owner_ref": "XOXO",
  "settings": {
    "description": "My Permanent Room",
    "mode": "group",
    "scheduled": false,
    "adhoc": false,
    "duration": 30,
    "moderators": "1",
    "participants": "3",
    "quality": "SD",
    "canvas": false,
    "screen_share": false,
    "abwd": true,
    "max_active_talkers": 4
  } 
}
```
EnableX server responds with JSON containing a unique *room-id*.
```
{
  "result": 0,
  "room": {
    "name": "My Permanent Room",
    "owner_ref": "XOXO",
    "settings": {
      "scheduled": false,
      "adhoc": false
    },
    "created": "2021-05-25T00:20:30.851Z",
    "room_id": "xxxxxxxxxxxxxx"
  }
}
```
## Scheduled Room
This Room is only available for a particular duration/period that needs to be specified with a scheduled time and duration. Use the following Settings in JSON Payload for API Call to create Scheduled Room:

*{"settings": {"scheduled": true, "scheduled time": "YYYY-MM-DD HH:II:SS", "duration": 30}}*

The *scheduled time* here is in GMT.

**Example 3: API Call to create Scheduled Room**
```
POST https://api.enablex.io/video/v1/rooms
Content-Type: application/json
Authorization: Basic XXXXXXXX
 
{
  "name": "My Scheduled Room",
  "owner_ref": "XOXO",
  "settings": {
    "description": "My Scheduled Room",
    "mode": "group",
    "scheduled": true,
    "adhoc": false,
    "scheduled_time": "2021-05-31 05:30:00",
    "duration": 30,
    "moderators": "1",
    "participants": "3",
    "quality": "SD",
    "abwd": true
  }
}
```
EnableX server responds with JSON containing a unique *room-id*.
```
{
  "result": 0,
  "room": {
    "name": "My Scheduled Room",
    "owner_ref": "XOXO",
    "settings": {
      "scheduled": true,
      "scheduled_time": "2021-05-31 05:30:00",
      "duration": 30,
      "adhoc": false
    },
    "created": "2021-05-25T00:20:30.851Z",
    "room_id": "xxxxxxxxxxxxxx"
  }
}
```
## Adhoc Room
It can be created instantly and is only available for a single call. Use the following Settings in JSON Payload for API Call to create Scheduled Room:

*{"settings": {"scheduled": false, "adhoc": true}}*

**Example 4: API Call to create Adhoc Room**
```
POST https://api.enablex.io/video/v1/rooms
Content-Type: application/json
Authorization: Basic XXXXXXXX
 
{
  "name": "My Adhoc Room",
  "owner_ref": "XOXO",
  "settings": {
    "description": "My Adhoc Room",
    "mode": "group",
    "scheduled": false,
    "adhoc": true,
    "duration": 30,
    "moderators": "1",
    "participants": "3",
    "quality": "SD",
    "canvas": false,
    "screen_share": false,
    "abwd": true,
    "max_active_talkers": 4
  }
}
```
EnableX server responds with JSON containing a unique *room-id*.
```
{
  "result": 0,
  "room": {
    "name": "My Adhoc Room",
    "owner_ref": "XOXO",
    "settings": {
      "scheduled": false,
      "adhoc": true
    },
    "created": "2021-05-25T00:20:30.851Z",
    "room_id": "xxxxxxxxxxxxxx"
  }
}
```
To learn more about Server APIs, refer to the following sources:

- [Basic Understanding and API Authentication](./server-API-video-application-server.md)
- [Create and Manage Meeting Rooms](./create-rooms.md)
# Create Meeting URL
The video meeting taking place in a meeting room can be accessed easily through the Meeting URL. This Meeting URL is used as a source URL in the IFRAME Embed Code.

The Meeting URL (see Example 5) comprises two key components: Room ID and Domain.

**Example 5: Meeting URLs**
```
https://your-subdomain.host-domain/#ROOM_ID#
```
EnableX requires unique Room IDs for both Participants and Moderators. They can join the Video Meeting with their respective unique Meeting URLs.

- Participant Meeting URL
    - For Embed Lite – 4 Participant UI Layout
        - *https//your-subdomain.yourvideo.app/#ROOM_ID#*
    - For Embed Premium – 12 Participant UI Layout
        - *https//your-subdomain.yourvideo.live/#ROOM_ID#*
- Moderator Meeting URL
    - For Embed Lite – 4 Participant UI Layout
        - *https//your-subdomain.yourvideo.app/host/#HASH*#*
    - For Embed Premium – 12 Participant UI Layout
        - *https//your-subdomain.yourvideo.live/host/#HASH*#*
Here *#HASH*#* is a base64 encoded string with *ROOM ID* and *APP ID* (APP ID is generated when you create a Project. Use “-” (Dash) as a separator, for example, *base64 encode ("ROOM_ID"-"APP_ID")*.

A Moderator has the following special privileges in a Video Room:

- Lock Room
- Record
- Live Streaming
- Mute Room
- Hard Mute Participants
- Disconnect Participant
- Control Participants Entry
- Close Conference