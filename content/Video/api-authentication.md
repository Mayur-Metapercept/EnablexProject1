---
title: "API Authentication"
date: 
description:
type: "docs"
weight: 2
---

The Server API uses HTTP Basic Authentication mechanism to authenticate API calls. Each API call is validated via the authentication header.

The following Information is used as credentials to access Server API for your Application in the HTTP basic authentication header in the API call request:

- **Application ID** or **APP_ID** as username
- **Application Key** or **APP_KEY** as Password

```
POST https://api.enablex.io/video/v2/rooms/
Authorization: Basic XXXXXX    
Content-Type: application/json
```
The *Authorization* header in the above example contains a value XXXXX which is a base64 encoded string of the **APP_ID:APP_KEY**.

**How to get APP_ID and APP_KEY?**

All API Credentials are paired to a Project. You will need to create a Project first to receive the API credentials. To create Project, follow the given steps:
- Login to EnableX Portal
- **Navigate**: {Main Menu} Projects / Create New Project

Once your Project is created, you will receive an email with the Project’s Access Credentials, that is **APP_ID** and **APP_KEY**.
