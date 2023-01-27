---
title: "Co-Browsing with Video Embed"
date: 
description:
type: "docs"
weight
---
Co-browsing is ‘collaborating browsing’ and this allows both the moderator and the participant to simultaneously navigate the same web page.
# Overview
Co-browsing is collaborative and interactive in the way that it allows participants joining in a video call to actively browse together. And on top of this, co-browsing is simultaneous and synchronous. That way both participants in a co-browsing session can see what the other person is doing on the screen.

Examples of how to use co-browsing to make remote contact with your customers more interactive:

- Fill out forms and applications together, guiding the participant through the process in real-time.
- Showcase two-way interactive presentations, more engaging for your prospects.
# How does co-browsing work?
Co-Browsing with others is related to a Website or Webpages. So, your Website or Webpages which are to be co-browsed, must be made ready for Co-Browsing first. Once they are ready, you Invite others to join a Co-Browsing session with you through a Unique URL, i.e. existing URL with some Query String Parameters.

Once other person joins, both can see each other Cursor Position on the page and all actions at one end get replicated at the other end. If one clicks on a link, the other end already reaches the same page.

You can invite more people to join in the same Co-Browsing Session.
# Co-Browse with Video Embed
Let’s know how to use Co-Browsing with Video Embed.
## Update your Website/Webpage to Co-Browse
Let’s get your Website ready for Co-Browsing. Follow the simple steps given below:

- You need a JS file named *EnxCoBrowse.js.* Download it. This is a file that helps in easy integration of Co-Browsing.
- You downloaded a zip file. Extract it and save the JS file within your Website’s accessible path.
- Add the Code given below in each webpage you want for Co-Browsing either within HEAD tag or towards the end of page.
```
<script src="/PATH/EnxCoBrowse.js"></script>
<script src="https://togetherjs.com/togetherjs-min.js"></script>
```
You are done. Your Website / Web Pages are ready for Co-browsing Session.

**Note:** As you see here that you are using an Open Source Library Together.JS for Co-Browsing, in case your Co-Browsing Session needs to cover specific use-case, you are free to extend EnxCoBrowse.js file we created for easy integration. You need to read through all features, support of TogetherJS to help yourself to extend.
## Enable Co-Browsing through Visual Builder (Template Editor)
Now, lets enable Co-Browsing feature in Video Embed.

- Login to the Portal and go to your Embed Project’s Dashboard through Video / Settings menu.
- Open the Video Embed dropdown, and click the Edit Template menu.
![Video Embed](./video-embed-co-browsing.png)
- You get Visual Builder to edit the Template. This UI has many tabs at the bottom.
- Go to the Feature Selection tab.
- Note that there is a Co-Browsing option. Enable it. This will help the Co-Browsing option to appear in the Video Embed.
![Edit Template](./edit-template-co-browsing.png)
- Click the Build App button to update your Video Embed.
## Add URLs for Co-Browsing
You can now add single URL or multiple URLs for Co-Browsing with Video Embed:

- Login to the Portal and go to your Embed Project’s Dashboard through Video / Settings menu.
- Open the Video Embed dropdown, and click the Co-Browsing menu.
![Video Embed](./video-embed-co-browsing.png)
- You get a Form to manage your Website URL for Co-Browsing. You need to add your URLs here with the desired Page Title.
- These are the URLs you will see in Video Embed to share with other participants for Co-Browsing.
![Manage Co-Browsing URLs](./manage-co-browsing-url.png)
- This form allows you to add maximum of 10 URLs. There is no edit option. However, you can delete the added URLs to add new ones.
- These URLs are starting points to Co-Browse that you want to share. However, once shared, you can browse through many other or all pages of your Website.
## Test your Embed for Co-Browsing
It’s time to test.

- Go to your Embed Page or open Moderator URL of your Embed.
- Get someone to join as a participant too.
- Find and click the Co-Browse option in the Toolbar. Until another participant or the moderator joins, the Co-Browse option doesn’t appear.
- You get a Co-Browse screen. It lists all the URLs you had added through the Portal Form.
- Select one URL and hit the button. This action will open a browser window / tab on your side as well as on the other side with the same URL that you shared.
- If the new browser window doesn’t open on either end, make sure that it’s not blocked by POP-UP Blocker of the browser. Disable the POP-UP Blocker if needed and share the URL again.
- Now, both end can browse the URL/Website together.
