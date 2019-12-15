---
layout: post
title:      "Smooooth Scrolling SPA"
date:       2019-12-15 21:50:54 +0000
permalink:  smooooth_scrolling_spa
---


SPA's (or Single Page Apps) are exactly as the name implies.  Instead of serving multiple pages for different content, like index, about, contact, portfolio for example, an SPA only serves the index.html page.  Within this one page can be different content, so when the user clicks a link in the nav bar at the top of the page, the link scrolls to the target anchor point on the page where that content lives.
<br/>
<br/>
Normally, clicking that link would cause a sudden, jerking movement to the requested anchor point on the page.  But users expect a better quality experience from websites today, so this just wouldn't be okay.  Instead, try using a smooth scroll to your anchor point.
<br/>
<br/>
Smooth scrolling can be accomplished several ways, like if you want to set smooth scrolling for your whole site, just add this to your CSS file:
```
html {
  scroll-behavior: smooth;
}
```
<br/>
In React, you can add the [react-scroll](https://www.npmjs.com/package/react-scroll) package to your project and set the `smooth` attribute of your `<Link>` to `true`.  You can also set additional attributes like `duration`, which controls how long it takes to scroll to the anchor point, and `offset` which is like padding and allows you to scroll additional px (like to accommodate a fixed nav bar height).
<br/>
<br/>
While smooth scrolling is almost an expected behavior by users for some sites, it also comes with a couple downsides, too.  For instance, if your user is navigating quickly between points on your site, a slow scroll can become frustrating.  Another issue can be accessibility.  You'll need to accommodate for users that rely completely on a keyboard to navigate your site.  So, when this user follows a link, the keyboard focus should follow it.
<br/>
<br/>
There's also the normal browser behavior that should be maintained, like being able to go back using the browser back button, or being able to copy/paste a URL and having the browser navigate to the last specific location.  There is a great post on CSS-Tricks (link below) that walks through these issues and provides some demos.
<br/>
<br/>
<br/>
Additional references:
<br/>
<br/>
[Smooth Scrolling and Accessibility on CSS-Tricks](https://css-tricks.com/smooth-scrolling-accessibility/)
<br/>
[React-scroll on npm](https://www.npmjs.com/package/react-scroll)
<br/>
[Scroll-behavior on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/scroll-behavior)
