# How to use React Native Video UIKit?

## Install React Native UI Kit

To install **React Native UI kit** and **Video SDK**, do the following:

1. Open the Terminal.
2. Go to the React Native Project directory.
3. Run the following command to install **React Native UI Kit**:
```
npm install enx-uikit-react-native
```
4. Run the following command to install **React Native Video SDK**:
```
npm install enx-rtc-react-native
```

## Requirements

* Vscode and Android Studio (*Recommended to use Latest version*).
* Enablex Developer Account (*Sign up*).
* A valid token to join room.
* XCode (*Recommended to use Latest version*).
* An iOS or Android Device for testing the Application.
* Basic understanding of React Native development.

## Define Device Permissions

To define device permissions for **Android**, do the following:
1. Open the `AndroidManifest.xml` file.
2. Add the required device permissions to the file.
```
<manifest> 
... 
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.RECORD_AUDIO" /> 
<uses-permission android:name="android.permission.CAMERA" /> 
<uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />  
... 
</manifest> 
```
3. After adding the permission in the AndroidManifest.xml file, do code at your app level to show the dialog to grant permissions.

To define device permissions for **iOS**, do the following:
1. Open `info.plist`.
2. Add `NSCameraUsageDescription` and `NSMicrophoneUsageDescription`. This is needed to add permission into to your application.

## Initializing the Enx React Native UIKit
To use React Native UIKit SDK, do the following:
1. Use npm to install it.
2. Import `EnxVideoView` to your application with comand given below.
3. Pass Token to `EnxVideoView`.
```
import {EnxVideoView} from "enx-uikit-react-native" 

<EnxVideoView 
	token={tokenObj} 
	embedUrl= {URL of Video Embed to get Config Info} 
	setting = {this.state.setting} 
	onDisconnect = {this.onDisconnect}  
	connectError = {this.connectError} 
	customButtonHandler = {this.customButtonHandler} 
/>
```
The table below consists of the description of each parameter in the command:
| Parameter | Description |
| --- | --- |
| *Token* | Use EnableX Video Room Token to join Video Session |
| *embedUrl* | Use URL of Low Code Video Embed to get Configuration Information in case you look to get Embed Tool Settings imported into the UIKit |
| *setting* | Settings of Topbar and Bottombar in the Video Session Interface. Use true to enable a feature, false otherwise. Also, use Color Code for different elements as needed |
| *onDisconnect* | Get notified when user gets disconnected from Video Room |
| *connectError* | Get notified when user fails to connect to Video Room |
| *customButtonHandler* | To handle event for the custom button |

**Note:** In the `setting` parameter, you can use Color Code for the different elements as needed.
Example:
```
setting: [ 
	/* Enable Tools in Bottombar */
	bottomOption=[ 
		{	AUDIO: true	}, 
		{	VIDEO: true	}, 
		{	SWITCH_CAMERA: true },
		{	SWITCH_AUDIO: true }, 
		{	GROUP_CHAT: true }, 
		{	DISCONNECT: true },
		{	CUSTOM_BUTTON: true, 
			imagePath: require('./image_asset/recording_on.png')
		} 
	], 
	/* Enable Tools in Topbar */
	topOption=[ 
		{	USER_LIST: true	}, 
		{	MENU: true	} 
	], 
	bottomBarColor={ 
		COLOR: '#FF0000' 
	}, 
	topBarColor={ 
		COLOR: '#FF0000' 
	} 
] 
```

## Customize Participant List with Options

You can configure the participant list with optional action items per your need. To enable these, put “true” against each, and the enabled action will be made available against each participant in the Participant List.

To configure pass the following array in the setting:
```
participantOption=[ 
	{VIDEO: true},		// To enable hard stop Video
	{AUDIO: false},		// To enable hard mute Audio 
	{CHAT: true},		// To enable Private Chat
	{DISCONNECT: true},	// To enable force disconnect 
] 
```
Given below is the overall setting array:
```
setting: [ 
	participantOption=[ 
		{VIDEO: true},		// Enable hard stop Video
		{AUDIO: false},		// Enable hard mute Audio 
		{CHAT: true},		// Enable Private Chat
		{DISCONNECT: true},	// Enable force disconnect 
	],

	bottomOption=[ 
		{SWITCH_CAMERA:true},	// Enable Switch Camera
		{VIDEO: true},		// Enable Video Mute
		{AUDIO: true},		// Enable Audio Mute
		{SWITCH_AUDIO:true},	// Enable Switch Mic
		{GROUP_CHAT:true},	// Enable Group Chat
		{DISCONNECT: true},	// Enable Disconnect
		{	CUSTOM_BUTTON:false,
			imagePath:require('./image_asset/recording_on.png')
		} 
	], 

	topOption=[ 
		{USER_LIST:true},	// Enable Participant List
		{MENU:true},		// Enable Menu
	], 

	bottomBarColor={ 
		COLOR:'#D3D3D3'		// Bottombar Color
	}, 

	topBarColor={ 
		COLOR:'#D3D3D3'		// Topbar Color
	}, 
]
```