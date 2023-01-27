

# How to use Android Video UIKit?

Follow these steps:

- **Step-1**: Download latest Android SDK (Android Archive Library).

- **Step-2**: Download latest Android UIKit (Android Archive Library).

- **Step-3**: Add downloaded AAR files to the ***lib*** folder.

- **Step-4**: Go to your Project’s root directory and edit build.gradle by placing the following code in the ***allprojects.repositories*** section:

```js
allprojects{ 
repositories { 
		flatDir { 
			dirs 'libs' 
		} 
	} 
}
```

- **Step-5**: Go to your application level ***build.gradle*** file and add the following code in the dependencies section:
 
 ```js
implementation fileTree(dir: 'libs', include: ['*.aar', '*.jar'], exclude: []) 
implementation('io.socket:socket.io-client:1.0.1') { 
	exclude group: 'org.json', module: 'json' 
} 
```

## Define Device Permissions

Define permissions in AndroidMainfest.xml as shown below:

```js
<uses-permission android:name="android.permission.CAMERA" /> 
<uses-permission android:name="android.permission.RECORD_AUDIO" /> 
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> 
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" /> 
<uses-permission android:name="android.permission.BLUETOOTH" android:maxSdkVersion="30"/> 
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" android:maxSdkVersion="30"/> 
<uses-permission android:name="android.permission.WAKE_LOCK" /> 
<uses-permission android:name="android.permission.BLUETOOTH_SCAN"android:usesPermissionFlags="neverForLocation"/> 
<uses-permission android:name="android.permission.BLUETOOTH_ADVERTISE" /> 
<uses-permission android:name="android.permission.BLUETOOTH_CONNECT" /> 
```