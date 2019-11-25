---
layout: post
title:      "Event Delegation in JavaScript"
date:       2019-11-25 06:06:55 +0000
permalink:  event_delegation_in_javascript
---


Event delegation allows attaching an event listener to a parent node/element, rather than directly to the element itself.
<br/>
<br/>
To understand event delegation, we first need to know what event bubbling is.  Event bubbling is the process where an event (a mouse click, for example) "bubbles" up through all its parent elements, or nodes.  This is also event propagation, when the event (click) propagates up the DOM, and can be "heard" by all its parent elements.  You can "listen" for the event by setting an event listener.  An event listener is when we listen for actions that happen on an elements, in order to then execute a function.  The event itself contains information about what happened (like what element/node was clicked).
<br/>
For example:
<br/>
```
const parentNode = document.getElementByID("parentIdName")
parentNode.addEventListener( "click", () => { doSomething(event) } )

function doSomething(event) {
 if (event.target && event.target.nodeName === "desiredNodeName") {
  // do something here
	}
 }
```
<br/>
For the record, don't get confused between `event.target` and `event.currentTarget`:
* **event.target** is the element you are listening *for* (i.e. the child node)
* **event.currentTarget** is the element that the event listener is *attached* to (i.e. the parent node)

<br/>
But what if the element(s) you want to listen to don't exist when the page is loaded?  For instance, on a list whose items are added dynamically by the user.  You can't attach an event listener to them if they don't exist when the page is loaded.
<br/>
<br/>
Another example is when you have list items that may need to change frequently by you or another developer.  Imagine the extra workload that's needed if you have to add or update an event listener every time you add or change an element.  This is where event delegation saves time.
<br/>
<br/>
**Event delegation** is the process by which you can attach the event listeners to the parent elements, and when the event happens on the child element (the item is clicked), it "bubbles" up the DOM, the event listener on the parent "hears" it and checks which event happened to see if it matches what it was listening for.  If there is a match, it executes.
<br/>
<br/>
<br/>
Something else worth mentioning because it's related to bubbling, or propagation, is to be aware of the differences between `event.preventDefault()` and `event.stopPropagation()`:
* **preventDefault()** prevents the default action from happening when the event is triggered, but the triggered event is still propagated, or bubbled up the DOM to be heard by all the parent elements.


* **stopPropagation()** allows the default action from happening when the event is triggered, but the triggered event is NOT propagated, or bubbled up the DOM and therefore will NOT be heard by parent elements.

The reason that this is important is because stopPropagation() is likely to have negative and unexpected effects on your program, like plugins not working or impacts in other areas of your application.
<br/>
It's very likely that you'll mostly only need to use preventDefault(), so use the other with caution.
<br/>
<br/>
<br/>
Additional resources:
* [How JavaScript Event Delegation Works](https://davidwalsh.name/event-delegate)
* [Bubbling and Capturing, javascript.info](https://javascript.info/bubbling-and-capturing)
* [What is Event Delegation in JavaScript?](https://medium.com/@bretdoucette/part-4-what-is-event-delegation-in-javascript-f5c8c0de2983)

<br/>
