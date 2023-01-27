---
title: "iOS Screen Share"
date: 
description:
type: "docs"
weight: 2
---
Screen Share feature is an important feature with a real-time communication platform. For the user to have a continued broadcast screen, the user needs to broadcast an extension in his Application as the App goes in the background.
---
Note: *You must have iOS 12+ to make screen share work in iOS.*
# Live Broadcast using ReplayKit Library
Using the ReplayKit library, users can build app extensions for live broadcasting.
**Class**: *RPSystemBroadcastPickerView*
## Add the Broadcast Extension
- Go to Project > File > Target > Broadcast Upload Extension  
![Broadcast Extension](./broadcast-extension.png)
- Set the bundle ID for Broadcast target Exm – *com.companyName.Appname.Broadcast.extension* 
After adding the broadcast extension, make sure that you have added the correct bundle id for your broadcast extension and your App.
## Open the Broadcast Extension through RPSystemBroadcastPickerView
Add the below code and run the Application. The broadcast will be open and you will start receiving the sample buffer (buffer frame of your image).
```
RPSystemBroadcastPickerView *pickerView = [[RPSystemBroadcastPickerView alloc]initWithFrame:CGRectMake(0, 0, 50, 50)];
pickerView.translatesAutoresizingMaskIntoConstraints = false;
pickerView.autoresizingMask = (UIViewAutoresizingFlexibleTopMargin | UIViewAutoresizingFlexibleRightMargin);
NSURL *url = [[NSBundle mainBundle] URLForResource:@"BroadCastExtension" withExtension:@"Appex" subdirectory:@"PlugIns"];
 if(url != nil){
       NSBundle *bundle = [NSBundle bundleWithURL:url];
        if(bundle != nil){
   pickerView.preferredExtension= bundle.bundleIdentifier;
       }
  }
 pickerView.hidden = true;
 pickerView.showsMicrophoneButton = false;
 SEL buttonPress = NSSelectorFromString(@"buttonPressed:");
 if ([pickerView respondsToSelector:buttonPress]){
         [pickerView performSelector:buttonPress withObject:nil];
 }
[self.view addSubview:pickerView];
[self.view bringSubviewToFront:pickerView];
pickerView.center = self.view.center;
[self.extensionContext loadBroadcastingApplicationInfoWithCompletion:^(NSString* _Nonnull bundleID,NSString *_Nonnull displayName, UIImage *_Nullable AppIcon){
            if(AppIcon != nil){
                
            }
        }];
```
You receive sample buffer in the broadcast class *Sample Handler* through a delegate method.

**Class**: *Sample Handler*

Delegate Method: - *(void)processSampleBuffer:(CMSampleBufferRef)sampleBuffer withType:(RPSampleBufferType)sampleBufferType; get buffer frame*

Other delegated methods are listed below:

- *(void)broadcastFinished* – If the broadcast has stopped/finished
- *(void)broadcastPaused* – If the broadcast has paused
- *(void)broadcastResumed* – To resume the broadcast
## Broadcast the Device Screen to EnableX server
EnableX iOS SDK functions with the broadcast extension to broadcast your device screen and it publishes over the EnableX server.

Add App group capabilities to the App and the broadcast extension. It enables the exchange of data from the App to the extension and vice versa.
- Add app group to your application.
    - Go to Testing > TARGETS (select your application)  > Capability > App Groups
![App Groups Application](./App-Groups.png)
- Add app group to your broadcast extension.
    - Go to Testing > TARGETS (select your broadcast) > Capability > App Groups
![App Group Targets](./app-groups-2.png)
- Join EnableX Conference through your application, store your *roomID* through *NSUserDefaults* or any other storage that can help you to get the same *roomID* in the broadcast extension as well.
```
NSUserDefaults *userDaf = [[NSUserDefaults alloc]initWithSuiteName:@"group.com.enx.Videocall"];
        [userDaf setObject:[@"your roomID through which you have joined EnableX Room" objectForKey:@"RoomId"] forKey:@"RoomId"];
[userDaf synchronize];
```
- Get self *clientID* and store with *NSUserDefaults* after successfully joining the EnableX Room.
```
NSUserDefaults *userDefault = [[NSUserDefaults alloc]initWithSuiteName:@"group.com.enx.Videocall"];
[userDefault setObject:_remoteRoom.clientId forKey:@"ClientID"];
 [userDefault synchronize];

```
- Pass the app group key to Enablex SDK after storing the *clientID* in *userDefault*.
```
[[EnxUtilityManager shareInstance] setAppGroupsName:@"group.com.enx.Videocall" withUserKey:@"ClientID"];
```
- Start the broadcast through *RPSystemBroadcastPickerView* after sharing the *roomID* and the *ClientID*.
- Use the class *SampleHandler* to broadcast extension in *RPSystemBroadcastPickerView*. This class notifies all events to the user.
    - Next, add one class that will help you to get an update from SampleHandler and pass it to the EnableX iOS SDK.
    - Important:-The user needs to join the EnableX room with the help of the same roomID shared through the main application.
## Connect to the Broadcast Extension
*SampleHandler* will initiate the helper class (the class that you have created inside the broadcast extension). On successful connection to broadcast extension, you will receive a delegated method in *SampleHandler*.
- *(void)broadcastStartedWithSetupInfo:(NSDictionary< NSString *,NSObject * > *)setupInfo*
After getting this delegated method, connect to the EnableX Room with the same *roomID* and pass through the main application.
- Get the same *roomID* stored in *USerDefault*
```
NSUserDefaults *userDefault = [[NSUserDefaults alloc] initWithSuiteName:@"group.com.enx.Videocall"];
NSString *roomId = [userDefault objectForKey:@"RoomId"];
```
- Pass the stored app group name to EnableX SDK at the same time
```
[[EnxUtilityManager shareInstance] setAppGroupsName:@"group.com.enx.Videocall" withUserKey:@"ClientID"];﻿
```
- Create a EnableX token and connect with room after getting the *roomID*
```
EnxRoom *remoteRooml = [[EnxRoom alloc]init];
[remoteRooml connectWithScreenshare:respinseDict[@"token"] withScreenDelegate:self];
```
User receives a callback from EnableX iOS SDK on successful room connection as below:
- *(void)broadCastConnected;*
If the room connection gets failed due to any cause, the user will receive a failure callback through EnableX iOS SDK as below:
- *(void)failedToConnectWithBroadCast:(NSArray *)reason*
## Start Screen Share
The *EnxRoom.startScreenShare()* method is used to create a Screen-Sharing Stream @ 6fps to publish in the Room. 
EnableX SDK organizes the screen share and publishes it over the EnableX Media channel. Once screen share is published successfully, the broadcast extension class receives a callback method and the application receives an acknowledgment method for starting the screen share.
**Class**: *EnxRoom*
**Methods**:

- *[enxRoom startScreenShare];*
- *(void)didStartBroadCast:(NSArray *)data* – After publishing the Shared-Screen Stream, the broadcast extension class receives this callback method.
- *(void)room:(EnxRoom *)room didStartScreenShareACK:(NSArray *)Data* – For starting the screen share, the application receives this acknowledgment method.
## Send the Video Buffer Frame to EnableX Room
Once you are connected to the room and have started screen share, start sending video buffer frame to EnableX Room.
*-(void)sendVideoBuffer:(CVPixelBufferRef _Nonnull)sampleBuffer withTimeStamp:(int64_t)timeStampNs;*
where *SampleBuffer* is the frame of the screen and *TimeStampNsc* is in a nanosecond.
Let us consider that the user receives the “*CMSampleBufferRef*” from the broadcast.
- Convert “*CMSampleBufferRef*” with “*CVPixelBufferRef*”
    - *CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(bufferImage);*
- Create a time stamp in “int64_t” format
    - *int64_t timeStampNs = CMTimeGetSeconds(CMSampleBufferGetPresentationTimeStamp(bufferImage)) *1000000000;*
## Compress the Sample Buffer Frame
The user receives the buffer image once the broadcast extension has started successfully through the broadcast callback method.

Note: The broadcast extension has a limitation of max 50M memory at run time. In case, if this memory exceeds, in that case, the broadcast extension will terminate giving a memory warning.

The user needs to compress the sample buffer frame (the buffer frame received through the broadcast extension) either by using vImage crop or any other crop methodology.
- *(void)processSampleBuffer:(CMSampleBufferRef)sampleBuffer withType:(RPSampleBufferType)sampleBufferType;*
## Stop Screen Share
The *EnxRoom.stopScreenShare()* method is used to stop the ongoing screen sharing.

Once the screen share is unpublished, the broadcast extension class receives a callback method and the application receives an acknowledgment method for starting the screen share.
**Class**: *EnxRoom*

**Methods**:

- *[enxRoom stopScreenShare];*
- *(void)didStoppedBroadCast:(NSArray *)data* – After unpublishing the shared screen stream, the broadcast extension class receives this callback method.
- *(void)room:(EnxRoom *)room didStartScreenShareACK:(NSArray *)Data* – For stopping the screen share, the application receives this acknowledgment method.
## Disconnect the Room
The user needs to disconnect the room connected through the broadcast extension for the screen share after the screen share has stopped.
**Class**: *EnxRoom*

**Methods**:

- *[enxRoom disconnect]*;
- *(void)broadCastDisconnected;* – After the broadcast room is disconnected, the broad extension receives a room disconnected callback
- *(void)disconnectedByOwner;* – During ongoing screen share if parent use got disconnected due to any reason, the broadcast extension receives a callback from EnableX iOS SDK using this method.
**Events**:

- *[self finishBroadcastWithError:nil];* – After receiving this callback event, the user needs to stop the broadcast.
## Exit Screen Share
The *EnxRoom.exitScreenShare()* method is used by the parents to stop the ongoing screen sharing.

**Class**: *EnxRoom*

**Method**: *(void)exitScreenShare*;

**Delegate Methods**:

- *(void)room:(EnxRoom *_Nullable)room didExitScreenShareACK:(NSArray *_Nullable)Data;* – Acknowledgment callback for the parent client.
- *(void)didRequestedExitRoom:(NSArray *_Nullable)Data;* – Notification received by the child client (screen share client). As the screen share client receives this callback, they initiate to stop the broadcast and disconnect from the room.
## Error Codes / Exceptions
| Code      | Description |
| ----------- | ----------- |
| 5137      | Screen Share is not running in conference       |



