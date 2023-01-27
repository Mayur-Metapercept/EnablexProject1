---
title: "Video Technical Specification"
date: 
description:
type: "docs"
weight: 2
---
# Video Technical Specification #

| Parameter | Description |
| ------ | ------ |
| **Video Streaming** |    |
| HD Streaming |  720p. Resolution: Min 320X180@26fps, Max 1280X720@26fps  |
| SD Streaming |  480p. Resolution: Min 320X180@26fps. Max 640X480@26fps  |
| LD Streaming | 240p/180p. Resolution: Min 80X45@26fps. Max 640X360@26fps   |
| Video Layers | Add any of the 1 up to 3 layers in Stream during initiation process.  |
| | 1 LAYER = HD 720p layer only |
| | 2 LAYER = HD 720p & SD 480p layers only |
| | 3 LAYER = HD 720p, SD 480p & LD 240p/180p layers |
| Video Codec |  VP8. Support for H264 discontinued.  |
| Audio Codec | OPUS   |
| Active Talker Streams | Maximum of nine Top Active Talker Streams are processed, recorded and transferred to other ends.   |
|  |    |
| **Screen Share** |    |
| Resolution  |  Default HD 1080p Resolution: Max 1920×1080@6fps. May vary depending on Source Screen Size.  |
| Bandwidth Needed |  Bandwidth required to transmit: 300kbps, Bandwidth to receive: 300kbps  |
| Browser Support |  [Browser Compatibility](https://www.enablex.io/developer/video/browser-compatibility-of-enablex-video/)  |
|  |    |
| **Canvas Streaming** |    |
| Resolution | HD 720p. Resolution: Min 320X180@6fps, Max 1280X720@23fps   |
| Bandwidth Needed | Bandwidth required to transmit: 300kbps, Bandwidth to receive: 300kbps   |
|  |    
| **Media Tunnelling** |    |
| UDP Port |  Port Range 30000 – 35000  |
| Fallback |  Through the TURN Server and it is configurable.  |
|  |    |
| **Recording** |    |
| Source Stream |  Each Stream in Session is recorded individually. Format is .mkv  |
| Location |  Recorded locally. Transferable post session.  |
| Playable Session | Transcoded single video file. Processed post-session. Format is mp4.   |
| Recording Quality | Max HD 720p (Or as received at Server)   |
| Transcoded Quality | Max SD 480p   |
| File Size | HD 720: 11MB/Minute, SD 480px 4MB/Minute   |
|  |    |
| **Quality Adaption** |    |
| Auto Adaption |  Auto adjustment to receive optimum quality video as per the available bandwidth. |
| Fallback |  Audio only call, if available bandwidth not optimum for video communication.  |
| Auto Restoration | Restores the Video once the network connectivity improves.   |
|  |    |
| **PSTN / SIP** |    |
| Dail-in to Session |  Available  |
| In-Session Dial-Out |  Available  |

