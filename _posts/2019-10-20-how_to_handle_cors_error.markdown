---
layout: post
title:      "How to Handle CORS Error"
date:       2019-10-21 02:29:19 +0000
permalink:  how_to_handle_cors_error
---


CORS stands for Cross Origin Resource Sharing.  You probably already know about CORS and have very likely run into some issues because of it.  Browsers have a security step built in to prevent *cross-site request forgery*, which is when malicious sites 'hijack' a browser's cookies to access the secure site those cookies belong to.
<br/>
<br/>
A simple example would be if you use your username and password to sign into a secure site, like Facebook for instance.  After authentication, Facebook would then store a session cookie in your browser.  This cookie is how you can navigate from page to page within Facebook and not have to provide your username and password every time you open a new page.
<br/>
<br/>
Remember, HTTP is a stateless protocol, which means that the connection between the browser and the server is lost once the transaction ends, so it doesn't remember that you signed in to Facebook already.  The cookies that are stored in your browser are what tell Facebook that you are signed in.
<br/>
<br/>
The problem that can happen is when a malicious site gains access to those session cookies and then tries to access Facebook with them (pretending to be you).  During a normal request/response interaction between the browser and the server, the browser includes *origin* information in the server request that includes the protocol, domain and port that are being used during that request.  The server then includes this *origin* information in it's response to the browser, and the browser checks that the *origin* information matches.
<br/>
<br/>
So where CORS comes into the picture is when the browser detects that the origins of the server and web application don't match, like when a malicious site is sending a request to the server with your 'hijacked' cookies.  When this happens, the browser will block the request, issuing a CORS error.
<br/>
<br/>
<br/>
As front end developers, we're likely to run into CORS errors while develping applications that access web APIs.  During development and testing, our browser is sending requests to, and receiving responses from, our local server.  But our application is also sending a request to a web API for information that will be used in our application.  This triggers the Cross Origin Resource Sharing error.
<br/>
<br/>
<br/>
Here's how you can get around the issue, during development, and then during production:
<br/>
<br/>
**During development**, you can install a Chrome extension that will allow you to turn off/on CORS security checks in the browser.  The name of the extension is [Moesif Origins & CORS Changer](https://chrome.google.com/webstore/detail/moesif-orign-cors-changer/digfbfaphojjndkpccljibejjbppifbc?hl=en-US).  This extension has worked for me, allowing me to test my application without any CORS errors.  It's also safe, since I am in control of turning it on and off as needed (just remember to turn it off when you don't need it!)
<br/>
<br/>
Now, while this works great during development and testing, on my machine, it's not going to work in production bacause users of your application probably don't have the Moesif extension installed, and even if they did you wouldn't want to ask them to turn it on!  Why should they trust *you*?
<br/>
<br/>
**During production**, you can use a proxy server to send the requests to your web API.  If you were really listening *closely* ealier, you may have noticed that the CORS issue is concerned with browser-to-server requests/responses.  So, if you use a proxy *server*, you can avoid the CORS issue altogether, because the requests/responses are now *server-to-server*.
<br/>
<br/>
There is a Heroku app that is available to use for this, and it worked well for me.  It's `https://cors-anywhere.herokuapp.com`.  The way to utilize this method is to prepend the URL in your `Fetch` (or `XMLHttpRequest`) call with this proxy url.  So, for example, a Fetch API call to:
<br/>
<br/>
`https://your-web-api.com/info`
<br/>
<br/>
would be replaced with:
<br/>
<br/>
`https://cors-anywhere.herokuapp.com/https://your-web-api.com/info`
<br/>
<br/>
<br/>
The first time I tried these two methods, I installed the Moesif extension and tried it first (and it worked).  Then I turned off the extension and tried the method of prepending the cors-anywhere.herokuapp, which also worked just fine.
<br/>
<br/>
An **important note** about these methods, is that they both essentially turn off CORS checking in the browser, which isn't safe for all situations, so be mindful.  If you need them, there are additional resources out there on how to create your own proxy to use with your application, thus eliminating the need to use the cors-anywhere approach in production.
<br/>
<br/>
If you are having CORS errors, I would absolutely recomment reading up on it, how it works, and where to look in your browser console (*hint*: the Network tab) to see the details of the requests and responses between the browser and server.  It'll help you understand what specifically is causing the browser to block requests and therefore what to 'google' to find the answer.  And MDN is a good place to start...
<br/>
<br/>
<br/>
<br/>
![Cookie Monster!](https://media.giphy.com/media/xT0xeMA62E1XIlup68/giphy.gif)
