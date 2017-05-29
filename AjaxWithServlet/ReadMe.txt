AJAX stands for Asynchronous JavaScript and XML. AJAX is a technique for creating better, faster, and more interactive web applications with the help of XML, HTML, CSS, and Java Script.

⦁	A client event occurs.
⦁	An XMLHttpRequest object is created.
⦁	The XMLHttpRequest object is configured.
⦁	The XMLHttpRequest object makes an asynchronous request to the Webserver.
⦁	The Webserver returns the result containing XML document.
⦁	The XMLHttpRequest object calls the callback() function and processes the result.
⦁	The HTML DOM is updated.

The XMLHttpRequest object is the key to AJAX. XMLHttpRequest (XHR) is an API that can be used by JavaScript, JScript, VBScript, and other web browser scripting languages to transfer and manipulate XML data to and from a webserver using HTTP, establishing an independent connection channel between a webpage's Client-Side and Server-Side.The data returned from XMLHttpRequest calls will often be provided by back-end databases. 
XMLHttpRequest can be used to fetch data in following formats:
⦁	XML
⦁	JSON
⦁	Plain Text

Listed below is listed are some of the methods and properties of XMLHttpRequest object that you have to get familiar with.
XMLHttpRequest  Methods:
⦁	abort(): Cancels the current request.
⦁	getAllResponseHeaders(): Returns the complete set of HTTP headers as a string.
⦁	getResponseHeader( headerName ):Returns the value of the specified HTTP header.
⦁	open( method, URL )
⦁	open( method, URL, async )
⦁	open( method, URL, async, userName )
⦁	open( method, URL, async, userName, password )

Specifies the method, URL, and other optional attributes of a request.

The method parameter can have a value of "GET", "POST", or "HEAD". Other HTTP methods, such as "PUT" and "DELETE" (primarily used in REST applications) may be possible.

The "async" parameter specifies whether the request should be handled asynchronously or not. "true" means that the script processing carries on after the send() method without waiting for a response, and "false" means that the script waits for a response before continuing script processing.

send( content )
Sends the request.

setRequestHeader( label, value )

Adds a label/value pair to the HTTP header to be sent.

XMLHttpRequest Properties:
⦁	onreadystatechange: An event handler for an event that fires at every state change.
⦁	readyState: The readyState property defines the current state of the XMLHttpRequest object.
The following table provides a list of the possible values for the readyState property:

State	Description
0	The request is not initialized.
1	The request has been set up.
2	The request has been sent.
3	The request is in process.
4	The request is completed.

readyState = 0 After you have created the XMLHttpRequest object, but before you have called the open() method.

readyState = 1 After you have called the open() method, but before you have called send().

readyState = 2 After you have called send().

readyState = 3 After the browser has established a communication with the server, but before the server has completed the response.

readyState = 4 After the request has been completed, and the response data has been completely received from the server.

⦁	responseText: Returns the response as a string.
⦁	responseXML: Returns the response as XML. This property returns an XML document object, which can be examined and parsed using the W3C DOM node tree methods and properties.
⦁	status: Returns the status as a number (e.g., 404 for "Not Found" and 200 for "OK").
⦁	statusText: Returns the status as a string (e.g., "Not Found" or "OK").


Ajax code:

	function ajaxCall() {
		var xhttp = new XMLHttpRequest();
		xhttp.onreadystatechange = function() {
			if (this.readyState == 4 && this.status == 200) {
				document.getElementById("para").innerHTML 				= this.responseText;
			}
		};
		xhttp.open("GET", "ajaxCall", true);
		xhttp.send();

	}

note:ajaxCall is the name of the servlet we are calling
There are other ways of creating XHR object. These ways are specific to certain browsers. Following are those:


⦁	Modern Browsers create XHR object as follows:
	
	var xhttp = new XMLHttpRequest();

⦁	IE5 and IE6 Browsers do not support XHR object directly. They use ActiveXObject for that purpose.
	
	var xhttp = new ActiveXObject("Microsoft.XMLHTTP");


Breaking down Method:
⦁	We create XHR object
⦁	NOw we create callback function on event onreadystatechange, which will get triggered evertime readystate changes
⦁	when readystate=4 and statu=200 ,i.e. everytuhng is ok, we will fetch the response as responseText (for String or JSON) Or responseXML(for XML).
⦁	outside call back we do xhttp.open(method,fileToCall,asyncOrNot).
⦁	Method can be Get or Post.
⦁	fileToCall will be a text file on local machine or a page. In this case its a servlet.
⦁	asyncOrNot can be true or false.For true the call will not block other operation of page. If false then untill and unless server responds and we get a readyStat 4 and status 200 control will not move forward and page might hang. So if ajax request is very light then its ok to put this as false else always true. After all, its Ajax(Asychronous... ).

⦁	At last we send the request.


Sending Data from Ajax:
In above example we just made a simple ajax call to servlet with a response. WHen we want to send some data also we do following:

⦁	For Get request:

xhttp.open("GET", "demo_get2.asp?fname=Henry&lname=Ford", true);
xhttp.send();

Here we sent fname and lname data to servlet.
⦁	For Post request:

xhttp.open("POST", "ajax_test.asp", true);
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
xhttp.send("fname=Henry&lname=Ford");

So as post should not send data as query parameter because of security issues, we add an HTTP header with setRequestHeader() and then sends the data along with send method.

setRequestHeader(header, value): Adds HTTP headers to the request
header: specifies the header name
value: specifies the header value

















