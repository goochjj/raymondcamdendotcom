{
	"title": "CFC Blackstone Update",
	"categories": [
		"ColdFusion"
	],
	"tags": [],
	"date": "2004-11-08T08:11:00+06:00",
	"url": "/2004/11/08/190599E2-AFEB-E2AB-EE9DD515EC0EE00D",
	"oldurl": "http://www.raymondcamden.com/2004/11/8/190599E2-AFEB-E2AB-EE9DD515EC0EE00D"
}

So, first, let me make it clear I got permission from MACR to state this. I wanted to get this out at the Birds of a Feather but I forgot to ask in time.

Two nice bugs related to CFCs are fixed in Blackstone:

1) Right now if you duplicate or WDDX a CFC, you get... something. What you get, however, is not really a CFC (or serialized CFC). This can definitely lead to confusion on the developer's part. In Blackstone, you now get an error when you duplicate/WDDX a CFC. While it would be nice if these functions actually worked, I'm very happy MACR made the functions throw an error. Also note that you can very easily add a duplicate/serialize/deserialize method to your CFCs.

2) There is a bug in CFMX 6.1 with CFCs and cfinclude. If you cfinclude your method code, all variables that <i>were</i> var scoped are copied to the Variables scope. Obviously this kinda sucks. Right now you can avoid this by not using cfinclude. If your method code is so long that it is hard to parse within the rest of the CFC, it may be time for refactoring. The good news, though , is that this is fixed in Blackstone.