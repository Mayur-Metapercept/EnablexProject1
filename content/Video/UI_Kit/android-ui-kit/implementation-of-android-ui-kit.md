
# Implementation

## Prerequisite

To use the Enx_UIKit_Android Framework user must have the following:

- A valid Token to join the room.
- Camera Permission
- Mic Permission

## Code a little

- **Step-1**: Go to your Activity and import the packages shown below:

```js
import com.enablex.enxuikit_android.observer.EnxVideoStateObserver 
import com.enablex.enxuikit_android.view.EnxVideoView 
```

- **Step-2**: Initialize the EnxVideoView class and then add the reference of EnxVideoView to your layout as shown below:

```js
// You need to get Token to get connected
// Refer:https://www.enablex.io/developer/video-api/server-api/rooms-route/#create-token

// Initialize EnxVideoView
enxVideoView = EnxVideoView(this,token,this, "Low Code Embed URL")
// Low Code Embed URL is optional, in case you want to import settings.

// Set Layout Parameters
val rlp = RelativeLayout.LayoutParams(RelativeLayout.LayoutParams.MATCH_PARENT, RelativeLayout.LayoutParams.MATCH_PARENT)

// Add VideoView to your Layout
this.addContentView(enxVideoView, rlp) 
```

- **Step-3**: Handle Orientation

To handle Orientation please follow below 2 steps:

- Add the property given below to your activity inside AndroidMainfest.xml file:
***android:configChanges="orientation|screenSize|keyboardHidden"***

- Overide ***onConfigurationchanged*** function and call below function
***enxVideoView?.configurationChanged(newConfig)***

override fun onConfigurationChanged(newConfig: Configuration) { 
    super.onConfigurationChanged(newConfig) 
    enxVideoView?.configurationChanged(newConfig) 
} 
- **Step-4**: Handle Back Button

To handle the back button please follow step:

```js
Overide onBackPressed function and call below function    
override fun onBackPressed() {
    enxVideoView?.backPressed() 
}
```

- **Step-5**: Customize Bottom Bar

You can design the Bottom Bar according to you needs and you can set the desired sequence by passing a list of ***EnxButton*** to ***configureBottomOptionList*** function. While creating your own button use the ***setImage*** function and pass two images (first image for normal state and second image for selected state) except the disconnect button as it takes a single parameter for the image. For more detail, please refer to below code snippet:

```js
val setting = EnxSetting.getInstance(this) 

// Enumerated values to use for BottomOption are
// AUDIO, VIDEO, SWITCH_CAMERA, SWITCH_AUDIO, GROUP_CHAT, DISCONNECT 

val audioButton = EnxButton(this,EnxSetting.BottomOption.AUDIO.tag) 
audioButton.setImage(R.drawable.audio_on,R.drawable.audio_off) 

val chatButton = EnxButton(this,EnxSetting.BottomOption.GROUP_CHAT.tag) 
chatButton.setImage(R.drawable.group_chat,R.drawable.group_chat_noti) 

val disconnectButton = EnxButton(this,EnxSetting.BottomOption.DISCONNECT.tag) 
disconnectButton.setImage(R.drawable.end_call_new) 
 
setting.configureBottomOptionList(listOf<EnxButton>(videoButton, cameraSwitch, chatButton, audioButton, disconnectButton)) 
```

- **Steps-6** Customize Top Bar

You can design the Top Bar according to your needs and they can set the desired sequence by passing a list of ***EnxButton*** to ***configureTopOptionList*** function. For example, while creating your own button for REQUEST_FLOOR use the ***setImage*** function and pass two images (first image for normal state and second image for selected state). But for USER_LIST and MENU ***setImage*** function takes a single parameter. For details, please follow the below code snippet:

```js
val setting = EnxSetting.getInstance(this)

// Enumerated values to use for TopOption are
// USER_LIST, MENU, REQUEST_FLOOR 

val userList = EnxButton(this,EnxSetting.TopOption.USER_LIST.tag) 
userList.setImage(R.drawable.participant_icon) 

val webinarButton = EnxButton(this,EnxSetting.TopOption.REQUEST_FLOOR.tag) 
webinarButton?.setImage(R.drawable.notification_icon, R.drawable.notification_icon_selected) 

val menu = EnxButton(this,EnxSetting.TopOption.MENU.tag) 
menu.setImage(R.drawable.ic_more_vert)  

 
setting.configureTopOptionList(listOf<EnxButton>(menu,userList, webinarButton)) 
```

- **Steps-7** Set Background Color of Bottom Bar

You can update the background color of Bottom Bar by passing resource id of the color to ***updateBottomOptionView*** function.

```js
val setting = EnxSetting.getInstance(this) 
setting.updateBottomOptionView(R.color.white) 
```

- **Steps-8** Set Background Color of Top Bar

You can update the background color of Top Bar by passing resource id of the color to ***updateTopOptionView*** function.

```js
val setting = EnxSetting.getInstance(this) 
setting.updateTopOptionView(R.color.white) 
```

- **Steps-9** Customize Participant List Options

You can add additional action against each participant in the participant list.

```js
val setting = EnxSetting.getInstance(this) 

val audioButton = EnxButton(this,EnxSetting.PartcipantList.AUDIO.tag) 
audioButton.setImage(R.drawable.audio_on,R.drawable.audio_off) 
 
val videoButton = EnxButton(this,EnxSetting.PartcipantList.VIDEO.tag) 
videoButton.setImage(R.drawable.video_on,R.drawable.video_off) 
 
val chatButton = EnxButton(this,EnxSetting.PartcipantList.CHAT.tag) 
chatButton.setImage(R.drawable.chat_icon) 
 
val dissButton = EnxButton(this,EnxSetting.PartcipantList.DISCONNECT.tag) 
dissButton.setImage(R.drawable.end_call_new) 

 setting.configureParticipantList(listOf<EnxButton>(audioButton,videoButton,chatButton, dissButton)) 

// Following Enumerated data may also be used to creation action buttons
// in Participatn list, viz. AUDIO, VIDEO, CHAT, DISCONNECT 
```

- **Steps-10** Handle Disconnection and Correction Error

Here you need to create an instance of ***EnxVideoView*** class which is the subclass of ***RelativeLayout***. You also need to pass a reference of Activity, a valid Token, and Observer to receive callback. 

There are 2 callbacks for you to clear instance or for any other UI/UX implementation. You need to override these functions below:

  - *For Disconnection*: You get notified when the user gets disconnected from the Video Room. The JSON you receive shows reason for disconnection.

  ```js
override fun disconnect(jsonObject: JSONObject?) 
```
- *For Connection Error*: You get notified if the user doesn’t get connected to the Video Room. The JSON you receive shows related error.
```js
override fun connectError(jsonObject: JSONObject?) 
```