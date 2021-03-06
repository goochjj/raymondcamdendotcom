{
	"title": "Query Metadata in CFMX7",
	"categories": [
		"ColdFusion"
	],
	"tags": [],
	"date": "2005-02-16T15:02:00+06:00",
	"url": "/2005/02/16/1CEE22D9-B4B6-62CD-1AC9A7C42D02ACFC",
	"oldurl": "http://www.raymondcamden.com/2005/2/16/1CEE22D9-B4B6-62CD-1AC9A7C42D02ACFC"
}

There were a few nice changes to cfqueries in CFMX7 that may have been missed by some folks. First - did you know that everytime you run a query, a variable called CFQUERY.executionTime is created? This variable contains the time the query took to execute. Also, in your query variable itself, you have more values like recordCount and columnList.

The problem with this is that you have metadata about the query in two places. Some in the query itself, some in a hard coded variable named CFQUERY. This by itself meant cfquery was partially not thread safe. 

Luckily CFMX7 solves this. It allows you to specify the name of the variable to store query metadata. (In fact, all cfml tags, except cftimer I believe, now allow you to specify a result variable.) By using result="data", you have a struct that contains the execution time, the sql (!!), column list, record count, and whether or not the query is cached.

So - this by itself is pretty useful. However, there is <i>another</i> kind of metadata you can get with a query. If you do getMetaData(queryob), you will get an array of structs. Each item in the struct is a column in your query. The order, unlike columnlist, matches the order in your original SQL. Each struct contains the name and type of the column, and if the column is case sensitive or not.