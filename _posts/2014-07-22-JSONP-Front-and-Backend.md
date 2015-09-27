---
layout: post
title: JSONP Front & Backend
tags:
- 计算机技术
- JavaScript
- Java

---
### Single Origin Policy
It means the elements in `cs.columbia.edu` can only request resources in its domain or its sub domains, such as `clic.cs.columbia.edu`. But sometimes a web page on `clic.cs.columbia.edu` may need to request resources on `cs.mit.edu`. There are many ways to deal with this problem, but through out my internship project, I found JSONP is the most convenient way.

### How to Bypass It?
If single origin policy is really the case, why you can see an image  in a web page that may be hosted on some other server? Why can you use Google Web Fonts where the font file is hosted on Google's servers. Why can you include a url of jQuery on some CDN server? It turns out, the aforementioned resources can indeed be requested cross domain. JSONP uses this to do cross domain request.

When you make a JSONP request, the browser sees it as regular JavaScript request, only that request "script" contains the data you need. However, in order for this to work, you cannot just put your plain data (since it's not JavaScript). You need to wrap them into a JavaScript function. Thus when the requested "script" arrives at your browser, you have control over that function (data).

### How JSONP Works?
<pre class="line-numbers"><code class="language-javascript">$.ajax({
		type: "get",
		async: false,
		url: "http://localhost:1990/iWantSomeData",
		dataType: "jsonp",
		jsonp: "callback",
		jsonpCallback: "callbackFunc",
		success: function (response) {
			console.log(response);
		},
		error: function () {
			console.log("Unexpected error");
		}
	});
</code></pre>
This is a regular ajax get request. The difference is that there are `jsonp` and `jsonCallback`. I have read some tutorials, and found they abuse the term `callback`. I don't really want to explain `jsonCallback` with `callback`. In the project, I need to develop both frontend and backend. So I got a chance to see it from both sides. Line 5 is not important, you can put any word you like in the there. Line 6 is important; it is the name of the wrapper JavaScript function in which the data is stored (as mentioned above, we wrap data into a JavaScript function).

For example, if I request a JSON object through `http://localhost:1990/iWantSomeData`, the server will return
<pre><code class="language-javascript">callbackFunc({"OS":[
    {"name":"Ubuntu", "vendor":"Canonical"}, 
    {"name":"OS X", "vendor":"Apple"},
    {"name":"Windows", "vendor":"Microsoft"}
]})</code></pre>
Notice this JSON is wrapped in a JavaScript script, for the browser, it is just a regular script. On line 7, the response is the JSON object ***extracted*** from the returned "script".