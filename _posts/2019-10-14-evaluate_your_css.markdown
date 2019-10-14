---
layout: post
title:      "Evaluate Your CSS"
date:       2019-10-14 06:27:28 +0000
permalink:  evaluate_your_css
---


If there is anything that seems to be consistent when I talk to other developers, it's that they all shake their head when I bring up the frustrations of getting CSS styles to work exactly as desired.

<br/>
You probably already know about this trick, but there may be more to it than you realized.  When trying to perfect your CSS styles, try opening up the inspector.  In Chrome, you can do this with the shortcut  `option+command+i` .  Then, click on 'Elements' in the top section (if it isn't already selected).

<br/>
In the 'Elements' section, you can navigate to the html tag you are trying to apply a style to.  When you click on that tag within the 'Elements' section, the styles that are being applied to it appear in the next section below, called 'Styles'.
<br/>
(**Hint**: you can also use the shortcut  `shift+command+c`  to activate the selection tool and directly click/select the item on the page you want to 'inspect')

You'll notice that all the attributes and styles listed in the 'Styles' section are grouped by the html tag they are assigned to.  There are some sections listed here that are *not* the one you chose.  They are included here because their styles are being inherited by the tag you clicked on.

You'll also notice that some of the styles listed have strikethroughs.  This is because that particular style is not being applied, probably because there is a more specific style that is overriding it, or it just isn't valid based on other attributes.

When you hover your mouse over any of the styles, a checkbox will appear to the left of the style.  This is where you can play with turning specific styles on or off.  Just check or uncheck the box.  If the style is being applied, you should see a change in the webpage.
Here's something you may not have known, you can directly edit the style values in the inspector.  If you want to change a text color, just double-click on the color value and type in a new value.  When you press enter, you'll see the result of the change in the webpage.

This is the most direct way to 'play' with your CSS styles to determine what you like, don't like, and need or don't need.  You can also use this technique to dial in on what style is affecting your desired look.  By knowing this, you can easily override the style with one you want by defining a more specific selector.  Or, you can locate the file that holds the style that you want to change.

I've found this most useful when using Bootstrap, because the styles are preloaded.  It can be very difficult to track down where the style is located in order to change it.  You don't want to use  `!important`  to override styles unless you really know how that will impact everything else.

<br/>
So, go ahead and play around with altering the CSS in a web page to get more familiar with it.  All you have to do to reset the page (and start from scratch) is reload the page!

<br/>
<br/>
![](https://media.giphy.com/media/jIv6pfqKiIvHPYZO6y/giphy.gif)




