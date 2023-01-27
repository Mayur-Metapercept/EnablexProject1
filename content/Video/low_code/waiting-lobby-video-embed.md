---
title: "Waiting Lobby with Video Embed"
date: 
description:
type: "docs"
weight: 2
---
The Waiting Lobby feature helps you to create an user experience for waiting participants before they could be allowed into the Video Room by Moderator.
# Overview
A Participant is forced to wait in a Lobby when Video Room entry is restricted. There are 2 type of entry restrictions may be deployed by Moderator, viz.
- Moderated Entry: When moderator decides which participant to join the Video Room. The Knock room allows participants to wait before he is allowed by the moderator to join a session.
- Wait for Moderator to join first: When Moderator decides to join before participants. Until then participants are made to wait.

Let’s deep dive into it.
# Room Entry Restriction
## Moderated Entry
Participants may be forced to wait in the Lobby until Moderator allows them in individually or all at one go.

Such entry restriction is imposed with a Room Settings named *knock*. A knock-enabled room doesn’t allow participant entry to room without Moderator’s permission.
```
/* Define a knock-enabled room */
{	"name": "Room name",
	"owner_ref": "XOXO",
	"settings": {
		"knock": true	/* To enable moderated entry */
		...
		...
	}
}
```
## Wait for Moderator to join first
Participants may be forced to wait in the Lobby until Moderator joins. As soon as a Moderator joins, all participants waiting in Lobby will automatically be put into the Video Room. Susequently, all participants are put directly into the Video Room without having to wait.

Such entry restriction is imposed with a Room Settings named *wait_for_moderator*. A wait-enabled room doesn’t allow participant entry to room until and unless a Moderator joins.
```
/* Define a wait-for-moderator enabled room */
{	"name": "Room name",
	"owner_ref": "XOXO",
	"settings": {
		"wait_for_moderator": true	/* To enable wait-for-moderator */
		...
		...
	}
}
```
Note: To know more about Room Creation, refer our [API document](./video-server-api-manage-room.md)
# Waiting Lobby
By default Waiting Lobby is a blank Page with a notification message placed into it. However, you may like to provide better waiting experience in Lobby for the Participants. This is where you may like to run a presentation or video to talk about yoru Service, Topic or Agenda to waiting Participants.
## Ways to decorate Lobby
You may like to use one of the following decorations in Lobby:

- Background Music: A background music may be played using an External MP3 file link.
- Image Slide Show with or without Background Music: A Image Slideshow may be presented with maximum of 3 External Image URL. Optionally, you may have a background music played with the Slideshow.
- Text Carousel with or without Background Music: A Text Carousel may be presented with maximum of 3 Sentendes/Phrases, Optionally, you may have a background music played with the Carousel.
- Video Play: Play a Video with External .MP4 file link.
## Query String Support to decorate
All type of Decorations are supported by Query String Parameters to be passed to the Meeting URL which is either used as IFRAME Source URL or WebView URL.
```
// Example: To play background music to Participants in Lobby
<IFRAME 
	allow="camera; microphone; fullscreen; speaker; display-capture" 
	src="MEETING-URL?lobby_music=PATH-TO-MP3-file">
</IFRAME>
```
**Note**:

- You must use Lobby Decoration Parameters to the Participant Meeting URL to embed. It’s not needed for the Moderator Meeting URL.
- See detailed explanation on [Query String Support for Lobby Decorations](./query-string-parameters-video-embed.md) here.
- While using External Image, Video, MP3 URL in Query String Parameter, make sure your Hosting Server of these resources are CORS enabled. We Embed faces CORS issue, it will fail to load related resources.