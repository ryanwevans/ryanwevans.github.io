---
layout: post
title:      "BEM Naming Convention"
date:       2019-10-26 22:22:15 -0400
permalink:  bem_naming_convention
---


BEM stands for Block, Element, Modifier.  The BEM methodology is to use a standard naming convention when naming classes in HTML and CSS.  It was created to make the relationship between your HTML and CSS intuitive and easy to understand.  By using this method, as a project gets larger, the ability to apply styles to a project stays manageable.
<br/>
<br/>
Imagine a developer that is new to a project codebase.  If the class names used utilize some form of standard and semantics, it is easy to read and understand which styles impact which elements.  It would be much easier to update, add or change styles without having to worry about possible random impacts in other areas of the project.  It would also be much easier to apply those same styles to other blocks or elements in the project.  Following the BEM naming convention is an easy way to do this, and most developers won't need any additional introduction to the project code before jumping in.
<br/>
<br/>
*Here's an explanation of each component:*
<br/>
<br/>
**Block**
<br/>
* Consider this the parent element, or a top level abstraction.


**Element**
<br/>
* This is a child item


**Modifier**
<br/>
* Modifiers and their values manipulate the style or theme of a block or element


<br/>
*Here's an example of the formatting convention:*
<br/>
* `.block-name__element-name_modifier-name_modifier-value`

<br/>
<br/>
*Here's the list of naming rules from the [BEM project website](https://en.bem.info/methodology/naming-convention/#naming-rules):*
* Names are written in lowercase Latin letters.

* Words are separated by a hyphen (-).

* The block name defines the namespace for its elements and modifiers.

* The element name is separated from the block name by a double underscore (__).

* The modifier name is separated from the block or element name by a single underscore (_).

* The modifier value is separated from the modifier name by a single underscore (_).

* For boolean modifiers, the value is not included in the name.

<br/>
<br/>
When I said that BEM is *a* way to do this, what I mean is that it's an existing standard that many front end developers use, but some choose to apply some of their own standards as well.  I would suggest sticking to the standard BEM conventions, unless you have reason to make changes.  If you do need to apply your own standards, try to keep future developers in mind and make your standards semantic and easy to read, so it's easy to determine the relationship between the HTML and CSS in your project.
<br/>
<br/>
<br/>
**Additional Resources:**
<br/>
* [BEM Project Website](https://en.bem.info/)
* [BEM 101](https://css-tricks.com/bem-101/)
* [Get BEM](http://getbem.com/naming/)
<br/>
<br/>



