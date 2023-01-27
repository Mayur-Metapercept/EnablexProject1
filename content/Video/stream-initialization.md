---
title: "Stream Options to initialize"
date: 
description:
type: "docs"
weight: 2
---
```
{
     "audio": true,          // Whether to add Audio to stream
     "video": true,          // Whether to add Video to stream
     "data": true,           // Whether to add Data to stream
     "screen": false,        // Whether to add Screen Share to stream
     "videoSize": [minWidth, minHeight, maxWidth, maxHeight], // Video Frame Size - Deprecated in Android SDK v2.0.1+, iOS SDK v2.0.1+, React Native SDK v1.6+ & Flutter SDK v1.6+.
     "audioMuted": true,     // Audio muted on entry to room  
     "videoMuted": true,     // Video muted on entry to room  
     "attributes": {         // Object to carry custom data  
         "custom1": ""
      },
     "options": {}           // Video Player Options */
     "videoSize": [minWidth, minHeight, maxWidth, maxHeight],
     "maxVideoLayers": Number// Number of Video Layers in Stream
                             // Enumerated Values: 1, 2, 3                               
                             // 1=HD 720p layer only
                             // 2=HD 720p & SD 480p layers only
                             // 3=HD 720p, SD 480p & LD 240p/180p layers  
 }
 ```