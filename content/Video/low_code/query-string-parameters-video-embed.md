---
title: "Query String Parameters for Video Embed"
date: 
description:
type: "docs"
weight: 2
---
The Meeting URL used in Webview or IFRAME Source may be customized by passing Query String Parameter to update UI Elements and/or to update User Experience. Without any of these paramters, the Low Code Embed appears / behaves as per settings done through Visual Builder. However, in case you look to alter while embedding, Query String Parameters come handy.

# Overview
The Meeting URLs can be further qualified with Query String Parameters, to pass the feature list and other data to the Video Meetings as per the requirement.

- Use the Query String Qualified Meeting URLs directly from the browser’s address bar or as an IFRAME Embed.
- Pass different parameters for different Participants or a Moderator in the same meeting.
- Use the Query String Parameters to overwrite the feature list through the portal as described in the Select Preferred Features. If associated parameters are not used, pre-set feature setting remains the same.
# How to use Query String Parameters in Meeting URL?
- Single Query String Parameters
    - *https://MEETING-URL?var=value*
- Multiple Query String Parameters
    - *https://MEETING-URL?var1=value&var2=value*
# Parameters: For Embed Lite Template
- **Entry to Session**
    - *name* – String. Name of the Participant or Host joining the Meeting
    - *user_ref* – String. Unique Identifier for the Participant or Host joining the Meeting
    - *video* – Values: yes, no. To join Meeting with or without Video
    - *audio* – Values: yes, no. To join Meeting with or without Audio
    - *landing* – Values: yes, no. To reach the landing page or to reach the session page directly. If *landing*=no, then *name* must be used.
- **Features**
    - *screenshare* – Values: yes, no. To enable or disable Screen Sharing
    - *group_chat* – Values: yes, no. To enable or disable Group chat
- **UI / UX Elements**
    - *username* – Values: yes, no. To display participant names on Video
- **Exit Session**
    - *exit_url* – String. URL to redirect to when user clicks Disconnect button
    - *exit_url_target* – Values: parent, self. Default: self. To redirect to *exit_url* in the self window or parent window
- **Tool Bar**
    - *disconnect_button* – Values: yes, no. Default: yes. To show Disconnect Button
    - *icon_color* – String. Color Code in Either in HEXCODE or Color Name. Button Icon Color. Default WHITE.
    - *con_bg_color* – String. Color Code in Either in HEXCODE or Color Name. Button Background Color. Default WHITE.
    - *disconnect_icon_color* – String. Color Code in Either in HEXCODE or Color Name. Disconnect Button Icon Color. Default WHITE.
    - *disconnect_icon_bg_color* – String. Color Code in Either in HEXCODE or Color Name. Disconnect Button Background Color. Default RED.
# Parameters: For all other Templates
- **Entry to Session**
    - *name* – String. Name of the Participant or Host joining the Meeting
    - *user_ref* – String. Unique Identifier for the Participant or Host joining the Meeting
    - *video* – Values: yes, no. To join Meeting with or without Video
    - *audio* – Values: yes, no. To join Meeting with or without Audio
    - *landing* – Values: yes, no. To reach the landing page or to reach the session page directly. With landing=no, name must be used.
- **Enabling Features**
    - *screenshare* – Values: yes, no. To enable or disable Screen Sharing
    - *whiteboard* – Values: yes, no. To enable or disable Whiteboard
    - *live_streaming* – Values: yes, no. To enable or disable Live Streaming
    - *group_chat* – Values: yes, no. To enable or disable Group chat
    - *pvt_chat* – Values: yes, no. To enable or disable Private chat
    - *room_lock* – Values: yes, no. To enable or disable Room Lock
- **UI / UX Elements**
    - **Background Image**: This is to use a background image in the Video Session UI.
        - *bg_img_url* – Required. Fully Qualified Image URL to be used as background image.
        - *bg_img_repeat* – Optional. Enumerated values: *no-repeat, repeat-x, repeat-y*. If not used, background will be repeated.
        - *bg_img_position* – Optional. Its combination of 2 words. e.g. “*left bottom*“.
            - 1st Word for horizontal positioning. Enumerated values: *left, right, center*
            - 2nd Word for vertical positioning. Enumerated values: *top, bottom, center*
- **User List**
    - *user_list_participant* – Values: yes, no. To enable or disable User List on Participant’s UI
    - *user_list_moderator* – Values: yes, no. To enable or disable User List on Moderator’s UI
    - *fixed_toolbar* – Values: yes, no. To make the toolbar continuously visible. The toolbar disappears after pre-defined time interval by default
    - *grid_view* – Values: gallery, leader. To start UI with chosen view. Default: gallery
- **Top Bar Elements**
    - *topbar* – Values: yes, no. To enable or disable topvar view. If Topbar is hidden, then none of the elements under it will be visible.
    - *user_count* – Values: yes, no. To enable or disable User Count
    - *room_name* – Values: yes, no. To display or hide the Room Name
    - *clock* – Values: yes, no. To enable or disable clock view
- **Waiting Lobby**
    - *lobby_timeout* – Number. In seconds. Default: 120 i.e. 2 minutes. User’s maximum waiting time in Lobby in number of seconds. When wait time exceeds, user gets redirected to *lobby_exit_url*
    - *lobby_exit_url* – String. URL to redirect the user when user waits more than *lobby_timeout*.
    - **Lobby Decorations**: Following parameters help create better waiting experience for users in Lobby. These parameters are to be used in the Participant Meeting URL. Note that all external URL host server must be CORS enabled, otherwise the related resource will not be rendered.
        - *Image Carousel/Slide Show*: Pass maximum of 3 image URLs to play as Slideshow./Carousel.
            - *lobby_img_1* – Image URL of 1st Image in the Slideshow.
            - *lobby_img_2* – Image URL of 2nd Image in the Slideshow.
            - *lobby_img_3* – Image URL of 3rd Image in the Slideshow.
        - *Text Carousel/Carousel*: Pass maximum of 3 Phrases, Text to play as Slideshow./Carousel
            - *lobby_text_1* – 1st Text in the Slideshow.
            - *lobby_text_2* -2nd Text in the Slideshow.
            - *lobby_text_3* -3rd Text in the Slideshow.
        - *Video Play*: Pass 1 Video File *URL* to play. *HTML5 <VIDEO></VIDEO>* Player supported File only.
            - *lobby_video* – Video URL to play
        - *Background Music*: Pass 1 Audio File *URL* to play. *HTML5 <AUDIO></AUDIO>* Player supported File only. Note that background music can be played individually, and also with Image and Text Slideshow. It is not used in conjunction with Video Play.
            - *lobby_music* – Audio/Music File URL to play as Background Music.
- **Exit Session**
    - *exit_url* – String. URL to redirect to when user clicks Disconnect button
    - *exit_url_target* – Values: parent, self. Default: self. To redirect to exit_url in the self window or parent window
- **Virtual Image Library**: Following parameter help create Image Library for Virtual Background. Note that all external URL host server must be CORS enabled, otherwise the related resource will not be rendered.
    - *virtual_bg_imgs* – String. URL of the Image. Must be hosted on https. Refer [Image specification](./virtual-background-video-embed.md).