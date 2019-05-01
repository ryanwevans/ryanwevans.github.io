---
layout: post
title:      "Simple Hoisting and Scope in JavaScript"
date:       2019-04-28 21:48:33 -0400
permalink:  simple_hoisting_and_scope_in_javascript
---


These two concepts can be a bit intimidating at first, so let's keep it simple for now.

Hoisting and Scope are important because you want to be sure your declarations are available to your code when you call on them.  If you've called on them expecting them to be accessible and they aren't, your code won't behave as planned.  And if you don't know when they are and aren't available to your code, you'll be in for a wild goose chase trying to understand why your variables and functions aren't returning the values you expect them to.

When JavaScript interprets your code, it actually reads it twice.  The first time, it loads your script.  The second time, it executes it.  During that first pass is when your declarations are Hoisted to the beginning of their Scope.  

What this also means is that when JavaScript first reads your code, it only makes your *declarations* available for reference at the beginning of their scope, but not the *assignments* (i.e. values).  This is true even if they were written in the same line of code:


This is a declaration:

```var x;```


This is an assignment:

```var x = 5;```



So what does it mean when a variable is 'within scope'?  It simply means that it is available to your code at that point.

The scope of a variable or function is either **Global** or **Local**.

**Global** means it's available everywhere in your program.

**Local** means it is  available only inside the function it was declared in (it's scope is *Local* to that function).

There is an exception to making local declarations, though, so be careful.  If you only *assign* the variable inside a function, and do so without actually *declaring* it with a keyword (*var* x=5), it will by default become a Global variable.

So...both of the following are assigning a value to a variable, but:

This is a *Local* declaration:

```var x = 5;```

 
 
This is a *Global* declaration:

```x = 5;```


Notice that we've used the  `var`  keyword here, not  `let`  or  `const` .  ES2015 introduced these two new keywords, and a new scope with them called Block scope, which is not available to the  `var`  keyword.

Using `var`  allows the declaration to be reassigned anywhere, which can make controlling your variable values challenging.

Whenever possible, you want to declare your variables using  `let`  and  `const`  to have better control over their values throughout your code.  And,   `let`  and  `const`  are NOT hoisted, so they are not available to your code before they are declared.

You can read more about  **let**  [here](https://www.w3schools.com/js/js_let.asp) , and  **const**  [here](https://www.w3schools.com/js/js_const.asp)

And you can read more about **Hoisting** [here](https://www.w3schools.com/js/js_hoisting.asp)  , and **Scope** [here](https://www.w3schools.com/js/js_scope.asp)

&nbsp;


* * *

###### While you're at it, check out the reading [here](https://www.w3schools.com/js/js_strict.asp) on **Strict Mode** .  As W3 Schools states:

"*It helps you to write cleaner code, like preventing you from using undeclared variables.*"


* * *

