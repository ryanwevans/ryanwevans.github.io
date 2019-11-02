---
layout: post
title:      "The Geolocation API"
date:       2019-11-02 19:28:33 -0400
permalink:  the_geolocation_api
---


The Geolocation API allows the user to provide their location to an application if they wish to.  The Geolocation API is provided through the `navigator.geolocation` object.  If the `navigator.geolocation` object exists, then Geolocation services are available.  Here's a simple example to test if geolocation services are available, provided by [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API):
```
if ("geolocation" in navigator) {
  /* geolocation is available */
} else {
  /* geolocation IS NOT available */
}
```

<br/>
The Geolocation object has three useful methods:
<br/>
* `getCurrentPosition()` - does exactly as the name implies, getting the current position
* `watchPosition()` - does what the name implies as well, continually tracking position
* `clearWatch()` - terminates the continuous tracking started by `watchPosition()`

<br/>
`getCurrentPosition()` and `watchPosition()` require a callback function to handle the `Position` object it receives upon a succesful location request.  They both also have an optional second parameter for a callback function to handle the `PositionError` object if the request fails.
<br/>
<br/>
The `clearWatch()` method takes one parameter, which is the `watchID` , an ID number that was returned from the `watchPosition()` method.
<br/>
<br/>
Here's an example of usage from [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API) that only handles a successful request:
```
navigator.geolocation.getCurrentPosition(function(position) {
  do_something(position.coords.latitude, position.coords.longitude);
});
```
<br/>
This example from [Crate.io](https://crate.io/a/geolocation-101-get-users-location/) checks that the browser supports geolocation, and then calls the `getCurrentPosition()` method which either passes a Position object to the  `onGeolocateSuccess()` callback function, or the PositionError object to the `onGeolocateError()` callback function:
```
function geolocate() {
  if (window.navigator && window.navigator.geolocation) {
    navigator.geolocation.getCurrentPosition(onGeolocateSuccess, onGeolocateError);
  }
}
```
<br/>
The `getCurrentPosition()` and `watchPosition()` methods will also take an additional third `PositionOptions` object with three properties (it doesn't inherit any properties):
<br/>
* `enableHighAccuracy`  - a boolean which is set to `false` by default in order to load faster (and use less power), if `true` the device will provide more accurate position information if it can
* `timeOut` - which is the maximum amount of time (in ms) that the device can take to return the position (the default is infinity)
* `maximumAge` - which is how old a cached position can be (the default is 0, meaning that the device isn't allowed to use a cached position)

<br/>
Remember that using the Geolocation API will prompt users to either 'block' or 'allow' geolocation services being shared with your application.  It is also only available in a secure context requiring an `https` connection.
<br/>
<br/>
*Resources:*
* [Geolocation API on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation_API)
* [Geolocation 101 - How To Get A User's Location (Crate.io)](https://crate.io/a/geolocation-101-get-users-location/)
* [getCurrentPosition() on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/getCurrentPosition)
* [watchPosition() on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/watchPosition)
* [clearWatch() on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Geolocation/clearWatch)
* [PositionOptions on MDN](https://developer.mozilla.org/en-US/docs/Web/API/PositionOptions)
* [Geolocation API from Google](https://developers.google.com/maps/documentation/geolocation/intro)

<br/>
