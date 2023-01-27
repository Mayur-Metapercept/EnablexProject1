---
title: "API Responses"
date: 
description:
type: "docs"
weight: 2
---
The Server API call  make use of  JSON Result Code to determine if the API call is successful.

**Success JSON**

Successful Server API calls will always return JSON with a 0 (zero) Result Code.

```
{    
     "result": 0,    
     ….
     ….
 }
```
**Error JSON**
If unsuccessful, for whatever reason, the Server API will return a JSON with a non—zero result code. An error response in JSON will always carry 3 keys, viz. Result Code, Error, Description. See example below:
```
{    
     "result": "Non-Zero Result Code",   
     "error": "Short reason",
     "desc": "Descriptive information about the error / warning"
 }
```