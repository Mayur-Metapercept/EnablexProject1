---
title: "Create Token"
date: 
description:
type: "docs"
weight: 2
---
A Token is required for any Client End Point to join a RTC session on EnableX Platform.. A Token created for a Room has an assigned role for the user. Note the following:

**Characteristics of Token**
- A Token is created only for a given Room-ID.
- A Token decides your role within a session, i.e. Moderator or a Participant or a Viewer. A Moderator is the Organiser who will have additional control over the session like start/stop recording, hard mute/unmute room, drop/eject participant from the room or end the session. The viewers can access all media streams and chat, but they cannot interact.
- Tokens are transactional. Every time you want to connect to the same room you would require a new Token.
- A Token can be used only once.
- Tokens have a 15 minutes lifetime within which it must be used to connect to a Room.
- For a Permanent Meeting Room, Token may be created any time.
- For a Scheduled Meeting Room, Token may be created 15 minutes prior to scheduled start time.
---
- [API Route](https://api.enablex.io/v2/rooms/{room-id}/tokens)
- **HTTP Request**: POST
- [Try Open API](https://openapi.enablex.io/video/v2/api-docs/#/Rooms/createToken)

**Sample Request**
```
POST https://api.enablex.io/video/v2/rooms/{room_id}/tokens
Authorization: Basic XXXXXXX
Content-Type: application/json

{
     "name": "User Name",
     "role": "participant",
     "user_ref": "XXX",
     "data": {
     	"custom_key": "String",
	"any_key": "String"
     }
}
```
**JSON Raw Body Payload on Request**
| Name     | Description | Required | Value |
| ----------- | ----------- | ----------- | ----------- |
| name | Name of the user who is creating token to join session | Yes | Alpha Numeric |
| role | Role of User | Yes | Enumerated Values: moderator, participant, viewer (All in lowercase). Note:moderator role user has access to session management controls, viewer role user doesn’t have stream publishing rights. |
| user_ref | User ID or Reference. You may use it from your Information System. Post Call Reports include this data for your reference/reporting | Yes | Alpha Numeric |
| data | its a custom data object that you can pass. You can define your own keys, max 5 keys to pass data about the user. The data will be available to others in-session. |  | | |

**Response**
```
{
     "result": 0, 
     "token": "JWT_WEB_TOKEN"
 }
 ```
