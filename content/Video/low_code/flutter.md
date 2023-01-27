---
title: "Low Code Video Embed with Flutter App"
date: 
description:
type: "docs"
weight: 2
---
We recommend to:

- Use the *flutter_inappwebview* and *permission_handler* modules to handle Media Device permissions in the *webview*.
- Update Settings in your iOS and Android projects to match your requirements.
- Add the *WebView* component to your code,. Setup properties and fill the room URL and parameters.
**Note**: There is a known issue to show the keyboard in Android *webviews*.
```
import 'dart:io';

import 'package:flutter/material.dart';
import 'package:flutter_inappwebview/flutter_inappwebview.dart';
import 'package:permission_handler/permission_handler.dart';

var _lowCodeUrl = "YOUR-LOW-CODE-EMBED-MEETING-URL"; 

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    if (Platform.isAndroid) {
      _lowCodeUrl += '?skipMediaPermissionPrompt';
    }
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: InAppWebViewPage(),
    );
  }
}

class InAppWebViewPage extends StatefulWidget {
  const InAppWebViewPage();

  @override
  State<InAppWebViewPage> createState() => _InAppWebViewPageState();
}

class _InAppWebViewPageState extends State<InAppWebViewPage> {

  @override

  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Meeting")),
      body: Column(children: <Widget>[
        Expanded(
          child: InAppWebView(
            initialUrlRequest: URLRequest(url: Uri.parse(_lowCodeUrl)),
            initialOptions: InAppWebViewGroupOptions(
              crossPlatform: InAppWebViewOptions(
                mediaPlaybackRequiresUserGesture: false,
              ),
              ios: IOSInAppWebViewOptions(
                allowsInlineMediaPlayback: true,
              )
            ),
            androidOnPermissionRequest: (
              InAppWebViewController controller,
              String origin, List<String> resources) async {
                await Permission.camera.request();
                await Permission.microphone.request();
                return PermissionRequestResponse(
                  resources: resources,
                  action: PermissionRequestResponseAction.GRANT
                );
              },
            ),
          ),
        ]
      )
    );
  }
}
```
