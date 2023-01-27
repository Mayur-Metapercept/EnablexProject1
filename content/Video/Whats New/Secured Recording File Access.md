---
title: "Secured Recording File Access"
date: 
description:
type: "docs"
weight: 2
---
## Overview ##

All Session Files, which include Recordings, Transcoded Videos, Chat Scripts and Meta Files of EnableX Video Sessions, were available through a publicly accessible HTTP URL within the first 72 hours of session expiry. 

**NOTE:** These open URL access will cease to exist from **May 15, 2022**.

EnableX has implemented a secured access mechanism to the Session Files through HTTP Basic Authentication.

## Old URLs of Recording Files ##
EnableX provided a direct HTTPS URL to the file at: 
[Recording File](https://portal.enablex.io/path/file.mp4)

The URLs were provided in the following ways:
- To business Applications:
    - Video API: Using the Video API, you can fetch a list of Recordings through an HTTP GET request to its archive route. The JSON response returns Recorded File paths.
    - Webhook Post: EnableX notifies you as soon as any Recording file(s) are available for your concluded sessions. The JSON posted to Notification Webhook URL as Raw Body contains META information of the Session with an Array of Recorded File paths.
- To Report:
    - In EnableX Portal
## Secured Recording File Access ##
Once the Secured Recording File Access mechanism is implemented, there is no change in the distribution of recording file paths. However, using a URL to access a file is changed to using the username and password.

**Access Example**
-
When you try to access the following URL:
[Recording File](https://portal.enablex.io/path/file.mp4)
- Using Programming: EnableX Service will send HTTP 403 header that is the FORBIDDEN response.
- Using Browser: Browser will prompt you with a dialogue box to enter the Username and Password to access the file.
![Enter Username and Password](https://github.com/metapercept/enablex-io/blob/master/content/Images/Secured%20Recording%20File%20Access.png)

**How to access the file through authentication?**
- Using the Browser: Enter Username and Password to access the file in the dialogue box when prompted. Once Credentials are validated and passed through, you get access to the file. For subsequent file access, it is not necessary to provide the username and password credentials.
- Using Programming: Update the URL to access the Recording file as explained below:
If the following URL is used:

    [Recording File](https://portal.enablex.io/path/file.mp4)

    We receive a HTTP error code 403 as response.

    Update the URL with Username and Password as below:

    [Updated URL](https://username:password@portal.enablex.io/path/file.mp4)

    The exact process is applicable to access transcoded files, chat-script, and meta files.

## Access Credentials ##

### Find Preset Username or Password ###

Follow the steps below to find the credentials to access the Recordings and all other session files.
- Login to the Portal
- Navigate to **Video**, select **Insights & Reports**
- Click the **Recordings** tab
- In the Search Filter Section, select the Project from the dropdown list. Click **Apply**.
- Recordings of the Project are displayed.
- The Username and the preset Password for recording file access are displayed at the top of the Report. Use these credentials to access the recorded file.
- Once the password is reset, this information is not displayed.

    ![Access Credentials](https://github.com/metapercept/enablex-io/blob/master/content/Images/Access%20Credentials.png)

## Reset Your Password ##
To access the recorded files, enter the default login credentials. 
For password setup, follow the procedure:
- Login to the EnableX Portal
- Navigate to Video, select **Settings**
- Click the **Recording** tab and navigate to **Recording Access Control** Section to change the default password.
    - Note: This section only appears when you have at least one session recording after **May 15, 2022**.
- Enter your account password
- Enter the new access password. The password must be of a minimum of ten characters.
- Re-enter the access password to confirm the password
- Click **Submit** to confirm the request.
![Submit](https://github.com/metapercept/enablex-io/blob/master/content/Images/Reset%20Your%20Own%20Password.png)

## Update Business Application ##

If your Business Application accesses the Recording files and any other session files using API Call or WebHook Post, update your Application so that it passes through the HTTP 403 Error.
Follow the steps explained above to update File URLs with username and password. 

**Note:** Update your Application before **May 15, 2022,** to ensure the Application functions without any issues.
