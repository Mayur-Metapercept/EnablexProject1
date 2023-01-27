---
title: "Low Code Video Embed with React Native App"
date: 
description:
type: "docs"
weight: 2
---
To use Low Code Video Embed with your React Native App, follow the Steps given below:

# Step#1
Install expo-permission by using following command:

*expo install expo-permissions*

# Step#2
Use the function given below to get Media Device permission before loading the view:
```
async function loadPermission () {
	try {
		const {granted} = await permission.askAsync(
			permission.CAMERA,
			permission.AUDIO_RECORDING
		);

		if(granted) {
			// Device Access available. To code further
		} else {
			// Device Access not available. Code to handle
		}
	} catch(error) {
		alert(error);
	}  
}
```