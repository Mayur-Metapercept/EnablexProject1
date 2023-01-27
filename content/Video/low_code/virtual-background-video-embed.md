---
title: "Virtual Background with Video Embed"
date: 
description:
type: "docs"
weight: 2
---
At a time when nearly everyone is working from home and dialing into meetings, a virtual video background is a way to use a professional backdrop to represent your company, you could add a polished look to your professional meetings.
# Overview
The Virtual Background feature allows users to blur own Video Background or to use a image from Library as as Video Background. This feature works best with a physical green screen at your backdrop or with uniform lighting on a plain backdrop. In other cases, user may experience patchy edges.
# Setup Virtual Background
In case you look to use Virtual Background in your Embed, you need to do the following:

## Enable Virtual Background
To use Virtual Background with your Embed, you must first enable it through the Visual Builder. Visual Builder helps you to edit the Embed Template by opting more features to use. Do the following in the Portal:
- **Approach**
    - **While getting started with Embed**: At 4th Step of “Get Started” wizard, you get “Visual Builder” to make edits on the chosen Template.
    - **To use with pre-configured Embed**: From “Video -> Settings” menu; you reach Embed Dashboard. Pull out the “Video Embed” dropdown and select “Edit Template” to get the “Visual Builder”.
    ![Video Embed](./low-code-video-embed-1.png)
- **Enable**
    - Go to the “*Manage Features*” tab of “*Visual Builder*”.
    - You get the “**Virtual Builder**” feature. Check the chechbox against it to enable.
    - Click “**Build App**” button to update your Embed with this feature.
    ![Edit Template](./edit-template.png)
- **Experience**
    - Open your App with the Video Embed.
    - See the Virtual Background option in Toolbar. Click it.
    - It opens up a Preview Virtual Background tool before purlishing. It comes with pre-configured “Blur” background Option.
    - Try it to experience.
## Setup Default Image Library
You need to define a Image Library which will be used in the Video Embed for users to use as their Virtual Background. Portal helps you setup your Image Library by adding maximum of 10 External Image URLs.

- Go to Portal. Follow “Video -> Settings” menu to reach Embed Dashboard.
- Pull out the “*Video Embed*” dropdown and select “*Vitual Backgrounds*”
![Video Embed](./video-embed-2.png)
- Virtual Background Image Library Tool: This tool gives you a list of images for your Virtual Background Image Library if already defined. You need to add External Image URLs in seperate lines in the TEXTAREA.
    - Image URLs must be hosted on “https”. Hosting Server must handle CORS issue. If CORS issue is faced, Embed will fail to use the Image.
    - Maximum allowed Image URL: 10
    - Maximum Dimension of Image: 600x400px (Prescribed for better performance)
    - Image Format: JPG, JPEG
    - Image Size: 200KB (Prescribed for better performance)
# Dynamic Image Library using Query String
Image URL for Virtual Background may also be passed through Query String. So, query string helps you to pass different image URL while embedding for a user. When Query String Parameter is used to define Image Library, it overrides Default Image Library.
- Use virtual_bg_imgs=IMG_URL as query String parameter. You can use this parameter multiple times in cas eyou want to add more than one image.
- Image URLs must be hosted on “https”. Hosting Server must handle CORS issue. If CORS issue is faced, Embed will fail to use the Image.
- Maximum Dimension of Image: 600x400px (Prescribed for better performance)
- Image Format: JPG, JPEG
- Image Size: 200KB (Prescribed for better performance)
**Note**: See detailed explanation on [Query String Parameters](./query-string-parameters-video-embed.md).
