---
title: "Live Media Statistics: Web SDK – Video API"
date: 
description:
type: "docs"
weight: 2
---
**Note**: *EnxRoom.subscribeStreamStatsForClient(Stream, EnableDisable)*, the following documentation covers a new method with greater flexibility on UI and Data.

The *EnxRoom.subscribeMediaStats()* method allows you to subscribe to live media statistics of Local, Remote, Canvas, and Screen-Share for debugging purposes or UI display at an endpoint. The following information for each stream is displayed using an Overlay over the respective player:

- For Local Streams
    - Transmission Bandwidth
    - Video Resolution
- For Subscribed Streams
    - Receiving Bandwidth
    - Video Resolution
    - Available Bandwidth for Remote User
    - Packet Loss
**Class**: *EnxRoom*

**Method**: *EnxRoom.subscribeMediaStats(reqType, callback)*

**Parameters**:

- *reqType* – Type of request on media statistics to configure how the media stats are delivered and stopped. Configurable options are given below:
    - *display* – Media Statistics are shown as overlay on each video player.
    - *notify* – Media Statistics are dispatched in JSON format along with an event *media-stats* to be handled in the code.
    - *notify-display* – Media Statistics are shown as overlay on each Video Player as well as data is dispatched in JSON format along with an event *media-stats*.
    - *disable* – This disables Media Statistics subscription. Subsequently overlays are removed from Video Player and *media-stats* event dispatch is stopped.
- *callback* – Callback returns with response information on Media Statistics subscription.
**Event Listener**:

*media-stats* – This event with Media Statistics in JSON format is dispatched only when Media Statistics is subscribed with *reqType: notify* or *reqType*: *notify-display*.
```
room.subscribeMediaStats('notify', function(resp) {
	// response is a JSON, e.g.
	/*
	{ 	"result": 0,  
		"msg": "Success"  
	}
	*/  
}); 

room.addEventListener("media-stats ", function(evt) {
	// evnt is JSON with Media Stats, e.g. 
	/*
	{	type: 'media-stats', 
		talkers: [{ }], 
		publisher:  {},
		share: {}, 
		canvas: {}
	}
	*/
});
```
**Media Stats JSON Payload**:

- *talkers* – Array of Objects containing Media Statistics of each User’s Stream available on Active Talker List. For Each Talker’s Endpoint, it shows both Subscription and Publishing Connection’s Statistics.
- *publisher* – Object containing Media Statistics of published stream connection.
- *share* – Object containing Media Statistics of Screen Share connection.
- *canvas* – Object containing Media Statistics of Canvas Stream connection.
```
{
  "type": "media-stats",
  "talkers": [
    null,
    null,
    {
      "id": 2,
      "subscriber": {
        "video": [
          {
            "displayString": "<div> <strong style=\"color:black;\" > 640X480p10@188Kbps</strong>:</div><div> <strong style=\"color:black;\" > AvailBw:500Kbps, loss:1</strong>:</div>",
            "resHeight": 480,
            "resWidth": 640,
            "packetsLost": 1,
            "bandwidth": 500,
            "frameRate": 10,
            "bitrate": 188
          }
        ],
        "total-bitrate-kbps": 238
      },
      "publisher": {
        "video": [
          {
            "displayString": "<div> <strong style=\"color:black;\" > 640X480p10@186Kbps</strong>:</div>",
            "resHeight": 480,
            "resWidth": 640,
            "packetsLost": 0,
            "bandwidth": 0,
            "frameRate": 10,
            "bitrate": 186
          }
        ],
        "total-bitrate-kbps": 227
      }
    }
  ],
  "publisher": {
    "total-bitrate-kbps": 354,
    "video": [
      {
        "displayString": "<div> <strong style=\"color:black;\" > 640X480p9@312Kbps</strong>:</div>",
        "resHeight": 480,
        "resWidth": 640,
        "packetsLost": 0,
        "bandwidth": 0,
        "frameRate": 9,
        "bitrate": 312
      }
    ]
  },
  "share": {},
  "canvas": {}
}
```