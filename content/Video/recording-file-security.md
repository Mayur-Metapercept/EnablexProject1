---
title: "Video Recording File Security"
date: 
description:
type: "docs"
weight: 2
---
Recorded files accessible through HTTP URL within the first 72 hours of recording will no longer remain accessible over open HTTP URL, rather they will be protected through HTTP Basic Authentication Process w.e.f. May 15, 2022.
# Overview
All Session Files, viz. Recordings, Transcoded Video, Chat Scripts and Meta Files of EnableX Video Sessions were available to you through a publicly accessible HTTP URL within the first 72 hours of session expiry. These open URL access will cease to exist w.e.f May 15, 2022.

EnableX implemented a secured access mechanism to the Session Files through HTTP Basic Authentication.

Note: This is a breaking change to be made effective on May 15, 2022. Therefore, your Application may need to be updated to this effect.
# Old URLs of Recording Files
EnableX used to provide a direct HTTPS URL to the file as – [Direct HTTPS URL](https://portal.enablex.io/path/file.mp4)

These URLs were given in the following ways:

- **To business Applications**:
    - **Video API**: Using the Video API, you can fetch a list of Recordings through an HTTP GET request to its archive route. The JSON response returns Recorded File paths.
    - **Webhook Post**: EnableX notifies you as soon as any Recording file(s) are available for your concluded sessions. The JSON posted to Notification Webhook URL as Raw Body contains META information of the Session along with an Array of Recorded File paths.
- **To report**:
    - In EnableX Portal
# Secured Recording File Access
After the Secured Recording File Access mechanism is implemented, the recording file paths will continue to be distributed exactly as done today, however, using the same URL to access a file will be changed to provide the username/password.

## Access Example
When you try to access the following URL:

[URL] (https://portal.enablex.io/path/file.mp4)

- Using Programming: EnableX Service will send HTTP 403 header i.e. FORBIDDEN.
- Using Browser: Browser will prompt you with a dialog to enter the Username / Password to access the file.
![Sign In](./sign-in.png)
## How to access file through authentication?
- **Using Browser**: Enter Username / Password to access the file in the dialog when prompted. Once Credentials are validated and passed through, you get access to the file. All subsequent file access using any other recording URLs will not be challenged to re-enter credentials within the same browser session.
- **Using Programming**: Re-do/Update the URL to access the Recording file as explained below:
Following URL Access is responded with an HTTP 403 error.

[URL](https://portal.enablex.io/path/file.mp4)

Update URL with username and password and try to access the file using the updated URL. You will be granted access.

[URL](https://username:password@portal.enablex.io/path/file.mp4)

Therefore, all you need to do is to update the Recording URL given programmatically with your username and password to make it work for you. Follow the same process to access transcoded files, chat-script, meta files too.
# Access Credentials
## Find Preset Username/Password
Follow the steps given below to find the credentials to access the Recordings and all other session files.

- Login to the Portal
- Navigate to Video > Insights & Reports
- Click the “Recordings” tab.
- In the Search Filter Section, select the Project from the dropdown. Click Apply.
- This will show up recordings of the Project.
- The Username and the preset Password for recording file access is shown at the top of the Report. Use these credentials to access the recorded file.
- When you reset your password, this information will no longer be shown.
![](./reset-password.png)
## Reset Your Own Password
To access the recorded files, enter the default credentials. In case you want to set up your password, follow the steps below:

- Login to the Portal
- Navigate to Video > Settings
- Click the “Recording” tab and go to the “Recording Access Control” Section to change the default password.
    - **Note**: This Section appears only when you have at least 1 session recording after May 15, 2022.
- Enter your account password
- Enter new access password. The password must be of minimum 10 characters.
- Re-enter the access password to confirm
- Click “Submit” to confirm the request
![Submit](./submit.png)
## Update Business Application
In case your Business Application accesses Recording files and any other session files using API Call or Web Hook Post, you need to update your App to the effect to pass through HTTP 403 Error.

Follow the steps explained above to update File URLs with username and password. You are requested to update your app before May 15, 2022 to ensure your App works without any hindrance.