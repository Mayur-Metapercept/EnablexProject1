---
title: "Screen Share with Audio"
date: 
description:
type: "docs"
weight: 2
---
# Overview
Screen Share now has options to add Audio Track from Microphone if the underlying Browser supports it. Also, the developer can use Meta-Data options to define their own data structure to help UX/UX at the receiving end.

To support Screen Sharing in the Room, you need to enable Screen-Sharing during [Room Creation](https://www.enablex.io/developer/video-api/server-api/rooms-route/#create-room) by setting the following in the JSON Payload: 

`{ "screen_share": true; })`

To receive Shared Screen, subscribe to the Screen-Share Stream ID# 101 and play it on the Video Player.

## Start Screen Sharing

The `EnxRoom.startScreenShare()` method is used to create a Screen-Sharing Stream @ 6fps to publish in the Room. Screen Sharing continues even when the Application runs in the background.

**Class**: EnxRoom

**Method**:
- `EnxRoom.startScreenShare(options, Callback)` - With Web SDK v2.1.2+
- `EnxRoom.startScreenShare(Callback)`- With Web SDK, version lower than v2.1.2

**Parameters**:
Introduced in Web SDK v2.1.2:

| Parameter | Type | Description |
| ------ | ------ |------- |
| `options` | JSON Object  | This is an optional parameter to have custom meta-data to help out UI / UX requirements and many other parameters affecting Screen Share. |
| `audio` | Boolean | This parameter allows Screen Share to carry an Audio Track from Microphone if the underlying browser supports it. The default value is false. |
| `layout` | String | Use this to pass some value to help define UI/UX at receiving end. For example, pass “presenter” to show a Presenter Layout with Screen Share at the receiving end. |

**Event Notifications**:

- `share-started` – Notification to everyone in the Room when Screen-Sharing starts.

![Start Screen Sharing](https://github.com/metapercept/enablex-io/blob/master/content/Images/Start%20Screen%20Sharing.png)

## Stop Screen Sharing

The `EnxRoom.stopScreenShare()` method is used to stop the ongoing Screen-Sharing.

**Class**: `EnxRoom`

**Methods**:

- `EnxRoom.stopScreenShare(sharedStream, Callback)`
- Alternate way to stop screen sharing
    `EnxRoom.unpublish(sharedStream, Callback)`

**Parameter**:
| Parameter | Type | Description |
| ------ | ------ |------- |
| `sharedStream` |    | Screen-share Stream |

**Event Notification**:

- `share-stopped` – Notification to everyone in the Room when Screen sharing stops.
![Stop Screen Sharing](https://github.com/metapercept/enablex-io/blob/master/content/Images/Stop%20Screen%20Sharing.png)

**Error Codes or Exceptions**:

| Code | Description |
| ------ | ------ |
| 1143 | Device not found. Screen Share disabled at OS. |
| 1151 | Another Screen-Share Stream active in the Room. |

***Note***:
- Application Share experience may differ from browser to browser.
- **Google Chrome** versions below 72 need an [Extension](https://chrome.google.com/webstore/detail/enablex-screen-sharing-ex/apedaiecomcfkjdjbnkfcdafaikkdkeo?utm_source=chrome-ntp-icon) to be installed from Web Store to initiate Screen Share (at the Publisher end).

## Force Stop other’s Screen Sharing ##

**Availability**: Web SDK 2.1.2+
If the moderator wishes to force stop any ongoing Screen Share by another user in the Room, he can do so by using `EnxRoom.stopAllSharing()` method. ***Note***: This is a Moderator exclusive feature and cannot be executed from Participant’s endpoint.
This method also forces stops any ongoing Canvas Streaming.

**Class**: `EnxRoom`

**Method**: `EnxRoom.stopAllSharing(Callback)`

**Event Notification**:
    - `share-stopped` – Notify everyone in the Room when Screen sharing stops.

![Force Stop Screen Sharing](https://github.com/metapercept/enablex-io/blob/master/content/Images/Force%20Stop%20other%E2%80%99s%20Screen%20Sharing.png)
