{
	"title": "CFMX Admin Password Issue",
	"categories": [
		"ColdFusion"
	],
	"tags": [],
	"date": "2004-09-07T14:09:00+06:00",
	"url": "/2004/09/07/DA8E1E2D-C987-50E9-46DDFBCFC6FAB0B1",
	"oldurl": "http://www.raymondcamden.com/2004/9/7/DA8E1E2D-C987-50E9-46DDFBCFC6FAB0B1"
}

Anyone seen this before? Whenever I try to turn on the "Use Admin Password" for CFMX, it gives me an Unable to set admin password error. This page refreshes and I'm brought to a screen where I need to enter the password. The password doesn't work. (No surprise there.) When I examine the neo-security.xml file, I see that admin.security.enabled is still false. Restarting CF makes the error go away... but there is no password protection for the server. 

I googled, and all I could find was a mention of ZoneAlarm in a <a href="http://www.houseoffusion.com/cf_lists/index.cfm/method=messages&threadid=20702&forumid=4">cf-talk thread</a>. Anyone else encounter this?