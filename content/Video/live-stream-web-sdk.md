---
title: "RTMP Live Streaming: Web SDK – Video API"
date: 
description:
type: "docs"
weight: 2
---
# Start / Stop Live Streaming
The *EnxRoom.startStreaming()* method allows the Moderator to forward live Video Sessions over RTMP Stream to any live streaming CDNs supporting this protocol. The *EnxRoom.stopForwarding()* method is used to stop forwarding RTMP Stream.
## Methods:

- *EnxRoom.startStreaming(streamingConfig, callback)*
- *EnxRoom.stopForwarding(callback)*
## Parameters:

- *streamingConfig* – Configuration options JSON object for forwarding streams.
    - *rtmpDetails.rtmpUrl* – Use “RTM-URL/RTMP-KEY” from CDN Provider
    - *rtmpDetails.urlDetails.url* – Required. RTMP Streaming View URL. If not given, a default Streaming View will be applied.
## Event Notifications:

- *streaming-started* – Acknowledgment to the Moderator when RTMP Streaming starts.
- *streaming-stopped* – Notification to all the Participants in the Room when RTMP Streaming starts/stops.
- *streaming-updated* – Intermediate Notification to the moderator who tried to start streaming with start-process updates
- *streaming-failed* – Notification to the moderator who tried to start streaming when streaming fails.
```
var streamingConfig = {	
	rtmpDetails: {
		rtmpUrl: "RTMP_URL/RTMP_KEY"
	},
	urlDetails: {
		url: "URL-TO-USE-AS-STREAMING-VIEW"
	}
};

// Start Streaming
room.startStreaming(streamingConfig, function(resp) {
	if (resp.result === 0) {
		console.log('Streaming started. You are live.');
	}
	else {	// Streaming failed
		console.log(resp.error)
	}

});

// Stop Streaming
room.stopStreaming(function(resp) {
	console.log('Streaming Stopped.');
})

room.addEventListener('streaming-started', function(event) {
	// All are notified that streaming has started
	// event.message.startedBy : who started the streaming
});

room.addEventListener('streaming-stopped', function(event) {
	// All are notified that streaming has stopped
	// event.message.stoppedBy : who stopped the streaming
});

room.addEventListener('streaming-failed', function(event) {
	// Notification that streaming failed
});

room.addEventListener('streaming-updated', function(event) {
	// Intermediate 
});
```
## Error Codes / Exceptions
| Code      | Description |
| ----------- | ----------- |
| 7000      | Failed to start streaming      |
