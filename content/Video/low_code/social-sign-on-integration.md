---
title: "Social Sign-On Integration with Video Embed"
date: 
description:
type: "docs"
weight: 2
---
EnableX Low Code Video Embed can be integrated with Social Sign-On with Google and Facebook. At the Landing Page, instead of entering name, users can simply join through Google or Facebook login. This SSO utilities can be configured through EnableX Portal using own Facebook and Google Account. 
# Overview
Social Sign-On integration is aimed to provide options for users getting into the Video Session through Google and Facebook authentication without having to fill in their name at the Embed Landing Page. This is an optional setting for Landing Page.
# Landing Page with SSO
When you configure your Embed to use SSO through Google or / and Facebook, Embed Landing Page would feature respective SSO Button(s) for users to choose. Once logged in, user may stay signed-in to join session in a single click from Landing Page.
![Landing Page](./sso-landing-page.png)
# Setup through Portal
EnableX Embed may be configured with the following SSO:

- Google
- Facebook
You may opt to use either or both with your Embed through EnableX Portal. To configure, follow the steps given below:

- Login to EnableX Portal
- Following Sidebar Menu “Video” and see “Settings” option.
- After reaching Video Settings page, select the right Project from the drop-down at the top of page.
- All settings are grouped in different tabs. Click on the “Features” Tab and see “Landing Page” option. Click it to open the pane.
![Set Up](./set-up.png)
- In the “Landing Page” pane, see a section called “Social Sign-On”. You get to see all supported SSO, viz. Google and Facebook.
![Landing Page](./Landing-Page-Setup.png)
- To enable either or both, you need to enter related Client ID. Follow instructions in the related sub-sections below:
## Google SSO Integration
To enable Google SSO, you need to enter all you need to add your Google Client ID from your own Google Account.

- [Read Google API Document](https://console.cloud.google.com/apis/credentials)– How to get Google Client ID.
- [Watch the Tutorial Video](https://youtu.be/xH6hAW3EqLk) – How to create Google OAuth Credentials (Client ID and Secret)
## Facebook SSO Integration
To enable Facebook SSO, you need to enter all you need to add your Facebook Client ID from your own Facebook Account.

- [Facebook App Development](/https://developers.facebook.com/)
- [Watch the Tutorial Video](https://youtu.be/jMVlSDU-6l4) – How to create Facebook App ID for Website login (OAuth client ID and secret – Enable Live mode)
