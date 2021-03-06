{
	"title": "Important Note for ColdFusion 8 Ajax Developers",
	"categories": [
		"ColdFusion",
		"jQuery"
	],
	"tags": [],
	"date": "2009-04-20T22:04:00+06:00",
	"url": "/2009/04/20/Important-Note-for-ColdFusion-8-Ajax-Developers",
	"guid": "3323"
}

Credit for this article goes to a discovery by <a href="http://www.raymondcamden.com/index.cfm/2008/2/27/Can-you-do-file-uploads-with-ColdFusion-8s-Ajax-features#cAABFE754-91DF-1F43-6FD5FB1D947239F6">Martin Franklin</a>. Thanks to a comment from him, I discovered something that may be of major importance to folks doing Ajax development on ColdFusion 8 boxes. If you do any work on a ColdFusion 8 box and do not have control over the Administrator settings, beware of the Secure Prefix setting.
<!--more-->
About two years ago I <a href="http://www.coldfusionjedi.com/index.cfm/2007/7/31/ColdFusion-8-Ajax-Security-Features">blogged</a> about ColdFusion 8 security features. One of them is JSON Prefixes. This is the ability to prefix all JSON results (generated by CFC, returnFormat=json) with a prefix. What's cool about this feature is that all the front end stuff ColdFusion uses will recognize this setting and automatically strip the prefix before processing the result.

What <i>isn't</i> so cool about this feature is that if you aren't using ColdFusion 8's front end AJAX stuff, then this can really trip you up. Imagine you've done all your work locally before pushing the code up to a shared host. All of a sudden your code stops working. It may be a good idea to pop open Firebug and look for something in front (like the default prefix, //) of the JSON response.

Here is a simple example:

<code>
&lt;html&gt;

&lt;head&gt;
&lt;script src="jquery/jquery.js"&gt;&lt;/script&gt;
&lt;script&gt;
$(document).ready(function() {
		
	$("#submitBtn").click(function() {
		var value = $("#number").val()
		$.getJSON("test.cfc?method=double&returnFormat=json",{number:value},function(d) {
			console.log(d)
		})
	})
	
})
&lt;/script&gt;
&lt;/head&gt;

&lt;body&gt;

&lt;input type="text" id="number"&gt; &lt;input type="submit" id="submitBtn" value="Double"&gt;	
		
&lt;/body&gt;
&lt;/html&gt;
</code>

Nothing too complex here. I've got a form with one input. When you hit the button, I run an AJAX request to a CFC method that will double the response. The CFC method is just:

<code>
&lt;cffunction name="double" access="remote" returnType="any" output="false"&gt;
	&lt;cfargument name="number" required="true" type="any"&gt;
	&lt;cfif isNumeric(arguments.number)&gt;
		&lt;cfreturn 2*arguments.number&gt;
	&lt;cfelse&gt;
		&lt;cfreturn 0&gt;
	&lt;/cfif&gt;
&lt;/cffunction&gt;
</code>

If you run the code (wrap the cffunction with a CFC of course) it should work just fine. Now go to your ColdFusion Admin, Settings page, and enable the Prefix:

<img src="https://static.raymondcamden.com/images/cfjedi//Picture 49.png">

Rerun your code and you will see... nothing. (To be clear, my code did nothing visual with the response except to log it to Firebug, so even before you 'saw' nothing unless you had Firebug open.) I modified my JavaScript a bit to add a global error handler (first time trying this, pretty impressed by how easy it was):

<code>
$.ajaxSetup({
	error:function(req,textstatus,errorThrown) {
		console.log(textstatus)
	}
})
</code>

Running the page again, I now saw this in the console: parseerror. 

Luckily there is a simple fix. You can override the setting (don't forget it can be set in the Application.cfc file as well) by adding the secureJson attribute to the function:

<code>
&lt;cffunction name="double" access="remote" returnType="any" output="false" secureJSON="false"&gt;
</code>

This correctly disabled the prefix and my code worked fine again.

<b>Definitely</b> keep this in mind if you are deploying to machines you don't have 100% control over, or, if things seem to break down when you deploy. (Of course, the first thing to check is for the onRequest method in an Application.cfc file. <i>Sure</i> hope Adobe fixes that in CF9.)