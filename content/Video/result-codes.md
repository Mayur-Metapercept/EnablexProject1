---
title: "Result Codes"
date: 
description:
type: "docs"
weight: 2
---

The Server API Response Codes are specified in the table below:

**General**
| Result Code     | Description | 
| ---- | ---- |
|   0  |   Successful Transaction  |

**Rooms**
| Result Code     | Description | 
| ---- | ---- |
|   10000  |   Application not found  |
|   10001  |   URL Parameter Missing: room_id  |
|   10002  |   Required Data Missing: name (Room Name)  |
|   10003  |   Invalid Value: settings.scheduled  |
|   10004  |   Required Data Missing: settings.scheduled_time  |
|   10005  |   Invalid Date/Time Format: settings.scheduled_time  |
|   10006  |   Illegible Date/Time: settings.scheduled_time  |
|   10007  |   Invalid Value: settings.participants  |
|   10008  |   Invalid Value: settings.auto_recording  |
|   10009  |   Unrecognized Key of settings  |
|   10010  |   Required Data Missing: owner_ref  |
|   10011  |   Invalid Value: settings.duration  |
|   10012  |   Invalid Value: settings.active_talker  |
|   10013  |   Invalid Value: settings.wait_moderator  |
|   10014  |   Invalid Value: settings.quality  |
|   10015  |   Required Data Missing: sip.uri  |
|   10016  |   Invalid Value: settings.adhoc  |
|   10017  |   Illegible Value: settings.adhoc  |
|   10018  |   Illegible Parameter. Not valid one for this Room Type  |
|   10019  |   Invalid Value: settings.mode  |
|   10020  |   Illegible Parameter: settings.mode  |
|   10021  |   Room Quality higher than App Quality not permitted  |
|   10022  |   Invalid Value: settings.moderators  |
|   10023  |   Illegible Value: settings.moderators  |
|   10024  |   Illegible value settings.peep  |
|   10025  |   Illegible value settings.knock  |
|   10026  |   Invalid SIP URI Value: settings.aor  |
|   10030  |   Denied Update request on active room  |
|   10106  |   Illegible Request. Room Type update not allowed  |
|   40001  |   Room not found  |
|   50000  |   Internal Server Error  |
|   50001  |   Failed to create Room  |
|   50002  |   Failed to fetch list of Rooms  |
|   50003  |   Failed to get Room Information  |
|   50004  |   Failed to delete Room  |
|   50005  |   Failed to delete Room  |

**Token**
| Result Code     | Description | 
| ---- | ---- |
|   10000  |   Application not found  |
|   10101  |   Required JSON Key Missing: name (User Name)  |
|   10102  |   Required JSON Key Missing: user_ref  |
|   10103  |   Required JSON Key Missing: role  |
|   10104  |   Invalid Value: role  |
|   10105  |   Server Busy  |
|   10111  |   Token denied. Conference is over  |
|   10112  |   Token denied. Beyond Permissible Cut-Off Time  |
|   10113  |   Token denied. Room is not active  |
|   10114  |   Token denied. Room is full  |
|   40001  |   Room not found  |
|   40002  |   Token denied. Unauthorized  |

**CDR**
| Result Code     | Description | 
| ---- | ---- |
|   10201  |   Reason URL Parameter Missing: conf-num (Conference Number)  |
|   10202  |   URL Parameter Missing: room-id  |
|   10203  |   URL Parameter Missing: to_date  |
|   10204  |   URL Parameter Missing: room-id  |
|   10205  |   Reason URL Parameter Missing: conf-num (Conference Number)  |