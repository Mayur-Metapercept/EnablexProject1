---
title: "Recording Watermarking"
date: 
description:
type: "docs"
weight: 2
---
# Overview

Watermarking is now available with session recording files. Upload a watermark file against your project and enable your room with the following settings:

`watermark:true`

Watermark your recorded files with an Image File uploaded through your Portal against your Project. [Transcoded Files](https://www.enablex.io/developer/video-api/client-api/web-toolkit/recording/#rec-file-type) will only be watermarked.
Follow the two points below to get transcoded files watermarked:

- ## Provision for Watermark Files ##

Upload the watermark file against your Project. Follow this path:

*Portal Login > Video > Settings > Recording > Watermarking*

- Image Format: PNG
- Image Dimension: 140×140 px (Maximum)

- ## Enable Room for Watermarking ##

You need to define your room to enable Watermarking in it. Use the setting:

`watermark=true`

![Enable Room for Watermarking](https://github.com/metapercept/enablex-io/blob/master/content/Images/Enable%20Room%20for%20Watermarking.png)
