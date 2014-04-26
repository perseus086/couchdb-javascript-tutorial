Couchdb-javascript-tutorial
===========================

A little tutorial, if you want to access to couchdb directly from Javascript. 

#Tutorial couchdb with javascript

##1. Enable CORS

You need to have access to the file: **local.ini**.

We need to activate CORS functionality. Check [this](http://wiki.apache.org/couchdb/CORS) page for more info

For that use this code:
<code>
couchdb -c
</code>


It should appear:
<pre>
/usr/local/etc/couchdb/default.ini
/usr/local/etc/couchdb/local.ini
</pre>

If you don't get that please install couchdb using homebrew.

<code>brew install couchdb</code>

Open the **local.ini** file and edit it with whatever you like, in this case I will use on mac the texteditor that everybody has by default.

Open the terminal:

<code> cd /usr/local/etc/couchdb </code>

Then,
<code> open -a TextEdit local.ini</code>

below **\[httpd]** add enable_cors = true

<pre>[httpd]
enable_cors = true</pre>


And at the end of the file add: <pre>[cors]
origins = *</pre>.



##2. JAVASCRIPT CODE

In the terminal run <code>couchdb</code>

Go tho this pages:

<code> http://localhost:5984/_utils/script/jquery.js</code>
<code> http://localhost:5984/_utils/script/jquery.couch.js </code>

You will notice that there is javascript code. We will use this files for our html website.

Now try this:

```html
<html>
	<head>
		<title>OPTIONS</title>
	</head>
	<body>
	</body>

<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<script src="http://localhost:5984/_utils/script/jquery.js"></script>
<script src="http://localhost:5984/_utils/script/jquery.couch.js"></script>
<script>
	$.couch.urlPrefix = "http://localhost:5984";
    $.couch.allDbs({
    success: function(data) {
        console.log(data)
    }
});

  </script>

</html>
```


Check your console you should see the databases that you have in an array.