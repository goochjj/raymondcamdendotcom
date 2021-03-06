+++
title = "Contact Me"
+++

Have a question you want answered? Is there something you would like me to write about on the blog? Just use the form below to reach out to me. I can’t promise I will respond to every question, but I will try to either respond or post an entry to the blog relating to your inquiry.

If you are asking about a particular blog entry, *please* share the URL of the entry you are asking about.
Also note that I do *not* accept guest blog entries or paid blog entries.

Also note that I speak English, and just English. I know a few words of Spanish and French, but I don't *really* speak it. Please do not email me in a foreign (to me) language as I will not be able to help you.

Another note - I cannot (and will not!) provide support for ColdFusion UI controls like cfgrid, cfinput, etc. I've discussed why multiple times and have even provided [direction](https://github.com/cfjedimaster/ColdFusion-UI-the-Right-Way) about how to move away from them.

Finally - I do not accept paid article submissions or infographics.

<script>
document.addEventListener("DOMContentLoaded", function() {

	var $sub = $("#_subject");
	$("#email").on("input", function() {
		$sub.val("Blog Contact Form (" + $(this).val() + ")");
	});
	
}, false);
</script>

<form action="//formspree.io/raymondcamden@gmail.com" method="POST" id="contactform">
	<input type="hidden" name="_next" value="{{% siteurl %}}/thankyou">
	<input type="hidden" name="_subject" id="_subject" value="Blog Contact Form">
	<input type="hidden" name="_format" value="plain">
	
	<input type="text" name="_gotcha" style="display:none" />
	
	<label for="contact_name">Name: </label>
	<input type="text" name="name" id="contact_name" required><br/>
	
	<label for="email">Email: </label>
	<input type="email" name="_replyto" id="email" required><br/>
	
	<label for="contact_comments">Comments: </label><br/>
	<textarea name="comments" id="contact_comments" required></textarea><br/>
	<input type="submit" value="Send" id="contactSubmit">
</form>