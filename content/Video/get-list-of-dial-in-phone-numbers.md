---
title: "Get List of Dial In Phone Numbers"
date: 
description:
type: "docs"
weight: 2
---
This API Route gives you a list of Dial-In phone numbers configured with your Account and SIP Service Configuration infomration.

- **Availability**: v1.5.3+
- [**API Route**] (https://api.enablex.io/video/v2/dialin/)
- **HTTP**: GET

**Sample Request**
```
GET https://api.enablex.io/video/v2/dialin/  
Authorization: Basic XXXXXXX
```

**Response JSON**
```
{               
	“_id”: “Object ID”, 
	“app_key”: “XOXO”, 
	“settings”: {                                      
		“sip”: true
	}, 
	“sip”: {
		“server_url”: “sip://xoxo:PORT”, 
		“username”: “String”, 
		“password”: “String”, 
		“sig_servers”: [“String”],	/* Multiple Signal Server IP/URL */ 
		“media_servers”: [“String”]	/* Multiple Media Server IP/URL */ 
	}, 
	“dialin”: [				/* Array of Phone Numbers */
		{ 
			“country”: “String”, 
			“country_code”: “String”, 
			“phone”: "String"
			“toll”: false		/* false = Tollfree */ 
		}
	}
}
```