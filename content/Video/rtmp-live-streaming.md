---
title: "RTMP Live Streaming"
date: 
description:
type: "docs"
weight: 2
---
# RTMP Live Streaming
---
Broadcast live video sessions to YouTube, Facebook, Vimeo or other digital platforms using an RTMP stream. In addition to the predefined layout, you also have the freedom to define your custom layout for live streaming.
---
## Overview
In Today’s time, the Streaming Platforms like Youtube, Facebook, Vimeo and may others are majorly used for Video Broadcasting to reach a larger Audience So, there is an ever increasing demand for live-streaming of ongoing Video Call Sessions too to through RTMP CDN Providers.

To meet this demand, EnableX Video Sessions now may be streamed live using few lines of Code to forward Streams over RTMP to any live streaming CDNs which support this protocol.

## How it works?
Refer the following diagram to understand how EnableX Video Sessions are streamed live:
![EnableX Video Session](./rtmp-1.png)
Users join a Video Session hosted on EnableX Platform from different end points. EnableX forwards a Single Video Stream (With a Presentable Configurable View) to to RTMP CDN. Now, its the responsibility of the CDN provider to send audio and video streams to its end users.
**Note**: RTMP supports only the H.264 codec.

## What you need?
### Setup Streaming through Live-Streaming CDN Providers
- Get Live Streaming CDN Account, e.g, YouTube, Vimeo, Facebook, Twitch or any other.
- Using your CDN Provider Account, setup your Streaming or schedule your Streaming.
- Once Streaming is setup, you get RTMP Streaming URL & Streaming Key. These 2 data are important for EnableX API to stream-out.
- You also get a Public URL from CDR Provider to share among intended viewers.
### Use EnableX API to Stream-Out to CDN
- Create UI in your EnableX SDK driven Video App to input *RTMP Streaming URL & Streaming Key* from user (Moderator) to initiate Streaming.
- Read through API Documentation to know how to code to stream out video Session to Streaming CDN.
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
	if (resp.status.resultCode === 0) {
		console.log('Streaming started. You are live.');
	}
	else {	// Streaming failed
		console.log(resp.status.error.errorDesc)
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
```
**Note**: EnableX uses a Default View to stream out. In case you wish to develop your own view, read how to create own RTMP Streaming View?
### Monitor / Manage Streaming on your Account with CDN Providers
- Once Streaming starts from EnableX Video App, it reaches to CDN Provider. You can monitor the stream as it reaches to the CDN Provider through your Account.
- You might experience significant lag from 10-40 seconds.
- If ifs a scheduled streaming event, you might to click a “Button” to go live to make the stream available on the public URL you shared with your intended user.
- You can monitor streaming stats, views etc. on the Console.
## How to setup streaming on YouTube?
This is an example help you understand Live Streaming setup process on YouTube. The Concept remains same with all other Live Streaming CDN Providers.
### Navigate to setup
- Login to YouTube.
- From Top-Right Corner, following menu options.
- Go to “YouTube Studio”
![Login](./youtube-1.png)

- From Right of Top-bar, click ‘CREATE”
- It opens up 2 options.
- Click on “Go Live”
![Create](./you-tube-2.png)
### Setup Streaming
- From Right Sidebar, click ‘STREAM”
- It opens up a Form.
- As Category, preferably choose “People and Blogs”
![Stream](./stream-1.png)
### Get CDN Information
- After setting up, you get Streaming Console to manage, get key information and get reported.
- Get *Stream URL* and *Streaming Key*. These 2 data you would need to use in API yo stream out.
![CDN Information](/cdn-information.png)
### Get Public URL to share
- From Right of Top-bar, click ‘Arrow” Icon.
- It opens up UI with many share options.
- See the URL, this is the URL to be shared with intended audience.
- COPY it.
![Share](./share.png)
## How to create own RTMP Streaming View?
RTMP Streaming View is a HTML Client Application hosted on a URL which is used as a Client to live stream to CDR Provider for a larger Audience to view. The Streaming Methods optionally be provided with a Custom URL to use as Streaming View. In case you don’t provide one, EnableX uses a default view.

- Use EnableX Web Toolkit to create a HTML Client that can join a Video Session given a Token.
- Ensure that this Client joins a Session only without publishing any Audio/Video Stream into the Room.
- Create a URL Scheme to accept EnableX Token as part of the URL itself, either as part of URL or as Query String. e.g.
    - *https: //your-domain/video/?token=ENABLEX-TOKEN*
- Host the Web Application on a secured web server. i.e. over https.
- Pass the URL of your hosted Web Application as part of Stream Configuration to the method to start streaming. Note, you should pass the URL without any Token or without the string ENABLEX-TOKEN. e.g. Pass only
    - *https: //your-domain/video/?token=*
## API References
- [Live Streaming with Web SDK](./live-stream-web-sdk.md)
- [Live Streaming with Android SDK](./live-stream-android-sdk.md)
- [Live Streaming with iOS SDK](./live-stream-ios-sdk.md)
