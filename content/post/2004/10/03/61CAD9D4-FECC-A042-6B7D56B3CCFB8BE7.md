{
	"title": "Reminder about Roles in CFFUNCTION",
	"categories": [
		"ColdFusion"
	],
	"tags": [],
	"date": "2004-10-03T20:10:00+06:00",
	"url": "/2004/10/03/61CAD9D4-FECC-A042-6B7D56B3CCFB8BE7",
	"oldurl": "http://www.raymondcamden.com/2004/1/3/61CAD9D4-FECC-A042-6B7D56B3CCFB8BE7"
}

So for some reason, I could have sworn the ROLES attribute of CFFUNCTION was an "and" list, by that I mean any role specified would be required. I just read on cf-talk that this is not the case and I have confirmed it. I'll be updating Galleon soon and will remove my workarounds to support checking for a role in a list of roles. (Only a few methods did this, but any unnecessary code is code that should be yanked!)