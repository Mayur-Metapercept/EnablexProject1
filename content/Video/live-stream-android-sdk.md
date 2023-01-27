---
title: "RTMP Live Streaming: Android SDK – Video API"
date: 
description:
type: "docs"
weight: 2
---
The *EnxRoom.startStreaming()* method allows the Moderator to forward live Video Sessions over RTMP Stream to any live streaming CDNs supporting this protocol. The *EnxRoom.stopStreaming()* method is used to stop forwarding RTMP Stream.
**Class**: EnxRoom

**Methods**:

- *public void startStreaming(JSONObject streamingDetails)*
- *public void stopStreaming(JSONObject streamingDetails)*  
**Parameters**:

- *streamingDetails* – Configuration options JSON object for forwarding streams.
    - *rtmpDetails.rtmpUrl* – Use “RTM-URL/RTMP-KEY” from CDN Provider
    - *rtmpDetails.urlDetails.url* – Optional RTMP Streaming View URL. If not given, a default Streaming View will be applied.
**Callbacks**:

- *onAckStartStreaming* – Acknowledgment to the Moderator when RTMP Streaming starts.
- *onAckStopStreaming* – Acknowledgment to the Moderator when RTMP Streaming starts.
- *onStreamingStarted* – Notification to all the users in the Room when RTMP Streaming starts.
- *onStreamingStopped* – Notification to all the users in the Room when RTMP Streaming stops.
- *onStreamingFailed* – Notification to all the users in the Room when RTMP Streaming fails to start or fails subsequently after getting started.
- *onStreamingUpdated* – Intermediate Notification to all the users in the Room with updates on RTMP streaming process.
```
JSONObject jsonObject = new JSONObject();

JSONObject rtmpDetails = new JSONObject();
rtmpDetails.put("rtmpUrl", "RTMP_URL/RTMP_KEY"");
jsonObject.put("rtmpDetails", rtmpDetails);

/* Optional Streaming View URL */
JSONObject urlDetails = new JSONObject();
urlDetails.put("url", "URL-TO-USE-AS-STREAMING-VIEW");
jsonObject.put("urlDetails", urlDetails);

room.startStreaming(jsonObject);	// Start Streaming
room.stopStreaming(jsonObject);		// Stop Streaming

public void onAckStartStreaming(JSONObject jsonObject){
	// Acknowledges that Streaming started
}

public void onAckStopStreaming(JSONObject jsonObject){
	 // Acknowledges that Streaming stopped
}

public void onStreamingStarted(JSONObject jsonObject) { 
	// Notifies all that Streaming started 
} 
public void onStreamingStopped(JSONObject jsonObject) { 
	// Notifies all that Streaming stopped
} 
public void onStreamingFailed(JSONObject jsonObject) { 
	// Notifies all that Streaming failed
} 
 
public void onStreamingUpdated(JSONObject jsonObject) { 
	// Notifies all with Streaming process updates
}
```
| Code      | Description |
| ----------- | ----------- |
| 5121      | Repeated *startStreaming()* call while the previous request is in process.       |
| 5122   | Repeated *startStreaming()* call after Streaming has started.        |
| 5123      | Repeated *stopStreaming()* call while the previous request is in process.       |
| 5124   | *stopStreaming()* called without starting a Stream first. Non-Contextual Method Call.        |
| 5125      | Invalid Stream configuration.      |
