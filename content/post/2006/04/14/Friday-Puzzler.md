{
	"title": "Friday Puzzler",
	"categories": [
		"ColdFusion"
	],
	"tags": [],
	"date": "2006-04-14T08:04:00+06:00",
	"url": "/2006/04/14/Friday-Puzzler",
	"guid": "1213"
}

I thought the last puzzler was kind of fun, so I figured why not do it again. I'm not around much today to comment on the entries, but if you are bored, here is a small coding challenge: Madlibs. Your code will take a hard coded string like so:

<blockquote>
Four score and {number} years ago,<br/>
Star Wars was a {adjective} movie.<br/>
I saw it with two hundred {plural noun}.<br/>
I need a new {noun} like I need a new {noun} in my head.
</blockquote>

It will look for any tokens inside { } characters, and create a simple form where the value inside the {} token is the label for the text field. In other words, the string above would have made a form with three text fields, labelled number, adjective, and plural noun. When the user hits submit, the values for each form field will replace the tokens in the original string.

Nice and simple, right? Don't even bother with validation. Just parse the string, create the form, and then display the madlib based on the user's input.

As a reminder, this is <i>not</i> a contest. There are no prizes. If you spend more than five minutes on it, walk away from your computer. Enjoy.