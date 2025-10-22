HyperText Transfer Protocol is what's used when viewing a website.
HTTP is the set of rules for communicating with web servers for the transmitting of webpage data.

HTTPS (HyperText Transfer Protocol Secure) is the secure version of HTTP.
HTTPS data is encrypted, unlike regular HTTP.

#### Requests and Responses

When accessing a website our browser needs to make requests to a web server for assets such as HTML, Images and download the responses.
Before that we need to tell the browser specifically how and where to access these resources using URLs.

Uniform Resource Located (URL) is an instruction on how to access a resource.
The following example consists of a URL - `http://user:password@example:80/view-room?id=1#task3`.

* Scheme instructs on what protocol to use for accessing the resource such as HTTP, HTTPS, FTP (File Transfer Protocol).
* User requires authentication to log in, we can put a username and password into the URL to log in.
* Host is the domain name or IP address of the server.
* Port is where exactly we're connecting to, usually 80 for HTTP and 443 for HTTPS but this could be hosted on any port between 1-65535.
* Path is the file name or location of the resource we're trying to access.
* Query String is extra bits of information that can be sent to the requested path.
* Fragment is a reference to a location on the actual page requested, this is commonly used for pages with long content and can have a certain part of the page directly linked to it.

Making a request is possible to a server with just one line - `GET /HTTP/1.1`.
Usually more data is sent using headers, an example of a header:

``` http
GET / HTTP/1.1

Host: example.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://example.com/
```

Line 1 is the request sending the `GET` method, request the home page with / and telling the web server we are using HTTP protocol version 1.1.
Line 2 we tell the web server we want the website `example.com`.
Line 3 we tell the web server we are using the Firefox version 87 Browser.
Line 4 we are telling the web server that the web page that referred us to this one is https://example.com
Line 5 HTTP requests always end with a blank line to inform the web server that the request has finished.

An example response:

```http
HTTP/1.1 200 OK

Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
	<title>Example</title>
</head>
<body>
	Welcome to Example.com
</body>
</html>
```

Line 1 `HTTP 1.1` is the version of the HTTP protocol the server is using and then followed by the HTTP Status Code (`200 OK`) which tells us the request has completed successfully.
Line 2 tells us the web server software and version number.
Line 3 tells us the current date, time and timezone of the web server.
Line 4 tells us the Content-Type header which tells the client what sort of information is going to be sent such as HTML, images, videos etc..
Line 5 tells us the Content-Length header which tells the client how long the response is, this we we can confirm no data is missing.
Line 6 HTTP response contains a blank line to confirm the end of the HTTP response.
Lines 7-14 is the information that has been requested.

#### HTTP Methods

HTTP methods are a way for the client to show their intended action when making an HTTP request.

* GET Request - this is used for getting information from a web server.
* POST Request - this is used for submitting data to the web server and potentially creating new records.
* PUT Request - this is used for submitting data to a web server to update information.
* DELETE Request - this is used for deleting information/records from a web server.

#### HTTP Status Codes

| **100-199 - Information Response** | These are sent to tell the client the first part of their request has been accepted and they should continue sending the rest of their request. These codes are no longer very common. |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **200-299 - Success**              | This range of status codes is used to tell the client their request was successful.                                                                                                    |
| **300-399 - Redirection**          | These are used to redirect the client's request to another resource. This can be either to a different webpage or a different website altogether.                                      |
| **400-499 - Client Errors**        | Used to inform the client that there was an error with their request.                                                                                                                  |
| **500-599 - Server Errors**        | This is reserved for errors happening on the server-side and usually indicate quite a major problem with the server handling the request.                                              |