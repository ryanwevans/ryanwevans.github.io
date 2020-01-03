---
layout: post
title:      "Update Your Copyright Year Automatically"
date:       2020-01-03 00:28:14 +0000
permalink:  update_your_copyright_year_automatically
---


Happy New Year!! 🎊
<br/>
<br/>
Did you remember to update your websites with the new copyright year?
<br/>
<br/>
Here's how to set it up with javascript to auto-update every year, so you don't have to worry about it...
<br/>
<br/>
All you need to do is make sure that your copyright statement is within `<p></p>` tags so this will be visible (not just within `<footer>` tags.
<br/>
Then, you can add the javascript code inline within `<script></script>` tags.
<br/>
<br/>
One important thing to note first... if you didn't already know, the `getYear()` method is deprecated, so you'll need to use the `getFullYear()` method.
<br/>
<br/>
<br/>
Here's an example of what the code looks like:
<br/>
<br/>
```
<footer>
   <p>website designed and built by Ryan Evans &copy;
      <script language="JavaScript" type="text/javascript">
         var today = new Date();
         var year = today.getFullYear();
         document.write(year);
      </script>
   </p>
</footer>
```
	
<br/>
<br/>
And there you have it!  Easy enough, right?  Now if you add this little snippet to your sites, you won't have to worry about updates every year!  That `<script>` will display the current year right next to the `&copy;` copyright symbol.
<br/>
<br/>
Here's wishing everyone a happy, healthy and prosperous new year!
<br/>
<br/>
<br/>
[Date.prototype.getFullYear() on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear)
<br/>
