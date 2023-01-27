---
title: "RTMP Live Streaming: iOS SDK – Video API"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.startStreaming()* method allows the Moderator to forward live Video Sessions over RTMP Stream to any live streaming CDNs supporting this protocol. The *EnxRoom.stopStreaming()* method is used to stop forwarding RTMP Stream.
**Class**: *EnxRoom*

**Methods**:

- *(void)startStreaming:(NSDictionary *_Nonnull)streamingConfig;*
- *(void)stopStreaming:(NSDictionary *_Nonnull)streamingConfig;* 
**Parameters**:

- *streamingConfig* – Configuration options for forwarding streams
    - *rtmpDetails.rtmpUrl* – Use “RTM-URL/RTMP-KEY” from CDN Provider
    - *rtmpDetails.urlDetails.url* – Optional RTMP Streaming View URL. If not given, a default Streaming View will be applied.
*Delegate Methods*:

- *room:didAckStartStreaming*: Acknowledgment to the Moderator when RTMP Streaming starts.
- *room: didStreamingStarted*: Notification to all Users that Live Streaming has started.
- *room: didStreamingStopped*: Notification to all Users that Live Streaming has stopped
- *room: didStreamingUpdated*: Intermediate Notification to all Users about the Live Streaming process.
- *room: didStreamingFailed*: Notification to all Users that Live Streaming has failed to start or failed subsequently after getting started.
**Deprecated Delegate Methods**: With iOS SDK 2.2.0+

- *room:didAckStopStreaming*: Acknowledgment to the Moderator when RTMP Streaming starts.
- *room:didStreamingNotification*: Notification to all the Participants in the Room when RTMP Streaming starts/stops.
```
//Start Live Streaming
NSDictionary *StreamInfo = @{@"rtmpDetails":
	:@{@"rtmpUrl":@"rtmp://a.rtmp.youtube.com/live2/4rjb-hprf-7wf5-9923"},
	:@"urlDetails":@{@"url":@"https://meeting-qa.enablex.io/room/?token="}
}

[EnxRoom startStreaming: StreamInfo];

// Stop Live Streaming
[EnxRoom stopStreaming: StreamInfo];

//All are notified that Streaming has started
- (void)room:(EnxRoom *_Nullable)room didStreamingStarted:(NSArray *_Nullable)data; 

//All are notified that Streaming has stopped
- (void)room:(EnxRoom *_Nullable)room didStreamingStopped:(NSArray *_Nullable)data; 

//All are notified that Streaming has failed
- (void)room:(EnxRoom *_Nullable)room didStreamingFailed:(NSArray *_Nullable)data; 

//All are notified that Streaming process updates
- (void)room:(EnxRoom *_Nullable)room didStreamingUpdated:(NSArray *_Nullable)data; 
```
**Error Codes / Exceptions**

| Code      | Description |
| ----------- | ----------- |
| 5121      | Repeated *startStreaming()* call while the previous request is in process.       |
| 5122   | Repeated *startStreaming()* call after Streaming has started.        |
| 5123      | Repeated *stopStreaming()* call while the previous request is in process.       |
| 5124   | *stopStreaming()* called without starting a Stream first. Non-Contextual Method Call.        |
| 5125      | Invalid Stream configuration.      |