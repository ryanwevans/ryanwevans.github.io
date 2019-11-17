---
layout: post
title:      "Progressive Web Apps"
date:       2019-11-17 01:04:04 +0000
permalink:  progressive_web_apps
---


What makes a web app, a Progressive Web App?
<br/>
<br/>
"Progressive Web Apps provide an installable, app-like experience on desktop and mobile that are built and delivered directly via the web. They're web apps that are fast and reliable. And most importantly, they're web apps that work in any browser." - [Google Codelabs](https://codelabs.developers.google.com/codelabs/your-first-pwapp/index.html?index=..%2F..index#0)
<br/>
<br/>
Progressive Web Apps have specific attributes:
* **Fast** - it should load visible content to the page quickly, as quickly as if you were opening a native app on your device.
* **Reliable** - it shouldn't vary in load time or responsiveness.
* **Responsive** - it should work on both mobile and desktop platforms with a single codebase (so if you're considering building a native application, you should strongly consider building a PWA instead).
* **Installable** - a user should have the option to install the app, without using an app store, and have the same user experience as an installed app, regardless of network connection.

<br/>
There's an easy way to check if your app meets the basic standards for a PWA, using Lighthouse:
* Open your app url in Chrome
* Open the dev tools pane ( press alt+command+i )
* Choose the 'Audits' tab to use Lighthouse to audit your app
* Leave all audits selected/checked
* Click the 'Run Audit' button at the bottom of the pane

When your audit is complete, you'll see that Lighthouse has returned audit results on Performance, Accessibility, Best Practices, SEO and that last one is PWA.  Each audit has a reference doc explaining the audit and how to fix issues.  Scroll down to review the audit results, or click on PWA to jump to those results.  You'll see what specific characteristics are missing (if any) from making your app a PWA.
<br/>
<br/>
<br/>
In order to address the attributes of **speed and reliability**, you'll need to run a service worker to precache some of your sites assets.  A service worker will essentially determine which assests to serve depending on whether you have network access.  It'll also update cached assets with network-provided ones when access is available again.  This provides users with a consistent, reliable and fast experience.
<br/>
<br/>
To make your app **installable**, you'll need to add a web app manifest.  This is a basic JSON file that lets you specify how your app will look to users.  There are many [available keys](https://developer.mozilla.org/en-US/docs/Web/Manifest#Members) in a web app manifest to control the appearance of your app.  The coolest part about installing your app is that it will be installed without an app store, and function just like an installed app.  This is why it might suit your project better than creating a native app.
<br/>
<br/>
To address the **responsiveness** of your app, refer to the audits and suggestions provided by Lighthouse.  You should already be familiar with building responsive apps, so there may be some improvements you can address.
<br/>
<br/>
Google Codelabs has some great, quick tutorials on PWA's, service workers and web app manifests.
<br/>
<br/>
Here are some resources to explore:
* [Your First Progressive Web App](https://codelabs.developers.google.com/codelabs/your-first-pwapp/index.html?index=..%2F..index#0) (Google Codelabs)
* [Service Workers](https://developers.google.com/web/fundamentals/primers/service-workers) (Google Developers)
* [Workbox](https://developers.google.com/web/tools/workbox/) - JavaScript Libraries for adding offline support to web apps
* [The Web App Manifest](https://developers.google.com/web/fundamentals/web-app-manifest) (Google Developers)
* [Web App Manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest#Members) (MDN)
* [Google Codelabs](https://codelabs.developers.google.com/)



